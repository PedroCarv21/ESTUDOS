# 10. S04E02 - Explicação Estrutura do Projeto

## Projeto ASP.NET

Neste projeto se encontram os seguintes arquivos/pacotes:

- **Dependencies:** é onde ficam as bibliotecas disponibilizadas por terceiros e que foram baixadas. Dentro de Dependencies são encontrados, entre os principais, os pacotes baixados no NuGet e os projetos referenciados.
- **Properties:** contém o arquivo launchSettings.json, responsável por instruir o Microsoft Visual Studio na hora de executar a aplicação.
- **Pasta Controllers**
- **Arquivo Program.cs:** ele é responsável por configurar a aplicação e definir como ela recebe e processa requisições HTTP.

```csharp
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.

builder.Services.AddControllers();
// Learn more about configuring Swagger/OpenAPI at https://aka.ms/aspnetcore/swashbuckle
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

// Configure the HTTP request pipeline.
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();

app.UseAuthorization();

app.MapControllers();

app.Run();
```

**OBS.: está sendo utilizada a versão 8.0 do .NET.**

Estas são explicações para alguns comandos presentes no `Program.cs`:

- `builder`: é a partir dessa variável que terá o acesso a diversos membros para configuração da aplicação. Por exemplo, é a partir do `builder.Services` que serão registrados os diversos serviços para que depois seja realizado a injeção de dependências. Os serviços aqui nada mais são do que componentes que a aplicação precisa e que, portanto, devem ser registrados no container de injeção de dependências.
- `AddControllers`, `AddEndpointsApiExplorer()` e `AddSwaggerGen()`: o primeiro método é para registrar os controllers, o segundo para fornecer informações sobre os endpoints para ferramentas como o Swagger e o último para a geração de documentação Swagger.
- `app`: representa a própria aplicação.
- `app.Environment.IsDevelopment()`: irá verificar se a aplicação está um ambiente de desenvolvimento. Um ambiente de desenvolvimento significa o ambiente usado enquanto você está programando. Caso o resultado seja `true`, então serão disponibilizados os dados da documentação (informações sobre endpoints, métodos HTTP, etc) e a interface para visualizar e testar a documentação; isso é feito através dos métodos `app.UseSwagger()` e `app.UseSwaggerUI()`.
- `UseHttpsRedirection`: redireciona a chamada HTTP para HTTPS.
- `UseAuthorization`: habilita a verificação de autorização.
- `MapControllers()`: faz os endpoints dos Controllers funcionarem e receberem requisições.
- `Run()`: inicia a aplicação.

**OBS.: todas essas informações foram retiradas não dessa aula, mas de outras fontes.**

# 11. S04E03 - Modelo Usuario

`DateTimeOffset` é um struct que não só armazena informações da data e hora (como o `DateTime`), mas também informações do fuzo horário.
# 13. S04E05 - Modelo EnderecoEntrega

## Diferença entre `ICollection` e `List`

A diferença é que `ICollection` é uma interface que representa uma estrutura de dados, podendo ser implementada com classes como, por exemplo, a própria `List`.

# 17. S04E09 - UsuarioRepository

## Método `Find()`

Este é um método de instância para objetos `List` que busca o primeiro elemento que atenda as condições passadas como argumento. Exemplo: encontrar um objeto cujo seja igual ao id passado como argumento.

```csharp
public static List<Usuario> _db = new List<Usuario>();

public Usuario Get(int id)
{
    return _db.Find(u => u.Id == id)!;
}
```

### Ponto de interrogação no final do método

Esse ponto de interrogação garante que o valor retornado não será nulo, ou seja, que será encontrado um elemento que atenda as devidas condições.
# 18. S04E10 - TEORIA - Injeção de Dependência

## Ferramenta `Microsoft.Extensions.DependencyInjection`

É um container de injeção de dependências (DI) padrão do ASP.NET.

Essas são as formas de instanciar os objetos:
- **Singleton:** cria um único objeto de um tipo específico e irá utilizar sempre essa mesma instância para injetar em qualquer classe que precise dela.
- **Scoped:** cria uma nova instância cada vez que uma solicitação (que significa escopo) é feita.
- **Transient:** cria uma instância toda vez que um serviço é solicitado. Se por exemplo, eu tiver dois atributos do mesmo tipo, serão criadas instâncias diferentes para cada um deles.
# 19. S04E11 - Configurar o DI

Para determinar qual classe será instanciada e injetada pelo container, vá até o `Program.cs` e utilize a propriedade `Services` do objeto `builder`. A partir daqui, é possível escolher qual será a forma de instanciação: `AddSingleton<>()`, `AddScoped<>()` ou `AddTransient<>()`. 

É necessário passar para o generics de um desses métodos qual será a classe instanciada ou qual classe será instanciada para uma determinada interface. Exemplo:

```csharp
builder.Services.AddScoped<IUsuarioRepository, UsuarioRepository>();
```

# 21. S04E13 - UsuariosController

## Criação de um controlador

É necessário colocar o atributo `[ApiController]` para que ele seja identificado como um controlador e o atributo `[Route("api/[controller]")]` de modo que o controlador possa ser referenciado por meio de uma rota específica. Esse `[controller]` será substituído pelo nome do controlador sem o `Controller` no final. Por exemplo, a classe:

```csharp
[ApiController]
[Route("api/[controller]")]
public class UsuariosController : ControllerBase
{
}
```

será acessada por meio da rota `api/Usuarios`, sendo `Usuarios` retirado de `UsuariosController`, removendo a palavra `Controller`.

Para criar uma classe, clique com o botão direito no projeto → Add → Class... → ASP.NET Core → API Controller - Empty → escolha um nome → Add. A classe será criada exatamente como é mostrado o código anterior.
### Classe `ControllerBase`

É uma classe padrão que oferece alguns recursos para determinar as respostas HTTP que os métodos irão retornar. Exemplo: `Ok`, `NotFound`, etc.

## Métodos HTTP

Estes são algum dos métodos HTTP que podem ser utilizados:

- `[HttpGet]`: usado para consultar dados. Caso queira consultar com base no id, use o `[HttpGet("{id}")]`, sendo considerado uma boa prática que o nome do parâmetro da url seja igual ao nome do parâmetro do método. Exemplo:
```csharp
[HttpGet("{id}")]
public IActionResult Get(int id)
{
}
```

- `[HttpPost]`: indica que um método irá enviar dados. Geralmente, é coletado os dados através do corpo da solicitação; para isso, use o `[FromBody]` antes do parâmetro. Exemplo:

```csharp
[HttpPost]
public IActionResult Add([FromBody] Usuario usuario)
{

}
```

- `[HttpPut]`: implica que um método atualizará informações. 
- `[HttpDelete]`: usado para deletar informações.
## Interface `IActionResult`

Utilizada para determinar qual será o código de status dos métodos dos controllers. Exemplo:

```csharp
[HttpGet("{id}")]
public IActionResult Get(int id)
{
    var usuario = _repository.Get(id);
    if (usuario == null)
    {
        return NotFound("Não encontrado!");
    }
    return Ok(usuario);
}
```

É através do `IActionResult` que eu consigo retornar métodos como `NotFound` ou `Ok`