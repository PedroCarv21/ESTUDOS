# 87. Exemplo Lambda

## Diferença entre `Action` e `Func`

Ambos são tipos utilizados para armazenar funções anônimas , ou seja, funções que não tem um nome próprio. A diferença é que `Action` não retorna nada enquanto que `Func` irá retornar algum valor.

É possível escrever uma `Action` ou `Func` tanto em um única linha (caso o corpo tenha também uma única linha) como também colocando o copo da função entre chaves. 

Exemplo de `Action` de uma única linha:

```csharp
Action imprimirMsg = () => Console.WriteLine("Olá Mundo");
imprimirMsg();
```

```csharp
Action<string> imprimirMsg = (nome) => Console.WriteLine($"Olá {nome}");
imprimirMsg("Pedro");
```

**OBS.: o tipo do parâmetro deve ser informado no Generics enquanto que o nome do parâmetro fica entre parênteses. Se for um único parâmetro, então não precisa de parênteses.**

Exemplo de `Action` com mais de uma linha:

```csharp
Action<int> eParOuImpar = (num) =>
{
    if (num % 2 == 0)
    {
        Console.WriteLine($"{num} é par.");
    }
    else
    {
        Console.WriteLine($"{num} impar.");
    }
};
eParOuImpar(3);
```

O `Func` funciona da mesma forma, porém é necessário informar qual será o retorno dessa função, representada pelo último tipo dentro do Generics. Exemplo:

```csharp
Func<int, string> eParOuImpar = (num) =>
{
    if (num % 2 == 0)
    {
        return $"{num} é par.";
    }
    else
    {
        return $"{num} impar.";
    }
};
Console.WriteLine(eParOuImpar(3));
```

# 88. Delegate com Lambda

Comando `delegate` é usado para criar um tipo que determinará as regras para uma função como, por exemplo, os tipos de parâmetros e também o retorno para aquela função anônima (como foi o caso de `Action` e `Func`). Exemplo:

```csharp
public delegate string ParOuImpar(int num);

static void Main(string[] args)
{
    ParOuImpar parOuImpar = (n) =>
    {
        if (n % 2 == 0)
        {
            return "É par";
        }
        else
        {
            return "É ímpar";
        }
    };
    Console.WriteLine(parOuImpar(4));
}
```

# 89. Usando Delegates

Em vez de passar funções anônimas como valores para os delegates, é possível também passar métodos. Exemplo:

```csharp
static void Main(string[] args)
{
    Operacao op = Somar;
    Console.WriteLine(op(2, 3));

    Func<int, int, int> op2 = Somar;
    Console.WriteLine(op2(2, 5));
}

public static int Somar(int x, int  y)
{
    return x + y;
}
```

# 90. Delegate com Funções Anônimas

É possível também passar um delegate para outro delegate. Exemplo:

```csharp
Operacao op3 = delegate (int n, int n2)
{
    return n + n2;
};

Console.WriteLine(op3(3, 6));
```

## Como converter uma string em array?

Método `ToCharArray()`. Exemplo:

```csharp
char[] letras = "pedro".ToCharArray();
```

## Como inverter a ordem dos elementos em um array?

Método `Array.Reverse()`. Exemplo:

```csharp
char[] letras = "pedro".ToCharArray();
Array.Reverse(letras);
```

## Como converter um array para string?

Comando `new string`. Exemplo:

```csharp
char[] letras = "pedro".ToCharArray();
Array.Reverse(letras);
Console.WriteLine(new string(letras));
```

# 92. Métodos de Extensão

Métodos de extensão são métodos criados para tipos já existentes (ex.: int, double, etc). Para isso, crie uma classe estática com um método estático, sendo o primeiro parâmetro marcado com o `this` para representar o objeto do tipo com o qual você quer trabalhar. Por exemplo:

```csharp
internal static class AuxilioInteiros
{
    public static int Somar(this int objeto, int argumento)
    {
        return objeto + argumento;
    }
}
```

```csharp
int x = 2;
Console.WriteLine(x.Somar(7)); // 9
x.Somar(5);
Console.WriteLine(x); // 2
```