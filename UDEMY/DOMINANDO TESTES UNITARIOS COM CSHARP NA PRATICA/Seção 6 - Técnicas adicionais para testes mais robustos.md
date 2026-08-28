# 11. Escapando de Testes ( Ignorando ou desabilitando )

Use o parâmetro `Skip` presente no atributo `[Fact]` para que o método não seja testado. O resultado será um ícone de alerta no Test Explorer e, na parte inferior, uma mensagem que explica o porque aquele método não foi testado (essa mensagem é passada como valor para o `Skip`. Exemplo:

![[Pasted image 20260828173117.png]]

# 13. Trabalhando com Fluent Assertions

## O que é Fluent Assertions

Um recurso que oferece métodos para verificação de testes com o objetivo de tornar o código mais legível. Para isso é necessário baixar esse recurso lá no NuGet Package Manager.

**OBS.: caso esse recurso seja utilizado para projetos comerciais, haverá uma cobrança.**

## Exemplo 1

Verifica se o nome obtido está de acordo com o nome esperado.

```csharp
[Fact(DisplayName = "Nome retornar nome completo")]
[Trait("Categoria", "Asserts")]
public void String_NomeCliente_DeveRetornarNomeCompleto()
{
    Cliente cliente = new Cliente("Pedro", "Carvalho", 3000);

    var nomeCompletoObtido = cliente.ObterNomeCompleto();

    //Assert.Equal(expected: "Pedro Carvalho", actual: nomeCompletoObtido);
    nomeCompletoObtido.Should().Be("Pedro Carvalho");
}
```
## Exemplo 2

Verifica se a string veio nula ou vazia.

```csharp
[Fact(DisplayName = "Nome deve ser nulo ou vazio")]
[Trait("Categoria", "Asserts")]
public void Cliente_Nome_DeveSerNuloOuVazio()
{
    Cliente cliente = new Cliente("", "Carvalho", 3000);

    //Assert.True(String.IsNullOrEmpty(cliente.Nome));

    String.IsNullOrEmpty(cliente.Nome).Should().BeTrue();
}
```

## Exemplo 3

Verifica se a quantidade de elementos na lista está correta, se os itens são únicos e se nenhum de qualquer elemento veio como nulo ou vazio.

```csharp
[Trait("Categoria", "Ordenacao")]
[Fact(DisplayName = "lista todos os clientes")]
public void Cliente_ObterTodos_DeveRetornarTodosClientes()
{
    var clientesFake = ClienteFactory.GerarListaClienteComAutoFixture(2);

    var clienteRepo = new Mock<IClienteRepository>();

    clienteRepo.Setup(r => r.ObterTodos()).Returns(clientesFake);

    var _clienteService = new ClienteService(clienteRepo.Object);
    var retornoLista = _clienteService.ObterTodos();

    //Assert.Equal(2, retornoLista.Count);
    retornoLista.Should().HaveCount(2)
        .And.OnlyHaveUniqueItems()
        .And.NotContain(c => String.IsNullOrEmpty(c.Nome));
}
```