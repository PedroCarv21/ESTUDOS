
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

