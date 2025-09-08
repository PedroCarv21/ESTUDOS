
## 97. Criando as estruturas básicas da API

### Comando `unique`

É inserido em um determinado campo de uma tabela com o intuito de que os valores daquele campo não sejam duplicados. Exemplo:

```sql
create table livro(  
    id uuid primary key not null,  
    isbn varchar(20) not null unique,  
    titulo varchar(150) not null,  
    data_publicacao date not null,  
    genero varchar(30) not null,  
    preco numeric(18, 2) not null,  
    data_cadastro timestamp,  
    data_atualizacao timestamp,  
    id_usuario uuid,  
    id_autor uuid not null references autor(id),  
    constraint chk_genero check (genero in ('FICCAO', 'FANTASIA', 'MISTERIO', 'ROMANCE', 'BIOGRAFIA', 'CIENCIA'))  
);
```

Neste exemplo, o campo `isbn` não terá valores duplicados.

## 98. Endpoint para cadastro de livro com Bean Validation
### Anotação `@ISBN`

É utilizado em um campo de uma classe para verificar se o código passado é um ISBN válido.

**OBS.: ISBN é um código numérico único que identifica livros, artigos, entre outras publicações.**

## 99. Conhecendo e configurando o MapStruct no projeto

### O que é MapStruct?

MapStruct é um gerador de código para Java que automatiza o processo de mapeamento entre objetos, simplificando o trabalho de desenvolvedores que precisam converter dados de um tipo de objeto para outro.
### Como configurar o MapStruct no `pom.xml`?

- Informe a versão do MapStruct dentro da tag  `<properties>`, que indica a versão do processador:

```xml
<org.mapstruct.version>1.6.3</org.mapstruct.version>
<lombok-mapstruct-binding.version>0.2.0</lombok-mapstruct-binding.version>
```

- Adicione a dependência do MapStruct em `<dependencies>`:

```xml
<dependency>  
    <groupId>org.mapstruct</groupId>  
    <artifactId>mapstruct</artifactId>  
    <version>${org.mapstruct.version}</version>  
</dependency>
```

- Adicione o plugin do MapStruct dentro da tag `<plugins>`. Ele será responsável por configurar o compilador para que gere o código-fonte dos mappers e do Lombok, de modo que ambos funcionem juntos e sem erro.

**OBS.: um mapper é uma interface com a anotação `@Mapper`, criada para definir como a a transformação de um tipo de objeto em outro deve acontecer.**

```xml
<plugin>  
    <groupId>org.apache.maven.plugins</groupId>  
    <artifactId>maven-compiler-plugin</artifactId>  
    <version>3.8.1</version>  
    <configuration>  
       <source>1.8</source> <!-- depending on your project -->  
       <target>1.8</target> <!-- depending on your project -->  
       <annotationProcessorPaths>  
          <path>  
             <groupId>org.mapstruct</groupId>  
             <artifactId>mapstruct-processor</artifactId>  
             <version>${org.mapstruct.version}</version>  
          </path>  
          <!-- other annotation processors -->  
          <path>  
             <groupId>org.projectlombok</groupId>  
             <artifactId>lombok</artifactId>  
             <version>${lombok.version}</version>  
          </path>  
  
          <path>  
             <groupId>org.projectlombok</groupId>  
             <artifactId>lombok-mapstruct-binding</artifactId>  
             <version>${lombok-mapstruct-binding.version}</version>  
          </path>  
       </annotationProcessorPaths>  
    </configuration>  
</plugin>
```

Dentro da tag `annotationPrecessorPaths`, se encontram a lista de processadores que o Maven deve executar durante a compilação:

- `mapstruct-processor`: gera automaticamente os mappers.
- `lombok`: gera automaticamente getters, setters, etc., a partir das anotações do Lombok.
- `lombok-mapstruct-processor`: faz com que o Lombok e o MapStruct trabalhem sem conflitos.

## 100. Criando um mapper do MapStruct

### Como criar um mapper?

É necessário criar uma interface com a anotação `@Mapper`. Esta anotação possui o atributo `componentModel` que recebe o valor `"spring"`, indicando para a anotação que ele deve gerar um bean.

Depois é preciso criar os métodos para o mapeamento. No exemplo, será convertido um `AutorDTO`para `Autor`  através do método `toEntity()` e também a opção de converter um método `Autor` para `AutorDTO` através do método `toDTO`:

```java
@Mapper(componentModel = "spring")  
public interface AutorMapper {  
  
    Autor toEntity(AutorDTO autorDTO);  
  
    AutorDTO toDTO(Autor autor);  
}
```

**OBS.: o nome dos métodos pode ser qualquer um.**

Caso o nome de um campo do DTO não seja igual ao nome do campo equivalente da entidade (ou vice-versa), é necessário informar isso através da anotação `@Mapping(source = "", target = "")`, colocada em um dos métodos de uma interface Mapper. Em `source`, coloque o nome do campo da classe que você quer converter e em `target`, coloque o nome do campo da classe convertida.
### Dica de como fornecer respostas para a requisição de modo mais eficiente

A classe `Optional` possui dois métodos importantes que substituem o `if` e o `else`:

- `map`: recebe uma expressão lambda e a executa caso o objeto `Optional` possua um valor presente.
- `orElseGet()`: recebe uma expressão lambda e a executa caso o objeto `Optional` não possua um valor nenhum.

```java
@GetMapping("/{id}")  
public ResponseEntity<AutorDTO> obterDetalhes(@PathVariable("id") UUID id){  
  
    return this.autorService.obterPorId(id)  
            .map(autor -> {  
                AutorDTO dto = autorMapper.toDTO(autor);  
                return ResponseEntity.ok(dto);  
            }).orElseGet( () -> ResponseEntity.notFound().build());  
}
```

**OBS.: a diferença entre `orElseGet()` e `orElse()` é que o primeiro excuta apenas quando `Optional` está vazio enquanto o segundo executa sempre, mesmo o `Optional` não sendo vazio.**

## 101. Mapeando e salvando um livro na base de dados

Na aula anterior, foi explicado que, para que haja uma relação entre um campo DTO e um campo de uma entidade com nomes diferentes, é necessário esclarecer isso através da anotação `@Mapping(source = "", target = "")`.

Porém, quando não somente os campos tem nomes diferentes, mas também tipos diferentes, é necessário utilizar o parâmetro `expression` em vez de `source`. O parâmetro `expression` será responsável por aplicar o código java, passado como valor, no campo informado no parâmetro `target`.

Por exemplo, o `CadastroLivroDTO` possui o campo `idAutor` do tipo `UUID` enquanto a entidade `Livro` possui o campo `autor` do tipo `Autor`. É preciso então buscar um registro da tabela `Autor`, através do campo `idAutor`, e devolvê-lo para o campo `autor` da entidade `Livro`.

Para isso, será necessário que o objeto retornado do método `autorRepository.findById(cadastroLivroDTO.idAutor()).orElse(null)` seja inserido no campo `autor`. Portanto, este código deve ser passado dentro do parâmetro `expression`.

Por fim, este código deve ser inserido dentro de `java ()`, para indicar que se trata de um código Java.

```java
@Mapper(componentModel = "spring")  
public abstract class LivroMapper {  
  
    @Autowired  
    AutorRepository autorRepository;  
  
    @Mapping(target = "autor", expression = " java( autorRepository.findById(cadastroLivroDTO.idAutor()).orElse(null) ) ")  
    public abstract Livro toEntity(CadastroLivroDTO cadastroLivroDTO);  
  
}
```

Como foi necessário a criação de um atributo para a resolução deste problema, teve que se usar uma classe abstrata em vez de uma interface.

## 102. Criando interface generica para nos ajudar nos controllers

### Nota sobre interfaces

Caso você queira criar um corpo em um método de uma interface, é necessário que esse método seja `default`. Exemplo:

```java
public interface GenericController {  
  
    default URI gerarHeaderLocation(UUID id){  
        return ServletUriComponentsBuilder  
                .fromCurrentRequest()  
                .path("/{id}")  
                .buildAndExpand(id)  
                .toUri();  
    }
}
```

## 104. Obtendo detalhes do livro - Mapstruct utilizando composição de outro mapper

### A necessidade de mappers dentro de mappers

Em casos onde seja necessário utilizar de um mapper para o mapeamento de uma das colunas da entidade e do DTO, é possível especificar o mapper através do parâmetro `uses` da anotação `@Mapper`:

```java
@Mapper(componentModel = "spring", uses = AutorMapper.class)  
public abstract class LivroMapper {  
  
    @Autowired  
    AutorRepository autorRepository;  
  
    @Mapping(target = "autor", expression = " java( autorRepository.findById(cadastroLivroDTO.idAutor()).orElse(null) ) ")  
    public abstract Livro toEntity(CadastroLivroDTO cadastroLivroDTO);  
  
    public abstract ResultadoPesquisaLivroDTO toDTO(Livro livro);  
  
}
```

Neste exemplo, o método `toDTO` fará o mapeamento da entidade `Livro` para o DTO `ResultadoPesquisaLivroDTO`. A entidade possui o campo `autor` do tipo `Autor` e o DTO possui o campo `autor` do tipo `AutorDTO`. Por essa razão, é necessário especificar o mapper pelo parâmetro `uses` que realizará o mapeamento correto destes dois campos.

## 106. Entendendo o que é uma Specification do Spring Data JPA

### Interface `Specification`

Esta interface possibilita a construção de consultas dinâmicas com base em critérios (campos) específicos. 

Para que um repositório tenha suporte a consultas baseadas em `Specification`, é necessário estendê-la com a interface `JpaSpecificationExecutor`, recebendo a entidade na parte do generics. Exemplo:

```java
public interface LivroRepository extends JpaRepository<Livro, UUID>, JpaSpecificationExecutor<Livro> {
    ...
}
```

## 107. Implementando as Specifications da entidade Livro

A interface `Specification` pode ser transformada na seguinte expressão lambda:

```java
Specification<Livro> specs = (root, query, criteriaBuilder) -> criteriaBuilder.conjunction();
```

Tal expressão lambda possui os seguintes métodos:

- `Root<T> root`: usada para acessar os atributos de uma entidades através do método `root.get()`. Este método deve receber como argumento o nome de algum atributo da entidade informada como tipo genérico. No exemplo anterior, o tipo genérico foi `Livro`, portanto, deveria ser passado algum atributo como argumento (ex.: `root.get("titutlo")`).
- `CriteriaQuery<?> query`: representa a consulta em si. Normalmente, não é preciso mexer muito nele, a menos que queira:
	- definir ordenação,
	- usar `distinct`,
	- fazer subconsultas etc.
- `CriteriaBuilder cb`: disponibiliza predicados (`equal`, `like`, `and`, `or`, `upper`, etc.) para construir a consulta.

Exemplo de um método que utiliza estes recursos:

```java
public static Specification<Livro> isbnEqual(String isbn){  
    return (root, query, cb) -> cb.equal(root.get("isbn"), isbn);  
}
```

Em suma este método retorna a seguinte consulta:

```sql
SELECT * FROM Livro WHERE isbn = ?
```

Outro exemplo mais sofisticado:

```java
public static Specification<Livro> tituloLike(String titulo){  
    return (root, query, cb) ->  
            cb.like(  
                    cb.upper(root.get("titulo")),  
                    "%" + titulo.toUpperCase() + "%"  
            );  
}
```

Este código representa a seguinte consulta SQL:

```SQL
SELECT * FROM Livro
WHERE UPPER(titulo) LIKE CONCAT('%', UPPER(?), '%');
```

**OBS.: a função `UPPER()` torna os valores encontrados no campo 'titulo' em caixa alta. Já a função `CONCAT` concatena os valores passados como argumento.**

Caso deseje fazer uma consulta simples, é possível utilizar o método `conjunction()` do `CrieteriaBuilder`:

```java
Specification<Livro> specs = (root, query, criteriaBuilder) -> criteriaBuilder.conjunction();
```

Isso equivale a `SELECT * FROM Livro where 1 = 1`.

## 108. Utilizando functions do banco na Specification JPA

### Função `to_char`

Esta é uma função do PostgreSQL utilizada para converter certos tipos de valores (como `timestamp`, `integer`, entre outros) em uma `String`. É possível ainda informar qual será o formato da `String` retornada:

```sql
select to_char(data_publicacao, 'YYYY') from livro;
```

O código acima faz uma consulta das datas encontrados na coluna `data_publicacao` da tabela `Livro` e retorna apenas o ano.

### Utilização do `to_char` em um método Java

Suponha que deva ser construído um método que compare os valores encontrados no campo `dataPublicacao` com o ano expresso como argumento.

Para fazer essa comparação, será necessário o método `cb.equal`, que receberá a função `to_char` como argumento e o ano como segundo argumento.

Para especificar o uso de `to_char`, é preciso utilizar o método `cb.function()` e passar a `String` `"to_char"` como o primeiro argumento. O segundo que `cb.function()` receberá é `String.class`, que especifica o tipo de retorno esperado de `to_char`.

O terceiro argumento é o nome do campo **da entidade** cujo os valores serão comparados (neste caso é `dataPublicacao`, que ser passado como argumento de `root.get()`). Por fim, informe o formato em que data deve retornar através de `cb.literal()` (por exemplo, `cb.literal("YYYY")`). Exemplo:

```java
public static Specification<Livro> dataPublicacaoEqual(Integer anoPublicaco){  
    return (root, query, cb) ->  
            cb.equal(cb.function(  
                    "to_char", String.class, root.get("dataPublicacao"), cb.literal("YYYY")),  
                    anoPublicaco.toString()  
            );  
}
```

## 109. Criando joins ao utilizar Specifications JPA

Há duas formas de se fazer um join entre duas entidades.
### Primeira solução

É possível chamar um método `get()` a partir de outro método `get()`. 

Por exemplo, a entidade `Livro` possui um atributo `autor` do tipo `Autor` (uma outra entidade) que, por sua vez, possui um atributo `nome`. Para acessar este atributo `nome`, seria utilizado o seguinte comando: `root.get("autor").get("nome")`.

O exemplo abaixo mostra um exemplo de uma consulta que compara, através do predicado `like`, o nome passado como argumento com os valores encontrados no campo `nome` da tabela `Autor`, desconsiderando letras maiúsculas e minúsculas.

```java
public static Specification<Livro> nomeAutorLike(String nome) {  
    return (root, query, cb) -> cb.like(  
            cb.upper(root.get("autor").get("nome")),  
            "%" + nome.toUpperCase() + "%");  
}
```

### Segunda solução

A solução anterior é mais simples, porém não permite especificar o tipo de `join` que deve ser realizado (por padrão, é feito um `inner join`). Estas são as opções de `join`:

- `INNER JOIN`: retorna apenas os registros que têm correspondência nas duas tabelas.
- `LEFT JOIN`: retorna todos os registros da tabela da esquerda, e os dados da tabela da direita quando houver correspondência. Quando não houver match, os campos da tabela da direita vêm como `NULL`.
- `RIGHT JOIN`: retorna todos os registros da tabela da direita, e os dados da tabela da esquerda quando houver correspondência. Quando não houver match, os campos da tabela da esquerda vêm como `NULL`.

Para especificar o tipo de `join` que será realizado, utilize o predicado `root.join()`, cujo o primeiro argumento deve ser o atributo correspondente a chave estrangeira e o segundo argumento deve ser uma destas constantes: `JoinType.LEFT`, `JoinType.RIGHT` e `JoinType.INNER`. Armazene o resultado deste predicado em um objeto do tipo `Join` e passe-o como argumento de um predicado `equal` ou `like`.

Este é um exemplo de como utilizar o predicado `join`.

```java
public static Specification<Livro> nomeAutorLike(String nome){  
        return (root, query, cb) -> {  
  
            Join<Object, Object> joinAutor = root.join("autor", JoinType.LEFT);  
            return cb.like(cb.upper(joinAutor.get("nome")), "%" + nome.toUpperCase() + "%");  
   
        };  
    }
```

## 111. Validação de ISBN duplicado

### Operação terminal `anyMatch()`

É utilizado para verificar se algum elemento de uma stream atende a uma determinada condição. Por exemplo: o código a seguir utiliza `anyMatch` para verificar se existe algum nome, presente na lista `nomes`, que começa com a letra 'A'.

```java
List<String> nomes = Arrays.asList("Carlos", "Ana", "João");

boolean temNomeComA = nomes.stream().anyMatch(nome -> nome.startsWith("A"));

System.out.println("Tem nome com A? " + temNomeComA);  // Saída: true
```

## 113. Como implementar pesquisa paginada com Spring Data

### O que é pesquisa paginada?

Significa separar uma quantidade específica de registros pesquisados por página. Desta forma, a consulta não fica tão sobrecarregada como em casos onde uma tabela possui mais de 100.000 registros.
### Como fazer a pesquisa paginada?

A interface `JpaSpecificationExecutor` fornece um método `findAll()`, que recebe um argumento do tipo `Specification` e outro argumento do tipo `Pageable` e retorna um objeto do tipo `Page`.

A interface `Page` irá disponibilizar os campos que informam dados a respeito da paginação, tais como: o total de páginas, o total de elementos, o tamanho da página (quantos registros ela carrega), entre outras informações.

Já a interface `Pageable` oferece um método `of()` para que seja passado como argumento a página em que você deve se encontrar (primeira página, segunda....) e também o tamanho da página. Ambos os valores devem ser inteiros. Exemplo:

```java
    public Page<Livro> pesquisa(  
            String isbn,  
            String nomeAutor,  
            String titulo,  
            GeneroLivro genero,  
            Integer anoPublicacao,  
            Integer pagina,  
            Integer tamanhoPagina){  
  
        Specification<Livro> specs = (root, query, criteriaBuilder) ->  
                criteriaBuilder.conjunction();  
  
        if (isbn != null){  
            specs = specs.and(LivroSpecs.isbnEqual(isbn));  
        }  
  
        if (genero != null){  
            specs = specs.and(LivroSpecs.generoEqual(genero));  
        }  
  
        if (titulo != null){  
            specs = specs.and(LivroSpecs.tituloLike(titulo));  
        }  
  
        if (anoPublicacao != null){  
            specs = specs.and(LivroSpecs.dataPublicacaoEqual(anoPublicacao));  
        }  
  
        if (nomeAutor != null){  
            specs = specs.and(LivroSpecs.nomeAutorLike(nomeAutor));  
        }  
  
        Pageable pageRequest = PageRequest.of(pagina, tamanhoPagina);  
  
        return livroRepository.findAll(specs, pageRequest);  
    }
```

Neste caso, a interface `livroRepository` estende `JpaSpecificationExecutor`, o que dá acesso ao método `findAll()`. Este método recebe então um objeto do tipo `Specification` (a variável `specs`) e outro objeto do tipo `Pageable` (a variável `pageRequest`), que já contém a página em que o usuário se encontra e o tamanho da página através do método `of()`.

É possível definir um valor padrão para a página em que o usuário se encontra e o tamanho da página através da anotação `@RequestParam()` por meio do atributo `defaultValue`.

A interface `Page` também oferece o método `map`, que pode ser muito útil para a transformação de entidade em um DTO. Exemplo:

```java
@GetMapping  
public ResponseEntity<Page<ResultadoPesquisaLivroDTO>> pesquisa(  
        @RequestParam(value = "isbn", required = false)  
        String isbn,  
        @RequestParam(value = "nome-autor", required = false)  
        String nomeAutor,  
        @RequestParam(value = "titulo", required = false)  
        String titulo,  
        @RequestParam(value = "genero", required = false)  
        GeneroLivro genero,  
        @RequestParam(value = "ano-publicacao", required = false)  
        Integer anoPublicacao,  
        @RequestParam(value = "pagina", defaultValue = "0")  
        Integer pagina,  
        @RequestParam(value = "tamanho-pagina", defaultValue = "10")  
        Integer tamanhoPagina){  
  
    Page<Livro> paginaResultado = this.service.pesquisa(isbn, nomeAutor, titulo, genero, anoPublicacao, pagina, tamanhoPagina);  
  
    Page<ResultadoPesquisaLivroDTO> resultado = paginaResultado.map(livroMapper::toDTO);  
  
    return ResponseEntity.ok().body(resultado);  
}
```

### Consulta

Ao fazer a consulta, o corpo da resposta deve devolver uma estrutura mais ou menos parecida com esta:

```json
{
    "content": [
        {
            "id": "76449b0d-57d8-423a-b0d5-e1abf6a4fbe1",
            "isbn": "5656544-4564654",
            "titulo": "Nova Espécie",
            "dataPublicacao": "1999-01-02",
            "genero": "FICCAO",
            "preco": 658,
            "autor": {
                "id": "7fb2820e-2dec-4c85-a9e0-dcdd6f19a8d1",
                "nome": "Antonio",
                "dataNascimento": "1978-08-05",
                "nacionalidade": "Americana"
            }
        },
        {
            "id": "6b48fde4-1cd0-43ec-a3df-b1313ffc0359",
            "isbn": "978-0-14-044913-6",
            "titulo": "Republica ATUALIZADO",
            "dataPublicacao": "1900-01-01",
            "genero": "CIENCIA",
            "preco": 10,
            "autor": {
                "id": "01743a13-dc39-43dd-b493-61adb7a8a03b",
                "nome": "Pedro",
                "dataNascimento": "2025-07-29",
                "nacionalidade": "brasileiro"
            }
        }
    ],
    "pageable": {
        "pageNumber": 1,
        "pageSize": 2,
        "sort": {
            "empty": true,
            "sorted": false,
            "unsorted": true
        },
        "offset": 2,
        "paged": true,
        "unpaged": false
    },
    "totalPages": 4,
    "totalElements": 7,
    "last": false,
    "size": 2,
    "number": 1,
    "sort": {
        "empty": true,
        "sorted": false,
        "unsorted": true
    },
    "first": false,
    "numberOfElements": 2,
    "empty": false
}
```

