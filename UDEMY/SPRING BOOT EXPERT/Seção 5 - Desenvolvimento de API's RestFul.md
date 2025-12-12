# 75. Entendendo tudo sobre Rest, HTTP e Requests

## O que é Rest?

Um conjunto de diretrizes sobre como deve ser implementado uma API web. Dentre as diretrizes em destaque estão:
- Utilização dos métodos HTTP (GET, POST, PUT e DELETE) para realizar operações.
- Uso de URL's para identificar recursos específicos.
- Transferência de dados entre cliente e servidor por meio de um formato padrão como JSON ou XML.

## Qual a diferença do Rest para Restful?

Restful é simplesmente uma referência para as API's que implementam as diretrizes Rest.
## Estrutura de uma Request (solitação)

- **URL**
- **Cabeçalho (Header)**: contém informações adicionais (metadados) sobre a requisição que está sendo feita. Exemplos:
	- **Accept**: informa o formato dos dados que o cliente espera (JSON, XML, etc...).
	- **Content-type**: o tipo de conteúdo que será enviado (JSON, XML, etc...).
	- **Authorization**: informações de autenticação como, por exemplo, um token.
	- **Host**: especifica o nome do domínio do servidor e a porta em que ele está escutando.
	- **User-Agent**: descreve qual foi o tipo de cliente que solicitou a requisição (Navegador FireFox, Postman, etc...).
- **Body (opcional)**
- **Verbos HTTP**:
	- **GET**
	- **POST**
	- **PUT**
	- **DELETE**
	- **PATCH**: diferente do método PUT, onde é atualizado por completo um registro, o método PATCH atualiza parcialmente alguns dados do registro.
	- **HEAD**: solicita metadados do servidor, porém sem o body da mensagem na resposta (como no caso do GET).
	- **OPTIONS**: informa as opções de requisição para um determinado recurso no servidor.

**OBS.: um recurso refere-se a qualquer componente para um cliente ou aplicação que o servidor pode fornecer. Isso pode incluir hardware (como processamento, armazenamento, memória) ou software (como aplicativos, serviços, APIs).**

# 76. Entendendo a composição de respostas do servidor

## Estrutura do response

- **Header**: 
	- **Content-type**
	- **Set-Cookie**: armazena um cookie que indica a sessão do usuário.
	- **Location**: informa qual a URL da API que o cliente está tentando acessar.
- **Body (opcional)**:
- **Código de status**:
	- **200 (Ok)**: a requisição foi bem sucedida.
		- **201 (Created)**: um novo recurso foi criado com sucesso.
		- **202 (Accepted)**: o servidor validou o formato da solicitação e a colocou em uma fila interna para processamento, caso seja um processo de longa duração ou uma operação diária.
		- **204 (No Content)**: a requisição foi realizada com sucesso, porém o servidor não retorna nada (como no caso de, por exemplo, uma deleção de um registro).
	- **400 (Bad request)**: houve algum erro na solicitação enviada pelo cliente.
		- **401 (Unauthorized)**: a solicitação teve problemas devido a falta de credenciais de autenticação corretas.
		- **403 (Forbidden)**: ocorre quando o cliente está autenticado, porém tenta acessar um recurso que o servidor não lhe autorizou (por alguma razão).
		- **404 (Not Found)**: quando o cliente tenta acessar um recurso que não existe no servidor.
		- **405 (Method Not Allowed)**: a solicitação enviada não é suportada (por exemplo, quando o cliente faz uma requisição por meio de um get, porém o único método disponível é um post).
		- **409 (Conflict)**: o conceito sobre este código de status já foi esclarecido na sessão 3:
		- ![[Seção 3 - Arquitetura e Estrutura do Framework#^55f860]]
		- **422 (Unprocessable Entity)**: quando o servidor recebe uma mensagem com erro semântico (como, por exemplo, campos obrigatórios não preenchidos) ou não atende a determinadas condições (como a violação de regras de negócio). ^53643b
	- **500 (Erro de Server)**: indica uma dificuldade de processamento do servidor.

# 77. Aprenda a modelar contratos de APIs

## O que é um contrato de API?

É a definição das regras de interação entre um cliente e uma API. Estas regras podem incluir: a URL utilizada para acessar a API, o verbo HTTP daquela API, o código status esperado, entre outras.

## Como definir um contrato?

- **Identificação do recurso (a URL utilizada para acessar o recurso)**: é recomendado que as URL's sejam substantivos no plural em vez de verbos que descrevam qual será a operação daquele recurso:
	- ![[Pasted image 20250716125340.png]]
- **Método/verbo HTTP apropriado**:
- **Código de status apropriado**: é preciso seguir esta combinação de código de status de acordo com cada tipo de requisição:
	- ![[Pasted image 20250716125208.png]]
- **Definição do payload (conteúdo da mensagem) do request e response**:
- **Definição dos headers**

# 80. Mapeamento de Requisição e padrão DTO

## Alternativas às anotações padrão para operações HTTP

É possível, além das anotações utilizadas geralmente (como `@GetMapping`, `@PostMapping`, etc ), usar o próprio `RequestMapping` para descrever o tipo operação HTTP que o método irá realizar.

Por exemplo, em vez de `@PostMapping`, é possível utilizar `@RequestMapping(method = RequestMethod.POST)`:

```java
@RequestMapping(method = RequestMethod.POST)  
public Object salvar(@RequestBody Autor autor){  
  
}
```

## Uso de records

É um tipo de classe criada de forma mais prática (ao automatizar métodos getters, construtor, `equals()`, `hashCode()`, `toString()`) e que tem com finalidade única o armazenamento de dados.

É bastante utilizado com o intuito de referenciar classes normais, repetindo apenas os atributos considerados essenciais para o envio de uma solicitação ou uma reposta.

Por exemplo, suponha que haja uma entidade Autor que possua os seguintes atributos: id, nome, dataNascimento, nacionalidade e livros. No entanto, na hora de um usuário fazer um novo registro na tabela Autor, é preciso somente que ele informe três campos: nome, dataNascimento e nacionalidade.

O DTO correspondente a entidade Autor deveria ser assim:

```java
public record AutorDTO(String nome, LocalDate dataNascimento, String nacionalidade) {  
}
```

Este DTO será então utilizado como parâmetro em um método POST para a inserção de um novo registro na tabela Autor:

```java
@RequestMapping(method = RequestMethod.POST)  
public Object salvar(@RequestBody AutorDTO autorDTO){  
  
}
```

## Classe ResponseEntity

É uma classe do Spring Framework que representa toda a resposta HTTP de um método de um controlador. É a partir desta classe que se torna possível definir: código de status, body da resposta, etc.

Por exemplo, este método retornará no body a mensagem "Autor salvo com sucesso!" e o código de status 201 (CREATED) por meio do `HttpStatus.CREATED`:

```java
@PostMapping  
public ResponseEntity salvar(@RequestBody AutorDTO autorDTO){  
    return new ResponseEntity("Autor salvo com sucesso!", HttpStatus.CREATED);  
}
```

# 81. Finalizando o contrato de Salvar um Autor

## Generics da classe `ResponseEntity`

O generics de `ResponseEntity` se refere ao tipo de objeto que será retornado no corpo da mensagem. Caso não deseje retornar nada, coloque `Void` dentro do operador diamante `<>`:

```java
@PostMapping  
public ResponseEntity<Void> salvar(@RequestBody AutorDTO autorDTO){  
    ...
}
```

## Definindo o location do cabeçalho da resposta

Para isso será necessário o seguinte código:

```java
URI localtion = ServletUriComponentsBuilder  
        .fromCurrentRequest()  
        .path("/{id}")  
        .buildAndExpand(autor.getId())  
        .toUri();
```

- **ServletUriComponentsBuilder.fromCurrentRequest()**: retorna um builder, ou seja, um objeto configurável capaz de montar uma URL.
- **path()**: define o seguimento da URL. É possível escolher qualquer seguimento como "salvar/{id}", por exemplo.
- **buildAndExpand()**: atribui um valor à variável de ambiente id (neste caso o id do autor).
- **toUri()**: converte para um objeto URI, que pode ser injetado em um `ResponseEntity`.

É assim que um objeto URI pode ser usado:

```java
ResponseEntity.created(localtion).build()
```

- **created()**: retorna o código de status 201 no cabeçalho.
- **build()**: finaliza a construção de um **ResponseEntity** personalizado, retornando uma instância desta classe.

O método como um todo ficaria desta forma:

```java
@PostMapping  
public ResponseEntity<Void> salvar(@RequestBody AutorDTO autorDTO){  
    Autor autor = autorDTO.mapearParaAutor();  
    autorService.salvar(autor);  
  
    URI localtion = ServletUriComponentsBuilder  
            .fromCurrentRequest()  
            .path("/{id}")  
            .buildAndExpand(autor.getId())  
            .toUri();  
  
    return ResponseEntity.created(localtion).build();  
}
```

O resultado no Postman será este:

![[Pasted image 20250719172230.png]]

# 82. Adicionando Auditoria JPA nas entidades

## Tipo timestamp em SQL

Ele é usado para o armazenamento de data e hora. Exemplo:

```sql
create table autor(  
    id uuid not null primary key,  
    nome varchar(100) not null,  
    data_nascimento date not null,  
    nacionalidade varchar(50) not null,  
    data_cadastro timestamp,  
    data_atualizacao timestamp,  
    id_usuario uuid  
);
```

## Anotações de auditoria

O Spring Data JPA oferece anotações para saber quando um registro na tabela foi criado (`@CreatedDate`) como também saber quando foi realizada a última atualização (`@LastModifiedDate`). Cada uma destas anotações devem ser colocadas em um atributo diferente, sendo estes campos preenchidos automaticamente.

No entanto, para que estas duas anotações funcionem adequadamente, é necessário duas outras anotações:

- `@EntityListeners(AuditingEntityListener.class)`: habilita a funcionalidade de auditoria em uma entidade, fazendo com que os campos com as devidas anotações mostradas anteriormente sejam automaticamente preenchidos e gerenciados.
- `@EnableJpaAuditing`: habilita a funcionalidade de auditoria no seu **projeto**, devendo ser colocada na classe `Application`.

Exemplo de entidade com as devidas anotações:

```java
@Entity  
@Table(name = "autor", schema = "public")  
@Getter  
@Setter  
@ToString(exclude = "livros")  
@EntityListeners(AuditingEntityListener.class)  
public class Autor {  
  
    @Id  
    @GeneratedValue(strategy = GenerationType.UUID)  
    @Column(name = "id")  
    private UUID id;  
  
    @Column(name = "nome", length = 100, nullable = false)  
    private String nome;  
  
    @Column(name = "data_nascimento", nullable = false)  
    private LocalDate dataNascimento;  
  
    @Column(name = "nacionalidade", length = 50, nullable = false)  
    private String nacionalidade;  
  
    @CreatedDate  
    @Column(name = "data_cadastro")  
    private LocalDateTime dataCadastro;  
  
    @LastModifiedDate  
    @Column(name = "data_atualizacao")  
    private LocalDateTime dataAtualizacao;  
  
    @Column(name = "id_usuario")  
    private UUID idUsuario;  
  
    @OneToMany(mappedBy = "autor", cascade = CascadeType.ALL, fetch = FetchType.LAZY)  
    private List<Livro> livros;  
}
```

# 83. Obtendo detalhes do Autor

## Classe Optional

Essa classe é utilizada para encapsular um valor e verificar a sua presença ou não, caso o valor seja nulo, através de métodos como `isPresent()` e `isEmpty()`. Exemplo:

```java
@GetMapping("/{id}")  
public ResponseEntity<AutorDTO> obterDetalhes(@PathVariable("id") String id){  
    Optional<Autor> autorOptional = this.autorService.obterPorId(UUID.fromString(id));  
    if (autorOptional.isPresent()){  
        Autor autor = autorOptional.get();  
        AutorDTO autorDTO = new AutorDTO(  
                autor.getId(),  
                autor.getNome(),  
                autor.getDataNascimento(),  
                autor.getNacionalidade()  
        );        
        return ResponseEntity.ok(autorDTO);  
    }  
    return ResponseEntity.notFound().build();  
}
```

Em suma, se o método encontrar `obterDetalhes` encontrar um registro por meio do parâmetro `id`, isso significa que `autorOptional.isPresent()` será `true` e, portanto, retornará um final um código de status 200 (Ok). Neste caso não é necessário o método `build()`.

Porém, se nenhum registro for encontrado, então retornará um código de status 404 (Not Found).

Há também o método `get()`, que retorna o valor encapsulado.

# 84. Deletando um Autor

## Retornar código de status 204 (no content)

Utilize o método `ResponseEntity.noContent().build()` para retornar um código de status 204. Exemplo:

```java
@DeleteMapping("{id}")  
public ResponseEntity<Void> deletar(@PathVariable("id") String id){  
    Optional<Autor> autorOptional = this.autorService.obterPorId(UUID.fromString(id));  
    if (autorOptional.isEmpty()){  
        return ResponseEntity.notFound().build();  
    }    this.autorService.deletar(autorOptional.get());  
    return ResponseEntity.noContent().build();  
}
```

## O que é um método idempotente?

É aquele método que, ao receber várias vezes em sequência a mesma requisição, irá retornar sempre a mesma resposta.

# 85. Pesquisa de Autores com filtro

## Parâmetro `required` da anotação `@RequestParam`

Informa se o parâmetro de solicitação é opcional (se o valor for `false`) ou obrigatório (se o valor for `true`). Exemplo:

```java
@GetMapping  
public ResponseEntity<List<AutorDTO>> pesquisarAutores(  
        @RequestParam(value = "nome", required = false) String nome,  
        @RequestParam(value = "nacionalidade", required = false) String nacionalidade){  
  
    List<Autor> autores = this.autorService.pesquisa(nome, nacionalidade);  
    List<AutorDTO> autoresDTO = autores  
            .stream()  
            .map(autor -> new AutorDTO(  
                    autor.getId(),  
                    autor.getNome(),  
                    autor.getDataNascimento(),  
                    autor.getNacionalidade()  
            )).collect(Collectors.toList());  
  
    return ResponseEntity.ok(autoresDTO);  
}
```

A especificação do atributo `value` na anotação `@RequestParam` é obrigatório já que são, neste caso, dois parâmetros e também ambos são opcionais.

# 88. Criando um DTO padronizado de respostas de erro

## O que é o enum `HttpStatus`?

Este enum oferece uma coleção de código de status HTTP, que inclui tanto o número referente ao código (201, 404, 500, etc...) como também um mensagem padronizada.

Para obter o número do código é necessário chamar o `HttpStatus`, mais o tipo de erro e, por fim, `.value()`. Por exemplo, se você deseja obter o código de status 409 (referente a conflito), então o script deve ser: `HttpStatus.CONFLICT.value()`.

Agora se deseja obter a mensagem, substitua o `.value()` por `.getReasonPhrase()`, ou seja, `HttpStatus.CONFLICT.getReasonPhrase()`.

# 89. Lógica de validação para regras de negócio

## Query method `existsBy`

Verifica se um registro existe ou não em uma tabela com base em alguma coluna, retornando `true` ou `false`. O método a seguir verifica se um registro existe com determinado nome, data de nascimento e nacionalidade no banco de dados:

```java
boolean existsByNomeAndDataNascimentoAndNacionalidade(  
        String nome,  
        LocalDate dataNascimento,  
        String nacionalidade);
```

## Método `ResponseEntity.status(int status)`

Insere um valor do tipo inteiro que indica o código de status.

# 91. Facilitando a Injeção com RequiredArgsContructor do Lombok

A anotação de classe `@RequiredArgsConstructor` é utilizada para a criação automática de um método construtor para atributos `final`, ou seja, aqueles que exigem a inicialização. Ao colocar esta anotação na classe, é preciso retirar o método construtor caso haja um. Exemplo:

```java
@Service  
@RequiredArgsConstructor  
public class AutorService {  
  
    private final AutorRepository autorRepository;  
    private final AutorValidator autorValidator;  
    private final LivroRepository livroRepository;
	...
}
```