
# 14. Arquitetura de uma Solução C-Sharp

## Qual a arquitetura de um projeto .NET?

A estrutura de uma aplicação é organizada da seguinte forma:
- **Solução:** nada mais é do que o software como um todo. Dentro da solução, pode haver um ou mais projetos.
- **Projetos:** responsáveis por agrupar todos os arquivos compilados necessários para atender a uma determinada funcionalidade da aplicação. Os projetos podem gerar tanto um executável como também um **Dynamic Link Library (DLL)**, um arquivo compactado que contém código feito para ser reutilizado.

## O que é o namespace?

É um identificador utilizado para organizar as classes, interfaces e outros tipos, evitando conflito de nomes.
# 17. Primeiro Programa

## Métodos para imprimir

- **Console.Write("")** → imprime a mensagem entre parênteses, mas permanece com o cursor na mesma linha.
- **Console.WriteLine("")** →  imprime a mensagem entre parênteses e move o cursor para a próxima linha.

**OBS.: em vez de digitar o método, digite `cw` e pressione `Tab`.**

# 20. Comentários de Código

## Comentário de uma única linha

Utilize o `//` para escrever um comentário de uma única linha.
## Bloco de comentário

Digite `///` para que apareça um comentário desse tipo:

```xml
/// <summary>
/// 
/// </summary>
/// <param name="a"></param>
/// <param name="b"></param>
/// <returns></returns>
```

- `<summary>`: resume a funcionalidade do método.
- `<param>`: utilizado para descrever sobre o parâmetro (caso o método tenha um). O parâmetro `name` é usado referenciar o parâmetro tratado.
- `<returns>`: descreve aquilo que o método retorna.


# 21. Variáveis e Constantes

| Tipo      | Valor                  |
| --------- | ---------------------- |
| `sbyte`   | inteiro                |
| `byte`    | inteiro (não negativo) |
| `short`   | inteiro                |
| `ushort`  | inteiro (não negativo) |
| `int`     | inteiro                |
| `uint`    | inteiro (não negativo) |
| `long`    | inteiro                |
| `ulong`   | inteiro (não negativo) |
| `float`   | decimal                |
| `double`  | decimal                |
| `decimal` | decimal                |
**OBS.: caso escolha `decimal`, coloque um `m` após o número. Exemplo: `decimal num = 5.6m`**

**OBS.2: caso queira ver o valor mín. ou máx. que um tipo suporta, use o método `MinValue()` ou `MaxValue()`.**
# 22. Inferência de Tipos

## O que é inferência?

É uma forma do compilador descobrir, a partir do valor que foi atribuído a uma variável, qual é o seu tipo. Este processo é feito quando é utilizado a palavra-chave `var`. Isso impede atribuir a uma variável valores de tipos diferentes do tipo do valor inicial. Exemplo:

```csharp
var n = 10;
n = "hello" // isso irá gerar um erro de compilação.
```

**OBS.: é necessário atribuir um valor à variável já no momento da declaração.**

# 23. Interpolação de Strings

Esse é um processo mais simples de concatenar uma variável com uma string. Essas são as duas formas:

```csharp
string nome = "Pedro";
string sobrenome = "Carvalho";

Console.WriteLine("Meu nome completo é {0} {1}.", nome, sobrenome);
Console.WriteLine($"Meu nome completo é {nome} {sobrenome}.");
```

# 24. Notação Ponto

Significa usar um ponto para acessar as partes de um objeto. Por exemplo:

| Método                                | O que faz                                                                      |
| ------------------------------------- | ------------------------------------------------------------------------------ |
| `ToUpper`                             | Torna todas as letras de uma string em maiúsculas.                             |
| `Insert(posicao, string)`             | Insere uma string dentro de outra string de acordo<br>com o posição informada. |
| `Replace(palavraAntiga, novaPalavra)` | Substitui uma palavra de uma string por outra.                                 |

## Como informar a possibilidade do valor `null` em um string?

Utilize o `?` antes da notação ponto. Por exemplo, o método `Length` pode lançar uma exceção caso a string seja `null`. Para evitar isso, é necessário utilizar o `?`.


```csharp
string msg = null;
Console.WriteLine(msg?.Length);
```

# 25. Lendo Dados do Console

Utilize o comando `Console.ReadLine()` para receber os dados. Exemplo:

```csharp
Console.Write("Nome: ");
string nome = Console.ReadLine();
```

Por padrão, o valor armazenado em `ReadLine()` sempre será uma string. Se deseja converter a string para outro tipo primitivo, utilize o comando `Parse()`; esse método está presente na maioria dos tipos primitivos (com exceção de `char`). Exemplo da conversão para `double`:

```csharp
Console.Write("Salário: ");
double salario = double.Parse(Console.ReadLine());
```

No caso de `double`, se for passado um valor decimal com ponto (ex.: 345.23), não será reconhecido esse ponto, pois, por padrão, é configurado o sistema para que ele reconheça o separador decimal de acordo com o seu país. Para mudar isso e poder utilizar o ponto em números decimais, chame o `System.Globalization` e importe o método `CultureInfo.InvariantCulture`.

```csharp
Console.Write("Salário: ");
double salario = double.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
```

# 26. Formatando Números

## Como definir a quantidade de casas decimais?

Utilize o método `ToString()`, passando o argumento `F` mais um número que irá representar a quantidade de casas decimais. Por exemplo: a quantidade de casas decimais serão duas neste código:

```csharp
double num = 5.678;
Console.WriteLine(num.ToString("F2"));
```

# 27. Conversões

## Nota sobre conversão explícita de tipos

Sempre que houver a possibilidade de perda de dados durante a conversão, será necessário fazer um casting.
## Formas de conversão do tipo `string` para `int`

### Método `ToInt32`

```csharp
string valor = "10";
int num = Convert.ToInt32(valor);
Console.WriteLine(num);
```

### Método `TryParse()`

```csharp
string valor = "10";
int num;
int.TryParse(valor, out num);
Console.WriteLine(num);
```

Caso tente fazer um conversão inválida, como tentar converter letras em números, o resultado será 0.
# 28. Operadores Aritméticos

## Método `Math.Pow()`

Utilizado para calcular a potenciação. Um primeiro argumento é o valor base e o segundo é o expoente.
# 31. Operadores Lógicos #02
## O que é o operador exclusivo `^`?

Também chamado de OU exclusivo, é um operador binário que retorna `true` apenas se um dos lados for verdadeiro e o outro for falso.
# 33. Operadores Unários

## Incremento e decremento pré e pós fixado

- **Prefixado (`++x`):** Incrementa primeiro, depois retorna o novo valor.
- **Pós-fixado (`x++`):** Retorna o valor atual primeiro, depois incrementa a variável. 

Por exemplo:

```csharp
int num1 = 1;
int num2 = 2;

Console.WriteLine(num1++ == --num2);
```

Assim será o processo: será feito a subtração `num2` - 1 e, em seguida, serão comparados os valores da variável `num1` (que é 1) e `num2` (que agora também é 1). O resultado será `true`. Por fim, será incrementado o valor 1 na variável `num1`.
