# 93. Exceções e Tratamento de Erro

## Como lançar uma exceção

Com `throw new` e mais um classe de exceção. Por exemplo:

```csharp
throw new ArgumentException("Saldo não pode ser negativo");
```

## Como utilizar o bloco try-catch-finally

```csharp
try{ 

}
catch (Exception ex)
{

}
finally
{

}
```
# 94. Criando Exceções Personalizadas

Crie uma subclasse de `Exception`. Por exemplo:

```csharp
internal class ValorNegativoException : Exception
{
    public ValorNegativoException() {}

    public ValorNegativoException(string message) : base(message) {}
}
```