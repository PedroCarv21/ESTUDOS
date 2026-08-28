# 9. Realizando Mock de Objetos

## O que é o Mock?

Suponha que você criou uma classe service e seu método construtor precise receber como argumento um objeto que implemente uma interface repository.

No caso de testes, não faz sentido passar uma implementação **real**, pois o objetivo é apenas simular a interação com o banco que a implementação do repository faria. Quem realiza essa simulação é justamente o mock.

Exemplo:

```csharp
var cliente = ClienteFactory.GerarClienteValidoComBogus();

var clienteRepo = new Mock<IClienteRepository>();

var clienteService = new ClienteService(clienteRepo.Object);
clienteService.Cadastrar(cliente);

clienteRepo.Verify(r => r.Cadastrar(cliente), Times.Once);
```

Neste exemplo, é criado uma instância de `Mock` que recebe uma interface dentro operador diamante. Isso significa que o Mock que deverá criar um objeto que implemente a interface informada (neste caso o `IClienteRepository`).

No momento que for chamar o método construtor do service (`new ClienteService()`), esse método construtor receberá como argumento o objeto criado pelo mock. 

Para ter acesso ao objeto, chame a propriedade `Object`. Por fim, teste algum método do service (neste caso, `Cadastrar()`) e verifique se tudo ocorreu como devia com o método `Verify`, presente no objeto criado pelo mock. Este método receberá dois argumentos:
- Uma arrow function indicando o método do service que deseja verificar.
- O struct `Times` para saber quantas o método foi chamado (muitas, uma vez, nenhuma). Neste exemplo, `Times.Once` indica uma vez só.
# 10. Simulando retorno de métodos com Mock

## Método `Setup` do `Mock`

Usado para ensinar ao Mock o que ele deve fazer quando um determinado método do repository é chamado. Neste exemplo, foi configurado para que, ao chamar método `ObterTodos`, seja retornado uma lista de objetos do tipo `Cliente`:

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

    //clienteRepo.Verify(r => r.ObterTodos(), Times.Once);
    Assert.Equal(2, retornoLista.Count);
}
```