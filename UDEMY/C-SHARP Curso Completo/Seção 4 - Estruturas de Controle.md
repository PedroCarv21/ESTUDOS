# 38. Estrutura SWITCH

É uma forma mais prática de tratamento de valores do que a estrutura `if-else`. Exemplo:

```csharp
int x = 1;
switch (x)
{
    case 1:
	    Console.WriteLine("É 1.");
	    break;
    case 2:
        Console.WriteLine("É 2.");
        break;
    default:
        Console.WriteLine("Não é nenhum desses valores.");
        break;
}
```

Em C#, é obrigatório colocar o `break`. No entanto, é possível também executar o mesmo bloco de código para dois cases diferentes e, neste caso, não  é preciso o `break`. Exemplo:

```csharp
switch (x)
{
    case 1:
    case 2:
        Console.WriteLine("É 1 ou 2.");
        Console.WriteLine("Uma destas duas opções.");
        break;
    default:
        Console.WriteLine("Não é nenhum desses valores.");
        break;
}
```

# 39. Estrutura WHILE

## Criação de números aleatórios

Inicialize a classe `Random` e chame o método `Next`, que recebe dois parâmetros que indicarão um intervalo de números possíveis. Por exemplo: se eu desejo que o número sorteado esteja entre 1 e 15 então deverá ser escrito `Next(1, 16)`, sendo que o número 16 não será levado em consideração.

```csharp
Random rnd = new Random();
int numeroSorteado = rnd.Next(1, 16);
```

# 42. Estrutura FOREACH

Estrutura utilizada para percorrer elementos de uma lista ou os caracteres de uma string, sem precisar o intervalo manualmente.

```csharp
int[] inteiros = { 5, 10, 3, 2 };
foreach (int i in inteiros)
{
    Console.WriteLine(i);
}
```

# 47. Membros: Atributos e Métodos

## Método `string.Format()`

Utilizado para formatar uma `string`. Exemplo:

```csharp
static string darBoasVindas(string nome)
{
    return string.Format($"Bem vindo, {nome}.");
}
```

# 52. Atributos Estáticos

## Recurso Object Initializer

É uma forma mais concisa de criar um objeto e definir suas propriedades logo após a sua criação. Por exemplo, isso:

```csharp
Usuario usuario = new Usuario()
{
    Nome = "Pedro",
    Email = "pedro@gmail.com"
};
```

É o mesmo que isso:

```csharp
Usuario usuario = new Usuario();

usuario.Nome = "Pedro";
usuario.Email = "pedro@gmail.com";
```

## Métodos e Atributos de classe

Ambos só podem ser acessados por meio do nome da classe **e não pelo nome de um objeto.**

Por exemplo, se eu tenho um atributo em uma classe `Usuario` definido assim:

```csharp
public static string Senha = "senha_padrao";
```

Isto significa que este atributo só posso ser acesso desta maneira:

```csharp
Usuario.Senha
```

E não através de um objeto `Usuario`:

```csharp
Usuario usuario = new Usuario()
{
    Nome = "Pedro",
    Email = "pedro@gmail.com"
};
Console.WriteLine(usuario.Senha); // Essa linha irá gerar uma exceção
```
# 55. Parâmetros Variáveis

O comando `param` permite passar uma quantidade indefinida de argumentos para um método. Por exemplo:

```csharp
static void Main(string[] args)
{
    listar("Pedro", "Maria", "José", "Felipe");
}

public static void listar(params string[] nomes)
{
    foreach (string nome in nomes)
    {
        Console.WriteLine(nome);
    }
}
```

Neste caso, os nomes serão armazenados no array `nomes` e depois listados com `foreach`.

**OBS.: o método não irá gerar nenhum erro em caso de não ser passado um único argumento.**

Se você tirar o comando `params`, seria necessário passar um array diretamente como argumento:

```csharp
static void Main(string[] args)
{
    string[] nomes = { "Pedro", "Maria", "José", "Felipe" };
    listar(nomes);
}

public static void listar(string[] nomes)
{
    foreach (string nome in nomes)
    {
        Console.WriteLine(nome);
    }
}
```

