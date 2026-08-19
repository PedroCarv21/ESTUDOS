# 67. Array

Declarando e inicializando um vetor:

```csharp
int[] idades = new int[3];
idades[0] = 23;
idades[1] = 55;
idades[2] = 45;
```
# 68. List

- **`Add()`:** adiciona um elemento na lista.
- **`AddRange`:** adiciona os elementos de uma lista em outra lista.
- **`RemoveAt()`:** remover um item da lista por meio do índice.
- **`IndexOf()`:** capturar o índice por meio de um elemento da lista passado como argumento.

```csharp
var usuariosCadastrados = new List<Usuario>();
usuariosCadastrados.Add(new Usuario("Pedro", "pedro@gmail.com", "p123"));

var novosUsuarios = new List<Usuario>()
{
    new Usuario("Maria", "maria@gmail.com", "m123"),
    new Usuario("Jose", "jose@gmail.com", "j123"),
};

usuariosCadastrados.AddRange(novosUsuarios);

usuariosCadastrados.RemoveAt(0);

foreach (Usuario usuario in usuariosCadastrados)
{
    Console.WriteLine($"Indice: {usuariosCadastrados.IndexOf(usuario)} { usuario}");
}
```

# 69. ArrayList

Utilize o construtor `ArrayList()` para a criação de uma coleção de elementos de vários tipos. Exemplo:

```csharp
var listaMista = new ArrayList()
{
    3.45,
    "hello",
    true
};
```

**OBS.: importe o `System.Collections;`.**

Para listar os elementos de um objeto `ArrayList` através de um `foreach`, declare a variável como `Object` ou `var`. Exemplo:

```csharp
foreach (Object item in listaMista) 
{
    Console.WriteLine($"{item} é do tipo {item.GetType()}.");
}
```

**OBS.: o método `GetType()` é utilizado para retornar o tipo de um valor.**

# 70. Set

Coleção que não permite elementos repetidos e também possibilita o acesso aos elementos por meio do índice, ou seja, não é indexado.

```csharp
var set = new HashSet<string>()
{
    "Pedro",
    "Maria",
    "Jose"
};

Console.WriteLine(set.Count); // 3
set.Add("Maria");
Console.WriteLine(set.Count); // 3, mesmo depois de tentar adicionar um novo item.
```

Outros métodos do `HashSet`:

- **`Contains()`:** verifica se o objeto está presente no set.
- **`Add()`:** adiciona um novo valor.
- **`Remove()`:** remove um item de acordo com o valor informado.

# 71. Queue

Essa coleção representa uma fila, sendo que o primeiro elemento a entrar é também o primeiro a sair (FIFO).

- **`Enqueue()`:** adiciona um elemento na fila.
- **`Peek()`:** retorna o primeiro elemento da fila.
- **`Dequeue()`:** retorna e exclui o primeiro elemento da fila.

```csharp
var queue = new Queue<string>();
queue.Enqueue("Pedro");
queue.Enqueue("José");
queue.Enqueue("Maria");

Console.WriteLine(queue.Peek());
Console.WriteLine(queue.Count);
Console.WriteLine(queue.Dequeue());
Console.WriteLine();
```

É possível também utilizar o construtor `Queue()` para agrupar elementos de tipos diferentes:

```csharp
var queue = new Queue();
queue.Enqueue(6);
queue.Enqueue("hello");
queue.Enqueue(4.5);

foreach (Object item in queue)
{
    Console.WriteLine(item);
}
```

**OBS.: importe o `System.Collections;`.**

# 72. Igualdade (Equals e GetHashCode)

## Objetos `HashSet`

Sobrescreva os métodos `Enquals()` e `GetHashCode()` caso o objeto `HashSet` receba elementos de um tipo personalizado.  

# 73. Stack

Representa uma pilha, possuindo os seguintes métodos:

- **`Push()`:** adiciona um elemento no topo da pilha.
- **`Peek()`:** retorna o elemento no topo da pilha.
- **`Pop()`:** exclui o elemento no topo da pilha.

Exemplo de uso:

```csharp
var pilha = new Stack<string>();
pilha.Push("Pedro");
pilha.Push("Maria");
pilha.Push("José");

ListarPilha(pilha);

Console.WriteLine(pilha.Peek());
Console.WriteLine();

pilha.Pop();

ListarPilha(pilha);
```

# 74. Dictionary

- **`Add()`:** adiciona um par chave-valor no dicionário.

```csharp
var produtos = new Dictionary<string, decimal>();
produtos.Add("TV", 4500.30m);
produtos.Add("Livro", 123.4m);
produtos.Add("Fone de ouvido", 450.6m);
```

- **`Key`:** obtém a chave de um dos itens.
- **`Value`:** obtém o valor de um dos itens.

```csharp
foreach (var item in produtos)
{
	Console.WriteLine($"{item.Key} => {item.Value}");
}
```

- **`ContainsKey()`:** verifica se existe uma chave no dicionário.

```
if (produtos.ContainsKey("Livro"))
{
	Console.WriteLine(produtos["Livro"]);
}
Console.WriteLine();
```

- **`TryGetValue()`:** tentará, através de uma chave informada, obter o valor vinculado e armazená-lo no segundo argumento.

```csharp
produtos.TryGetValue("TV", out decimal preco);
Console.WriteLine(preco);
Console.WriteLine();
```

- **`Keys`:** retorna uma coleção de chaves do dicionário.
- **`Values`:** retorna uma coleção de valores do dicionário.

```csharp
foreach (string chave in produtos.Keys)
{
	Console.WriteLine(chave);
}
Console.WriteLine();

foreach (decimal valor in produtos.Values)
{
	Console.WriteLine(valor);
}
Console.WriteLine();
```

- **`KeyValuePair`:** struct que representa um par chave-valor.

```csharp

foreach (KeyValuePair<string, decimal> produto in produtos)
{
	Console.WriteLine($"{produto.Key} = {produto.Value}");
}
```

- **`GetValueOrDefault()`:** retorna, através da chave informada, o valor vinculado ou 0, caso não encontre a chave.

```csharp
Console.WriteLine(produtos.GetValueOrDefault(""));
```

