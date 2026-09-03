
# 50. Métodos Com Retorno #02

## Encadeamento de métodos

Esse encadeamento se torna possível a partir do momento que o método retorna o objeto da própria classe. Por exemplo, através de métodos com `return this` como estes:

```csharp
public Usuario depositar(double quantia)
{
    Saldo += quantia;
    return this;
}
public Usuario sacar(double quantia)
{
    Saldo -= quantia;
    return this;
}
```

É possível chamar um métodos após outro método:

```csharp
Usuario usuario = new Usuario("Pedro", "pedro@gmail.com", "p123");
usuario.depositar(500.0).sacar(200.0);
Console.WriteLine(usuario.Saldo);
```

# 56. Parâmetros Nomeados

Informa o nome de cada parâmetro na chamada do método e também o seu vínculo com cada valor que está sendo passado como argumento. Exemplo:

```csharp
public static void formatarData(int dia, int mes, int ano)
{
    Console.WriteLine("{0:D2}/{1:D2}/{2}", dia, mes, ano);
}
```

## Formatação composta

Esta formatação será utilizada para completar uma quantidade de casas numéricas com zero caso o valor passado seja pequeno demais. Por exemplo, `1:D2`, tem o número `1` para indicar a posição do valor em `Console.WriteLine()` e `D2` para indicar o tamanho que esse valor deve ter. Se o número for 3, então ficará como 03; se o número for 45 então ficará como 45 mesmo.

# 58. Propriedades

## Qual a diferença entre propriedade e atributo?

- **Atributo:** acessa e atualiza o valor diretamente.
- **Propriedade:** acessa e atualiza o valor (geralmente) através dos métodos `get` e `set`.

## Formas de criar métodos `get` e `set`.

Opção 1:

```csharp
string _nome;
public string Nome
{
    get
    {
        return string.Format($"Nome do usuário: {_nome}");
    }
    set
    {
        if (string.IsNullOrEmpty(value))
        {
            Console.WriteLine("Informe um nome.");
        }
        else
        {
            _nome = value;
        }   
    }
}
```

Sempre quando for feito um `usuario.Nome` ou `usuario.Nome = "Pedro"` será chamado o método `get` e `set`.

**OBS.: se não colocar nada antes do tipo da propriedade/atributo, será considerado como `private`.**

**OBS.2: perceba que foi criado um atributo e uma propriedade com nomes semelhantes. Isso acontece porque, caso eu colocasse, em vez do atributo `nome`, a propriedade `Nome` dentro de um dos métodos `get` e `set` da própria propriedade, ocorreria uma chamada recursiva.**

Opção 2:

```csharp
private string email {get;set;}
```

Opção 3:

```csharp
public string senha
{
    get => senha; // A seta '=>' implica retornar o que vem depois dela.
    set
    {
        senha = value;
    }
}
```

# 59. Atributos Readonly

## A diferença entre `const` e `readonly`

Se for uma constante, é necessário inicializar o atributo já na declaração. Se o atributo for `readonly`, o atributo pode se inicializar já na declaração ou por meio do método construtor. Exemplo de constante:

```csharp
public const double Pi = 3.14;
```

Exemplo de atributo `readonly`:

```csharp
readonly string Cpf = "";

public Usuario(string nome, string email, string senha, string cpf) { 
    this.Nome = nome;
    this.Email = email;
    this.Senha = senha;
    this.Cpf = cpf;
}
```

# 60. Enumerações (Enum)

Os enums devem ser criado assim:

```csharp
public enum Genero
{
    Acao,
    Terror,
    Comedia,
    Romance,
    Aventura
}
```

E pode ser usado da seguinte forma:

```csharp
public string Titulo { get; set; }
public Genero Genero { get; set; }
public TimeSpan Duracao { get; set; }

public Filme(string titulo, Genero genero, TimeSpan duracao)
{
    Titulo = titulo;
    Genero = genero;
    Duracao = duracao;
}
```


Caso um atributo utilize enum como um tipo, o valor pode ser passado da seguinte forma:

```csharp
Filme filme = new Filme("Os Dez Mandamentos", Genero.Aventura, new TimeSpan(4, 0, 0));
Console.WriteLine(filme.Genero);
```

> [!NOTE] Sobre a struct `TimeSpan`
> É utilizado para representar o período de tempo em relação a alguma coisa. Recebe três valores inteiros, cada um representando a hora, o minuto e o segundo.

É possível também descobrir a posição de um valor que está dentro do enum através de um casting. Exemplo:

```csharp
int posicaoEnum = (int) filme.Genero;
```

# 62. Class vs Struct

## Criação de uma struct

A criação de uma struct se dá de forma semelhante a criação de uma classe, trocando apenas a palavra `class` por `struct`:

```csharp
public struct UsuarioStruct
{
    public string Nome;
    public string Email;
    public string Senha;

    public UsuarioStruct(string nome, string email, string senha)
    {
        Nome = nome;
        Email = email;
        Senha = senha;
    }
}
```

É também semelhante a inicialização de uma struct:

```csharp
UsuarioStruct usuario1 = new UsuarioStruct();
usuario1.Nome = "Pedro";
usuario1.Email = "pedro@gmail.com";
usuario1.Senha = "pedro123";
```

A diferença entre struct e classe é que a primeira faz atribuição por valor enquanto que a segunda faz atribuição por referência. 

**Atribuição por valor** significa que, ao fazer com que o uma struct receba uma outra struct como valor, isso irá gerar uma copia e cada uma das structs terá seu valor independente da outra. Exemplo:

```csharp
UsuarioStruct usuario2 = usuario1;
usuario1.Nome = "José";
Console.WriteLine(usuario2.Nome);
```

A atualização do nome do `usuario1` não irá afetar o `usuario2`.

**Atribuição por referência**, por outro lado, poderá ter o mesmo objeto referenciado por duas ou mais variáveis, ou seja, se uma variável mudar um dos valores, a outra variável também será afetada. No exemplo passado, se ambas as variáveis fossem criadas a partir da instanciação de uma classe, a alteração do valor do nome na variável `usuario1` também afetaria a variável `usuario2`.

# 64. Parâmetros por Referência (Ref/Out)

## Comando `ref`

Utilizada para modificar uma variável que é passada como argumento em um método. Par isso, coloque o comando `ref` tanto no parâmetro como também no argumento. Exemplo:

```csharp
static void Main(string[] args)
{
    int num = 3;
    Console.WriteLine(num);
    ElevarAoQuadrado(ref num);
    Console.WriteLine(num);

}

public static void ElevarAoQuadrado(ref int num)
{
    num *= num;
}
```

## Comando `out`

Não 'calcula' o valor de uma variável passada como argumento, apenas cria um valor e armazena esse valor no argumento, sendo necessário colocar `out` tanto no parâmetro como no argumento. Exemplo:

```csharp
static void Main(string[] args)
{
    CalcularPotenciacao(2, 3, out double result);
    Console.WriteLine(result);
}

public static void CalcularPotenciacao(int valorBase, int expoente, out double resultado)
{
    resultado = Math.Pow(valorBase, expoente);
}
```

**OBS.: com `out`, é possível declarar uma variável e, ao mesmo, passá-la como argumento. No entanto, com `ref` só é possível passar como argumento as variáveis que já foram inicializadas.**

É possível também retornar dois valores utilizando `out`. Exemplo:

```csharp
static void Main(string[] args)
{
    Calcular(3, out double eq, out double ec);
    Console.WriteLine(eq);
    Console.WriteLine(ec);

}

public static void Calcular(double valor, out double elevadoAoQuadrado, out double elevadoAoCubo)
{
    elevadoAoQuadrado = Math.Pow(valor, 2);
    elevadoAoCubo = Math.Pow(valor, 3);
}
```

# 66. Parâmetro com Valor Padrão

Permite especificar valores padrão para os parâmetros caso nenhum valor seja passado como argumento. Exemplo:

```csharp
static void Main(string[] args)
{
    Dividir(); // Resultado: 1.
    Dividir(6 / 3); // Resultado: 2.
    Dividir(6); // Resultado: dividendo será igual a 6 e o resultado será 6.
    Dividir(divisor: 2); // Resultado: 0,5.

}

public static void Dividir(double dividendo = 1, double divisor = 1)
{
    Console.WriteLine(dividendo / divisor);
}
```