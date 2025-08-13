
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