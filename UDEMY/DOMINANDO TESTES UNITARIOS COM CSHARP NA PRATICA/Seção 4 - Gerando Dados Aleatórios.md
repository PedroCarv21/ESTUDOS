# 7. Dados fakes com Auto Fixture

## O que é o Fixture?

É um recurso para testes, utilizado para gerar valores aleatórios no momento de instanciação de uma classe, tornando o processo de testes mais prático.
## Como baixar?

`Tools` → `NuGet Package Manager` → `Manage NuGet Packages for Solution...`

Informe o nome `AutoFixture` e instale-o.
## Como utilizar o Fixture?

Crie um objeto `Fixture` e chame o método `Build`, passando o nome da classe, que receberá dados aleatórios, no operador diamante. Por fim, chame o método `Create()`.

Caso queira predefinir condições na geração de valores para certas propriedades, utilize o método `With`. Exemplo:

```csharp
public class AutoFixtureTests
{
    private readonly Fixture _fixture;

    public AutoFixtureTests()
    {
        _fixture = new Fixture();
    }

    [Fact]
    public void Cliente_ComDadosGerados_DeveSerInativado()
    {
        var cliente = _fixture.Build<Cliente>()
            .With(c => c.Salario, new Random().Next(1500, 1800))
            .With(c => c.DataInativacao, (DateTime?) null)
            .Create();
    }
}
```

Os campos que forem do tipo `string` receberão um valor equivalente ao nome do próprio atributo concatenado com um `Guid`. Exemplo: `SobreNome385c793c-eafc-4201-a80a-6d30419f0cb9`

**OBS.: o método construtor é chamado automaticamente pelo xUnit antes da execução do método de teste.**

No caso da utilização de `With`, crie um método construtor para a classe informada no operador diamante e deixe os `get` e `set` das suas propriedades como `public`.

Caso queira criar muitos objetos de uma vez só, utilize o método `CreateMany`, passando a quantidade de objetos como argumento. Exemplo:

```csharp
var clientes = _fixture.Build<Cliente>()
    .With(c => c.Salario, new Random().Next(1500, 1800))
    .With(c => c.DataInativacao, (DateTime?)null)
    .CreateMany(10);
```

# 8. Dados fakes com Bogus

## Bogus

Biblioteca do C# utilizada para gerar dados falsos de modo mais prático do que manualmente. Ele é concorrente do Fixture.
## Como usar o Bogus

Primeiro, instale o pacote do Bogus seguindo os mesmos passos durante a instalação do Fixture.

Depois disso, é possível criar os dados tanto individualmente como também já inseri-los em um novo objeto.
### Criação dos dados individualmente

Para isso, é necessário criar uma instância de `Faker` passar como argumento o idioma que o Bogus irá se basear para gerar os dados aleatórios. A partir do objeto instanciado, chame os métodos que irão gerar dados de um determinado tipo (ex.: nome, sobrenome, email, etc). Exemplo:

```csharp
var nome = new Faker("pt_BR").Name.FirstName();
var nomeCompleto = new Faker("pt_BR").Name.FullName();
var email = new Faker("pt_BR").Internet.Email(nomeCompleto);
```

No caso do e-mail, é possível passar uma string como argumento de modo que e-mail gerado se baseará na string.
### Geração de dados para a instância de um objeto

Neste caso, será utilizado o método `CustomInstantiator`, responsável por informar ao Bogus sobre como deve ser criado o objeto com um método construtor personalizado. Exemplo:

```csharp
var cliente = new Faker<Cliente>("pt_BR")
    .CustomInstantiator(faker => new Cliente(
        faker.Name.FirstName(),
        faker.Name.LastName(),
        (double) faker.Finance.Amount(1500, 2000, 0),
        null
        ))
    .RuleFor(c => c.Email, (f, c) => f.Internet.Email(c.Nome, c.SobreNome))
    .Generate();
```

O `Finance.Amount()` recebe como argumento um intervalo (entre 1500 e 2000) e a quantidade de casas decimais (0 neste caso) que influenciará na criação de um valor monetário.

O `RuleFor` receberá dois tipos de argumento:
- O primeiro diz em qual campo o novo valor deve ser inserido.
- O segundo trata sobre como esse valor (neste caso o e-mail) deve ser criado.

