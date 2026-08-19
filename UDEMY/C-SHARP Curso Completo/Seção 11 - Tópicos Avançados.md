# 103. LINQ #01

## O que é LINQ (Language Integrated Query)?

É um recurso utilizado para consultas avançadas de dados que podem vir de várias fontes distintas (como listas ou banco de dados), apresentando-se como uma alternativa aos loops de repetição tradicionais.

## Principais métodos

Todos eles recebem arrow functions (com exceção do `ToList`) para realizar as operações.

- **`Where()`:** filtra os dados.
- **`OrderBy()`:** ordena os dados. Caso queira em ordem decrescente, utilize o - após o `=>`.
- **`Select()`:** extrai dados dos objetos da coleção para armazená-los em outra coleção.
- **`ToList()`:** retorna os dados dentro de uma lista.

### Exemplo

Filtrando os alunos com nota maior que 5, colocando em ordem decrescente, extraindo o nome dos alunos e, por fim, retornando uma lista:

```csharp
List<Aluno> alunos = new List<Aluno>()
{
    new Aluno("Pedro", 15, 7.0),
    new Aluno("Julia", 25, 9.0),
    new Aluno("Ana", 17, 5.0),
    new Aluno("Marcus", 20, 8.0),
};

List<string> alunosAprovados = alunos
    .Where(a => a.Nota > 5.0)
    .OrderBy(a => -a.Nota)
    .Select(a => a.Nome).ToList();
```

É possível fazer o mesmo processo da seguinte forma:

```csharp
var alunosAprovados2 = from aluno in alunos
where aluno.Nota > 5.0
orderby -aluno.Nota
select aluno.Nome;
```