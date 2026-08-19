# Qual a diferença entre classe e struct?

A diferença está na maneira como são armazenados. Classes são **tipos de referência** alocados na _Heap_, que exigem coleta de lixo. Structs são **tipos de valor** alocados diretamente na _Stack_ (ou embutidos no contexto).

# Qual a diferença entre `virtual` e `override`?

`virtual` permite que um método seja sobrescrito.

`override` substitui a implementação herdada.

Exemplo:

```
public virtual void Inicializar()
```

na `TestBase`.

Depois:

```
public override void Inicializar()
```

na `FaturaServiceTests`.
# O que é LINQ (**Language Integrated Query**)?

É uma tecnologia .NET utilizada para buscar, filtrar e transformar dados de alguma fonte de forma muito mais prática do que utilizar loops e condições.
# Quais outros tipos de testes você faria?

Tentar remover um item inexistente ou tentar buscar uma fatura com base em um id inexistente.

# Qual a diferença entre classe abstrata e interface?

**classes abstratas** definem uma base compartilhada (estado e comportamento) com **herança única**, enquanto **interfaces** determinam contratos estritos (apenas assinaturas) que permitem **múltiplas implementações**

# Quais são os quatro tipos de controlares de acesso?

- Public
- Private
- Protected: O membro só pode ser acessado dentro de sua própria classe ou por classes derivadas (que herdam essa classe).
- Internal: limita o acesso ao assembly (projeto).

# O que significa implementar IDisposable?

Significa que a classe possui recursos que precisam ser liberados.

# Qual a diferença entre `throw` e `throw ex`?

- `throw`: relança a exceção original exatamente como ela chegou. O registro de erro (StackTrace) manterá o rastro completo, mostrando que o erro começou no `MetodoB` e passou pelo `MetodoA`.
- `throw ex:` substitui o StackTrace original pelo momento em que a nova exceção foi disparada.

# Qual a diferença entre tipos por valor e por referência?

- Por valor: contêm os dados diretamente (armazenados na _Stack_). Exemplo: `int`, `float`, `bool`, `char`
- Por referência: armazenam apenas o endereço de memória onde os dados reais estão (alocados na _Heap_). Exemplo `classes`, `interfaces`, `string`

# O que é o FluentValidation?

Biblioteca do .NET utilizada para criar regras de validação de dados em objetos, de maneira fácil de ler.

# O que é o AutoMapper?

É uma biblioteca open-source do .NET que automatiza o mapeamento de um objeto para outro. Ela serve para copiar dados de um objeto para outro de forma automática, poupando o desenvolvedor de escrever códigos repetitivos e manuais ao converter, por exemplo, uma entidade de banco de dados para um DTO