
# 5. Utilizando Traits para Categorizar Testes

## Atributo `[Trait]`

Permite renomear e organizar os métodos de testes no Test Explorer. Exemplo:

```csharp
[Fact(DisplayName = "Cliente deve estar inativo")]
[Trait("Categoria", "Cliente testes")]
public void Cliente_ComDataInativacao_DeveEstarInativo()
{
    var cliente = new Cliente("Carlos", "Maia", 3000, new DateTime(2024, 12, 31));

    var ativo = cliente.Ativo;

    Assert.False(ativo);
}

[Fact(DisplayName = "Cliente deve estar ativo")]
[Trait("Categoria", "Cliente testes")]
public void Cliente_SemDataInativacao_DeveEstarAtivo()
{
    var cliente = new Cliente("Carlos", "Maia", 3000);

    var ativo = cliente.Ativo;

    Assert.True(ativo);
}
```

Vá até o Test Explorer e clique em `Group By` → `Traits`. O resultado é este no Test Explorer:

![[Pasted image 20260826164534.png]]

Caso não apareça, vá em `Build` → `Clean Solution` → volte para `Build` → `Rebuild Solution`.
# 6. Ordenação dos Testes

É possível determinar a ordem em que os métodos de testes serão executados.

## Criação da classe `PriorityOrderer`

Crie uma classe com o nome `PriorityOrderer`. Este deve ser o seu conteúdo:

```csharp
using Xunit.Abstractions;
using Xunit.Sdk;

namespace DemoCalculadoraTests
{
    [AttributeUsage(AttributeTargets.Method)]
    public class TestPriorityAttribute : Attribute
    {
        public TestPriorityAttribute(int priority)
        {
            Priority = priority;
        }

        public int Priority { get; }
    }

    public class PriorityOrderer : ITestCaseOrderer
    {
        public IEnumerable<TTestCase> OrderTestCases<TTestCase>(IEnumerable<TTestCase> testCases) where TTestCase : ITestCase
        {
            var sortedMethods = new SortedDictionary<int, List<TTestCase>>();

            foreach (var testCase in testCases)
            {
                var priority = 0;

                foreach (var attr in testCase.TestMethod.Method.GetCustomAttributes(typeof(TestPriorityAttribute).AssemblyQualifiedName))
                    priority = attr.GetNamedArgument<int>("Priority");

                GetOrCreate(sortedMethods, priority).Add(testCase);
            }

            foreach (var list in sortedMethods.Keys.Select(priority => sortedMethods[priority]))
            {
                list.Sort((x, y) => StringComparer.OrdinalIgnoreCase.Compare(x.TestMethod.Method.Name, y.TestMethod.Method.Name));
                foreach (var testCase in list)
                    yield return testCase;
            }
        }

        private static TValue GetOrCreate<TKey, TValue>(IDictionary<TKey, TValue> dictionary, TKey key) where TValue : new()
        {
            if (dictionary.TryGetValue(key, out var result)) return result;

            result = new TValue();
            dictionary[key] = result;

            return result;
        }
    }
}
```

## Atributo `[TestCaseOrderer]`

É um atributo de classe utilizado para informar onde está o `PriorityOrderer` e qual será a classe que terá seus métodos de testes ordenados. Exemplo:

```csharp
[TestCaseOrderer("DemoCalculadoraTests.PriorityOrderer", "DemoCalculadoraTests")]
public class OrdenacaoTests
{
}
```

## Parâmetro `TestPriority` do atributo `[Fact]`

É a partir deste parâmetro que será informado um número que representará a ordem de execução do teste. Exemplo de um teste que será executado em segundo lugar:

```csharp
[Trait("Categoria", "Ordenacao")]
[Fact(DisplayName ="Cliente retornar cliente"), TestPriority(2)]
public void ObterPorId_Cliente_DeveRetornarCliente()
{
}
```