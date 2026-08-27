# 103. LINQ #01

## O que é LINQ (Language Integrated Query)?

É um recurso utilizado para consultas avançadas de dados que podem vir de várias fontes distintas (como listas ou banco de dados), apresentando-se como uma alternativa aos loops de repetição tradicionais.
## Principais métodos

Todos eles recebem arrow functions (com exceção do `ToList`) para realizar as operações.

- **`Where()`:** filtra os dados.
- **`OrderBy()`:** ordena os dados. Caso queira em ordem decrescente, utilize o - após o `=>`.
- **`Select()`:** extrai dados dos objetos da coleção para armazená-los em outra coleção.
- **`ToList()`:** retorna os dados dentro de uma lista.

### Exemplo

Filtrando os alunos com nota maior que 5, colocando em ordem decrescente, extraindo o nome dos alunos e, por fim, retornando uma lista:

```csharp
List<Aluno> alunos = new List<Aluno>()
{
    new Aluno("Pedro", 15, 7.0),
    new Aluno("Julia", 25, 9.0),
    new Aluno("Ana", 17, 5.0),
    new Aluno("Marcus", 20, 8.0),
};

List<string> alunosAprovados = alunos
    .Where(a => a.Nota > 5.0)
    .OrderBy(a => -a.Nota)
    .Select(a => a.Nome).ToList();
```

É possível fazer o mesmo processo da seguinte forma:

```csharp
var alunosAprovados2 = from aluno in alunos
where aluno.Nota > 5.0
orderby -aluno.Nota
select aluno.Nome;
```

# 104. LINQ #02

Outros métodos LINQ:

- **`Single()`:** retorna o elemento procurado que deve ser único dentro da estrutura. Caso o elemento se repita, haverá uma exceção (assim como em `SingleOrDefault()`).
- **`SingleOrDefault()`:** retorna o elemento procurado que seja único dentro da estrutura. Caso o elemento não seja encontrado, será retornado `null`.
- **`First()`:** retorna o primeiro elemento encontrado que corresponder aos critérios do argumento.
- **`FirstOrDefault()`:** retorna o primeiro elemento encontrado que corresponder aos critérios do argumento. Caso não seja encontrado, retornará `null`.
- **`Last()`:** retorna o último elemento encontrado que corresponder aos critérios do argumento.
- **`LastOrDefault()`:** retorna o último elemento encontrado que corresponder aos critérios do argumento. Caso não seja encontrado, retornará `null`.
- **`Min()`:** retorna o menor valor.
- **`Max()`:** retorna o maior valor.
- **`Sum()`:** retorna o total da soma de todos os valores.
- **`Avarege()`:** retorna a média de todos os valores.

# 105. Nullables

Há duas formas de permitir que tipos primitivos aceitem valor nulo: `Nullable` e `?`. Exemplo:

```csharp
Nullable<int> num = null;
int? num2 = null;
```

Para verificar se a variável realmente tem valor ou não, utilize o método `HasValue`:

```csharp
if (num.HasValue)
{
    Console.WriteLine($"Valor: {num}");
}
else
{
    Console.WriteLine("Valor nulo.");
}
```

## Definindo valor padrão

Caso queira atribuir o valor de uma variável para outra variável, mas não sabe se o valor será nulo, coloque `??` no fim da a inicialização e, depois disso, defina o valor padrão. Por exemplo, se `num` for nulo, então `num3` receberá o valor 10:

```csharp
int num3 = num ?? 10;
Console.WriteLine(num3);
```

É possível também usar o método `GetValueOrDefault()`, porém o valor padrão não será definido por você. Por exemplo, o valor padrão é 0 para tipos inteiros, `false` para booleano, etc. Exemplo:

```csharp
int num4 = num.GetValueOrDefault();
Console.WriteLine(num4);
```

**OBS.: no caso de atributos, esses recebem valores padrão caso não sejam inicializados.**
# 106. Dynamic

Permite criar variáveis com tipagem dinâmica. Exemplo:

```csharp
dynamic num = 10;
num = 6.5;
Console.WriteLine(num);
```

## Qual a diferença entre `dynamic` e `var`?

O `var` define o tipo da variável em **tempo de compilação** enquanto o `dynamic` deixa para descobrir o tipo apenas em **tempo de execução**.
## Classe `System.Dynamic.ExpandoObject()`

É uma classe do C# que permite criar objetos cujos membros (como propriedades e métodos) podem ser adicionados, alterados ou removidos dinamicamente na hora. Exemplo:

```csharp
dynamic usuario = new System.Dynamic.ExpandoObject();
usuario.nome = "Pedro";
usuario.email = "pedro@gmail.com";
usuario.senha = "pedro123";

Console.WriteLine($"{usuario.nome}");
```

# 107. Generics

Utilização de Generics em uma classe:

```csharp
public class Classe<T>{
}
```

E caso queira criar uma subclasse para ela:

```csharp
public class Subclasse : Classe{
	public Subclasse : base(){
	}
}
```