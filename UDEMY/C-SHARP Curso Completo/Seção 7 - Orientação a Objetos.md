
# 76. Os Pilares da OO: Herança

## Qual a diferença entre composição e herança?

A composição consiste em construir um objeto maior injetando objetos menores e independentes nele.

A herança em C# define uma relação do tipo "é-um" com forte acoplamento entre classes, enquanto a composição define uma relação "tem-um" com baixo acoplamento e maior flexibilidade.
# 77. Os Pilares da OO: Encapsulamento

- **`public`**: O acesso é livre e sem restrições.
- **`internal`**: O acesso é restrito ao projeto atual.
- **`protected`**: O acesso é permitido na própria classe e em suas classes filhas (herança).
- **`private`**: O acesso é limitado apenas à classe onde foi criado.

# 79. Herança #01

A herança entre as classes deve ser realizado por meio de `:`. Por exemplo:

```csharp
public class ContaCorrente : Usuario
{
}
```

Caso a superclasse não possua método construtor padrão, será necessário escrever a herança do método construtor da subclasse. Exemplo:

```csharp
public class ContaCorrente : Usuario
{
    public ContaCorrente(string nome, string email, string senha) : base(nome, email, senha)
    {

    }
}
```

# 80. Herança #02

## Métodos sobrescritos

Caso você queira criar um método sobrescrito, será necessário colocar `override` no método da subclasse e `virtual` no método da superclasse. Exemplo:

```csharp
public class Carro
{
	protected int Velocidade;

	public Carro(int velocidade)
	{
		if (velocidade < 0)
		{
			Velocidade = 0;
		}
		Velocidade = velocidade;
	}

	public virtual int AumentarVelocidade()
	{
		Velocidade += 5;
		return Velocidade;
	}
}

public class Audi : Carro
{
    public Audi() : base(30)
    {

    }

    public override int AumentarVelocidade()
    {
        Velocidade += 10;
        return Velocidade;
    }
}
```

Se a instanciação utilizar a subclasse, então o método sobrescrito será chamado, independente se a declaração for feita com superclasse ou a subclasse.

```csharp
// O resultado será o mesmo.
Audi audi = new Audi();
Console.WriteLine(audi.AumentarVelocidade());
            
Carro audi2 = new Audi();
Console.WriteLine(audi2.AumentarVelocidade());
```

## Ocultação de método

Permite você utilizar tanto o método da subclasse quanto o método da superclasse. Para isso, utilize o comando `new` na assinatura do método da subclasse.

```csharp
public class Audi : Carro
{
    public Audi() : base(30)
    {

    }

    public override int AumentarVelocidade()
    {
        Velocidade += 10;
        return Velocidade;
    }

    public new int ReduzirVelocidade()
    {
        if (Velocidade > 0)
        {
            Velocidade -= 10;
        }
        return Velocidade;
    }
}
```

Neste caso, se a declaração da variável for feita com a superclasse, então será chamado o método da superclasse, mas se a declaração da variável for feita com o método da subclasse, então será utilizado o método da subclasse. Exemplo:

```csharp
// Os resultados serão diferentes.
Audi audi = new Audi();
Console.WriteLine(audi.ReduzirVelocidade()); // 20
            
Carro audi2 = new Audi();
Console.WriteLine(audi2.ReduzirVelocidade()); // 25
```

# 81. Construtor: Usando o this

## Diferença entre `base()` e `this()`

O `base()` serve para referenciar um método construtor da superclasse, enquanto que o método `this()` serve para referenciar um método construtor da própria classe. Exemplo de uso do método  `this()`:

```csharp
protected int Velocidade;
protected string Motor;

public Carro(int velocidade)
{
    if (velocidade < 0)
    {
        Velocidade = 0;
    }
    Velocidade = velocidade;
}

public Carro(int velocidade, string motor) : this(velocidade)
{
    Motor = motor;
}
```

## Método `ToString()`

Utilize a seguinte assinatura para sobrescrever o método `ToString()`:

```csharp
public override string ToString(){
	...
}
```
# 82. Encapsulamento

## Como criar projetos

Botão direito na Solution → Add → New Project... → Class Library → Next → escolha o nome do projeto → Next.
## O que é uma referência?

Uma referência entre projetos é quando um projeto depende de outro projeto para poder usar suas classes, métodos, interfaces etc.
## Modificadores de acesso para os membros da classe

- **`public`**
- **`procted internal`:** permite o acesso dos membros caso esteja no mesmo projeto ou se for uma subclasse (ainda que em projetos diferentes).
- **`protected`**
- **`internal`**
- **`private protected`:** os membros podem ser acessados pela própria ou por subclasses (desde que estejam no mesmo pacote).
- **`private`**

**OBS.: sempre comece com um modificador de acesso mais restrito e, na medida em que precisar aumentar o acesso do membro as outras partes do sistema, vai trocando o modificador.**
# 84. Classe Abstrata

## Considerações sobre métodos abstratos

- Um método abstrato implementado na subclasse precisa ter o `override`, mas, no caso da superclasse abstrata, não será necessário colocar o `virtual` no método abstrato.
- Uma classe abstrata pode ter tanto métodos implementados como também métodos abstratos. Em relação aos métodos abstratos, estes precisam ser implementados nas subclasses.

# 85. Interface

## Considerações sobre algumas regras

- Por padrão, métodos de uma interface já são públicos e abstratos. No entanto, o método implementado, que referência um método abstrato de uma interface, precisa ter o `public` explícito.
- O nome dos parâmetros de um método implementado não necessariamente precisam ser os mesmos do método abstrato. Exemplo:

```csharp
public interface Interface1
{
    string retornarMsg(string msg);
}

public class Msg: Interface1
{
    public string retornarMsg(string mensagem)
    {
        return mensagem;
    }
}
```

- Caso uma interface X herde de outra interface Y, a classe que implementar a interface X deve também não só implementar os seus métodos como também os métodos da interface Y.

```csharp
public interface Interface1: Interface2
{
    string retornarMsg(string msg);
}

public interface Interface2
{
    int retornarSoma(int a, int b);
}

public class Msg: Interface1
{
    public string retornarMsg(string mensagem)
    {
        return mensagem;
    }

    public int retornarSoma(int x, int y)
    {
        return x + y;
    }
}
```

# 86. Classe e Método Sealed

Comando que impede que:
- Classes que sejam herdadas por outras classes.
- métodos sobrescritos sejam alterados.
