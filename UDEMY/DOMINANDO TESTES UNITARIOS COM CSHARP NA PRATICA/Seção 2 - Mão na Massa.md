# 3. Fundamentos sobre os Testes de Unidade

## Atributo `[Fact]`

É um atributo utilizado para tornar um método testável. Exemplo:

```csharp
[Fact(DisplayName = "Somar_Numeros_Positivos")]
public void Somar_NumerosPositivos_DeveRetornarSomaCorreta()
{
    Calculadora calculadora = new Calculadora();

    int resultadoObtido = calculadora.Somar(10, 30);

    Assert.Equal(40, resultadoObtido);
}
```

O `DisplayName` é um parâmetro que permite definir o nome do método que será exibido no Test Explorer.
### Classe `Asssert`

Essa classe fornece vários métodos para testes. Um deles é o `Equal`, utilizado para verificar se o resultado esperado é igual ao resultado obtido. O primeiro argumento é referente ao resultado esperado enquanto que o segundo parâmetro é referente ao resultado obtido.
## Atributo `[Theroy]` e `[InlineData]`

São atributos utilizados para tornar testável um método parametrizado. No caso do `[InlineData]`, serão passados os argumentos. Isso permite o método ser testado vários vezes com argumentos distintos. Exemplo:

```csharp
[Theory]
[InlineData(3, 3, 6)]
[InlineData(5, 8, 13)]
public void Somar_VariosNumerosPositivos_DeveRetornarSomaCorreta(int num1, int num2, int resultadoEsperado)
{
    Calculadora calculadora = new Calculadora();

    int resultadoObtido = calculadora.Somar(num1, num2);

    Assert.Equal(resultadoEsperado,  resultadoObtido);
}
```

# 4. Asserções ( Asserts )

- **`Assert.Contains()`:** verifica se a string está contida no resultado obtido. Exemplo:
  ```csharp
[Fact]
public void String_NomeCliente_DeveConterPalavra()
{
    Cliente cliente = new Cliente("Pedro", "Carvalho", 3000);

    var nomeCompletoObtido = cliente.ObterNomeCompleto();

    Assert.Contains(expectedSubstring: "Pedro", actualString: nomeCompletoObtido);
}
  ```

**OBS.: é possível deixar os argumentos nomeados de modo a deixar claro qual argumento representa o valor esperado e qual argumento representa o valor obtido.**

- **`Assert.StartsWith()`:** compara se a string obtida começa com um conjunto de caracteres esperado.
- **`Assert.EndsWith()`:** compara se a string obtida termina com um conjunto de caracteres esperado.
- **`Assert.True()`:** verifica se o resultado retornou `true`. Exemplo:
```csharp
[Fact]
public void Cliente_Nome_DeveSerNuloOuVazio()
{
    Cliente cliente = new Cliente("", "Carvalho", 3000);

    Assert.True(String.IsNullOrEmpty(cliente.Nome));
}
```
- **`Assert.False()`:** verifica se o resultado retornou `false`. 
- **`Assert.NotEqual()`:** verifica se o resultado esperado é diferente do resultado obtido. Exemplo:
```csharp
public void Calculadora_Somar_NaoDeveSerIgual()
{
    Calculadora calculadora = new Calculadora();

    var resutadoObtido = calculadora.Somar(10, 5.7);

    Assert.NotEqual(expected: 15, actual: resutadoObtido, precision: 2);
}
```

**OBS.: o parâmetro `precision` representa a casa decimal que será adicionada ao valor passado como `expected`.**
- **`Assert.InRange()`:** averiguar se o valor obtido se encontra dentro do intervalo de valores informado. Exemplo:
  ```csharp
[Theory]
[InlineData(2000)]
[InlineData(6000)]
public void Cliente_Salario_DeveDefinirFaixaSalarialCorreta(double salario)
{
    var cliente = new Cliente("Carlos", "Maria", salario);

    if (cliente.PerfilCliente == PerfilClienteEnum.Normal)
        Assert.InRange(actual: cliente.Salario, 0, 4999);
    else if (cliente.PerfilCliente == PerfilClienteEnum.Vip)
        Assert.InRange(actual: cliente.Salario, 5000, 9999);
}
  ```
- **`Assert.Throws<>()`:** verifica se a função passada como argumento retorna a exceção esperada e que foi informada no operador diamante. Exemplo:
```csharp
[Fact]
public void Cliente_Salario_DeveRetornarExceptionPorSalarioInvalido()
{
    var exception = Assert.Throws<Exception>(() => new Cliente("Pedro", "Carvalho", 300));

    Assert.Equal(expected: "Salário inválido", actual: exception.Message);
}
```

