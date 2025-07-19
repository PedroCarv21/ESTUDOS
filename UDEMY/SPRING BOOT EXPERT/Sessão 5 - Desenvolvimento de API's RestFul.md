## 75. Entendendo tudo sobre Rest, HTTP e Requests

### O que é Rest?

Um conjunto de diretrizes sobre como deve ser implementado uma API web. Dentre as diretrizes em destaque estão:
- Utilização dos métodos HTTP (GET, POST, PUT e DELETE) para realizar operações.
- Uso de URL's para identificar recursos específicos.
- Transferência de dados entre cliente e servidor por meio de um formato padrão como JSON ou XML.

### Qual a diferença do Rest para Restful?

Restful é simplesmente uma referência para as API's que implementam as diretrizes Rest.

### Estrutura de uma Request (solitação)

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

## 76. Entendendo a composição de respostas do servidor

### Estrutura do response

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
		- **404 (Not Found)**: quando o cliente tenta um recurso que não existe no servidor.
		- **405 (Method Not Allowed)**: a solicitação enviada não é suportada (por exemplo, quando o cliente faz uma requisição por meio de um get, porém o único método disponível é um post).
		- **409 (Conflict)**: o conceito sobre este código de status já foi esclarecido na sessão 3:
		- ![[Sessão 3 - Arquitetura e Estrutura do Framework#^55f860]]
		- **422 (Unprocessable Entity)**: quando o servidor recebe uma mensagem com erro semântico (como, por exemplo, campos obrigatórios não preenchidos) ou não atende a determinadas condições (como a violação de regras de negócio).
	- **500 (Erro de Server)**: indica uma dificuldade de processamento do servidor.

## 77. Aprenda a modelar contratos de APIs

### O que é um contrato de API?

É a definição das regras de interação entre um cliente e uma API. Estas regras podem incluir: a URL utilizada para acessar a API, o verbo HTTP daquela API, o código status esperado, entre outras.

### Como definir um contrato?

- **Identificação do recurso (a URL utilizada para acessar o recurso)**: é recomendado que as URL's sejam substantivos no plural em vez de verbos que descrevam qual será a operação daquele recurso:
	- ![[Pasted image 20250716125340.png]]
- **Método/verbo HTTP apropriado**:
- **Código de status apropriado**: é preciso seguir esta combinação de código de status de acordo com cada tipo de requisição:
	- ![[Pasted image 20250716125208.png]]
- **Definição do payload (conteúdo da mensagem) do request e response**:
- **Definição dos headers**

## 80. Mapeamento de Requisição e padrão DTO

### Alternativas às anotações padrão para operações HTTP

É possível, além das anotações utilizadas geralmente (como `@GetMapping`, `@PostMapping`, etc ), usar o próprio `RequestMapping` para descrever o tipo operação HTTP que o método irá realizar.

Por exemplo, em vez de `@PostMapping`, é possível utilizar `@RequestMapping(method = RequestMethod.POST)`:

```java
@RequestMapping(method = RequestMethod.POST)  
public Object salvar(@RequestBody Autor autor){  
  
}
```

### Uso de records

É um tipo de classe criada de forma mais prática (ao automatizar métodos getters, construtor, `equals()`, `hashCode()`, `toString()`) e que tem com finalidade única o armazenamento de dados.

É bastante utilizado com o intuito de referenciar classes normais, repetindo apenas os atributos considerados essenciais para o envio de uma solicitação ou uma reposta.

Por exemplo, suponha que haja uma entidade Autor que possua os seguintes atributos: id, nome, dataNascimento, nacionalidade e livros. No entanto, na hora de um usuário fazer um novo registro na tabela Autor, é preciso somente que ele informe três campos: nome, dataNascimento e nacionalidade.

o DTO correspondente a entidade Autor deveria ser assim:

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

### Classe ResponseEntity

É uma classe do Spring Framework que representa toda a resposta HTTP de um método de um controlador. É a partir desta classe que se torna possível definir: código de status, body da resposta, etc.

Por exemplo, este método retornará no body a mensagem "Autor salvo com sucesso!" e o código de status 201 (CREATED) por meio do `HttpStatus.CREATED`:

```java
@PostMapping  
public ResponseEntity salvar(@RequestBody AutorDTO autorDTO){  
    return new ResponseEntity("Autor salvo com sucesso!", HttpStatus.CREATED);  
}
```

## 81. Finalizando o contrato de Salvar um Autor

### Generics da classe `ResponseEntity`

O generics de `ResponseEntity` se refere ao tipo de objeto que será retornado no corpo da mensagem. Caso não deseje retornar nada, coloque `Void` dentro do operador diamante `<>`:

```java
@PostMapping  
public ResponseEntity<Void> salvar(@RequestBody AutorDTO autorDTO){  
    ...
}
```

### Definindo o location do cabeçalho da resposta

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

