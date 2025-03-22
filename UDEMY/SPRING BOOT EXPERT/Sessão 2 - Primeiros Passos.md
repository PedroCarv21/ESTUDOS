
## Como criar uma aplicação Spring Boot?

Através do site [spring initialzr](https://start.spring.io/), onde serão estabelecidas as definições do seu projeto de acordo com as necessidades. Entre as configurações mais importantes, vale destacar:

- **Project**: é nesta área onde será escolhido o gerenciador de dependências. Gerenciador de dependências é uma ferramenta que gerencia as bibliotecas que devem ser instaladas para que o seu projeto funcione. Foi escolhida a opção Maven pois ela é mais fácil de aprender.
- **Group**: define o domínio do seu projeto. Ele deve ser escrito ao contrário, ou seja, se o seu domínio é example.com então ele deve ser escrito como com.example.
- **Artifact**: define o nome do projeto.
- **ADD DEPENDENCIES**: através deste botão serão adicionadas as dependências (ou bibliotecas) no seu projeto. Foram adicionadas as dependências: Lombok; Spring Boot Dev Tools; Spring Web; Spring Data JPA e H2 Database.
- **EXPLORE**: demonstra a estrutura do projeto antes de ser feito o download.
- **GENERATE**: faz o download do projeto.

![[Pasted image 20250318132843.png]]

## Como instalar plugins?

Clique em configurações (símbolo da engrenagem localizado no canto superior direito) -> clique em **Plugins...** -> digite o plugin desejado no campo de entrada (ex.: lombok) -> clique em **Install**.

![[Pasted image 20250319123432.png]]

## Estrutura do Projeto

### Arquivo pom.xml

É neste arquivo em que se encontram as dependências (bibliotecas) do projeto.
As dependências são definidas pela tag **dependency** e cada dependência estará dentro de uma tag chamada **dependencies** .

Dentro da tag **build** se encontram os puglins necessários para a compilação do seu projeto.

Na tag **properties** é onde estará a tag **java.version** que informa a versão da JDK.

Dentro da tag **parent** existem as configurações do template do projeto. Um exemplo é a versão do projeto; é a partir dela que serão escolhidas as versões de cada dependência compatível com a versão do projeto. É por isso mesmo que as dependências não possuem um versão pré-definida.
### Pasta .idea

São as configurações do projeto dentro da IDE utilizada. Não há o que se mexer nesta pasta.
### Pasta .mvn/wrapper

Contém arquivos que ajudam a definir de maneira mais simples a versão do Maven que o projeto precisa ter.
### Arquivo src/test/java/..../...AplicationTests

Arquivo criado apenas para subir a aplicação na hora da execução.

### Arquivo src/main/java/.../...Aplication

É a classe que contém o método **main** e que, portanto, inicia o projeto.

## Configurações do projeto e da IDE

As configurações do projeto podem ser encontradas clicando em **File** -> **Project Structure**. Defina a versão da sua JDK a partir dos **SDK** e **Language level** na área **Project** e, por fim, clique em **Apply**:

![[Pasted image 20250319155418.png]]

## Execução do programa

Vá até a classe **Application** e clique no botão de iniciar ao lado do método **main**. Se no final da execucação aparecer a mensagem **Started ...Application** então isso significa que a aplicacação está rodando.

![[Pasted image 20250319160154.png]]

## Plugin Maven

Este plugin se encontra no canto direito. Caso não esteja visível, vá até o canto superior esquerdo e clique em **View** -> **Tool Windows** -> **Maven**

![[Pasted image 20250319161318.png]]

Ao clicar no plugin, serão exibidas diversas pastas tais como:

- **Lifecycle**: as operações que podem ser realizadas em cima do projeto. Exemplo:
- **Plugins**: onde estão armazenados os plugins.
- **Dependencies**: onde estão armazenadas as dependências escolhidas durante o acesso do site Spring Initializr.
- **Repositories**: é por meio desta pasta que serão feitas tentativas para a instalação das dependências (primeiro através do arquivo **local** e depois, caso não tenha encontrado, através do arquivo **central**).

### O que fazer quando o projeto apresentar algum erro nas dependências?

Vá até a pasta **Lifecycle** do projeto através do puglin Maven e selecione tanto a operação **clean** como também **install**. Clique no botão de executar:

![[Pasted image 20250319165323.png]]

A operação **clean** irá limpar a pasta **target** do seu projeto (onde ficam os compilados) e o **install** irá realizar o processo de build do seu projeto.

### Como forçar a instalação das dependências?

Clique em **Execute Maven Goal** -> digite dependency:resolve -> clique em **Enter**

![[Pasted image 20250319170517.png]]

### Como alterar a versão do projeto?

Vá até o arquivo pom.xml -> altere a versão na tag **version** -> clique em **Reload All Maven Projects**

![[Pasted image 20250319171325.png]]

## Retornando Hello World com Spring

### Anotação @GetMapping

Antes de tudo, é necessário criar um método na classe **Application** que retorne uma String com a mensagem "Hello World". Após ter criado o método, é preciso dizer que tipo de operação deseja ser feita e por meio de qual rota será acessada esta operação.

Neste caso, é desejado a operação GET, ou seja, retornar alguma informação de alguma fonte. Por isso mesmo será escolhida a anotação **@GetMapping**.

**OBS.: SEMPRE QUE ESTIVER ACESSANDO UM SITE VOCÊ ESTARÁ FAZENDO UMA REQUISIÇÃO GET**

Para definir a rota, deve-se colocar entre parênteses, depois da anotação, uma String que informa o caminho com uma barra no inicio. Por exemplo, se o caminho é **hello-world** então a String passada como argumento para a anotação deve ser **"/hello-word"**. ^634a33

Por fim, coloque a anotação **@RestController** na classe **Application**. Veja na prática:

```
@SpringBootApplication  
@RestController  
public class ProdutosapiApplication {  
  
    @GetMapping("/hello-world")  
    public String helloWorld(){  
       return "Hello World !";  
    }  
  
    public static void main(String[] args) {  
       SpringApplication.run(ProdutosapiApplication.class, args);  
    }  
  
}
```

Execute a aplicação e acesse a URL localhost:8080 mais a rota especificada na anotação **@GetMapping**.

![[Pasted image 20250320114313.png]]

### Por que localhost:8080 ?

É informado **localhost** porque a aplicação está rodando na máquina local; em vez de digitar o IP (http://127.0.0.1:8080/hello-world) pode-se digitar apenas **localhost** que é mais simples. O número 8080 é referente a porta de acesso a aplicação e também a porta padrão do Tomcat: um servidor Java que já vem embutido nas aplicações Spring Boot.


**DICA: para duplicar uma linha, aperte Ctrl+D; para apagar o import das bibliotecas não utilizadas aperte Ctrl+Alt+O**

## Criando um endpoint para o recebimento de produtos

### O que é um endpoint?

É uma URL que, através dela, se torna possível interagir com uma aplicação Spring Boot. Um exemplo é o caso anterior onde foi feito o acesso da aplicação por meio do endpoint "/hello-world":

![[Sessão 2 - Primeiros Passos#^634a33]]

### Criando a classe Produto

O primeiro passo será criar uma classe **dentro do mesmo pacote da classe ...Application (caso contrário sua classe não será reconhecida)** que represente um objeto produto. Para criar uma classe é necessário clicar com o botão direito em um pacote -> New -> Java Class -> informe o nome da classe e pressione Enter.

**OBS.: se precisar criar um novo pacote, digite o nome do pacote separando o nome da classe por meio de ponto (.). Exemplo de um pacote model com uma classe Produto:**

![[Pasted image 20250320124821.png]]

Acesse a classe Produto e defina os atributos (ex.: id (String) , nome (String), descrição (String), preço (Double)) assim como também os getters e setters. Para isso, pressione Alt + Insert -> escolha a opção **Getter and Setter** -> pressione Ctrl enquanto clica em cada um dos atributos -> Ok

![[Pasted image 20250320130542.png]]

### Criando um controller para produtos

Controller é uma classe que processa as requisições HTTP e retorna respostas destas requisições. Para que uma classe seja considerada um Controller, é necessário passar a anotação **@RestController**.

Em seguida, coloque também a anotação **@RequestMapping** na classe ProdutoController, responsável por informar a url deste controller. Exemplo:

```
@RestController  
@RequestMapping("produtos")  
public class ProdutoController {  
      
}
```

### Criando um método Post para a inserção de objetos do tipo Produto


A partir da classe ProdutoController, crie um método **void** que irá 'salvar' as informações de um objeto Produto. No caso de métodos que fazem a operação de inserção (POST), coloque a anotação **@PostMapping** no método:

```
@RestController  
@RequestMapping("produtos")  
public class ProdutoController {  
  
    @PostMapping  
    public void salvar(Produto produto){  
        System.out.println("Produto recebido: " + produto);  
    }  
}
```

**OBS.: é possível informar um endpoint para um método post (ex.: @PostMapping("/produto")). Como não há neste caso uma URL informada, o acesso deste método post se dará apenas informando o endpoint do controller.**

### Enviando uma requisição POST com Postman

Acesse o Postman e siga os seguintes passos:

- Crie uma nova collection (agrupamento de solicitações) clicando em New -> Collection -> Informe o nome da Collection.
- No lado esquerdo, clique nos 3 pontos -> escolha a opção **Add request** -> dê um nome parra a nova **request**

![[Pasted image 20250320150231.png]]


- Coloque agora a opção Post em vez de Get -> informe o endereço da aplicação -> clique em Send. O resultado será o retorno do status 200 ok.

![[Pasted image 20250320150501.png]]

Ao retornar para a IDE, será impresso no terminal a mensagem do println colocada no método salvar.

**OBS.: crie um método toString() na classe Produto para que apareça desta forma.**

![[Pasted image 20250320150820.png]]

Para injetar dados na request e recebê-los, vá até o Postman e clique em **Body** -> selecione a opção **raw** -> selecione o formato **JSON**. Por fim, informe os dados que deseja inserir no formato JSON:

![[Pasted image 20250320153050.png]]

Antes de clicar em Send, vá até o RestController e adicione a anotação **@RequestBody** no parâmetro do método Salvar. Esta anotação indica que os dados recebidos estão na área Body da requisição (o mesmo Body que foi selecionado lá no Postman). 

Caso deseje que os dados aparecem também na resposta do Postman, mude o retorno do método de void para Produto e escreva no final do método **return produto**:

```
@RestController  
@RequestMapping("/produtos")  
public class ProdutoController {  
  
    @PostMapping  
    public Produto salvar(@RequestBody Produto produto){  
        System.out.println("Produto recebido: " + produto);  
        return produto;  
    }  
}
```

A mensagem aparecerá tanto no Postman quanto no terminal da IDE.

## Configuração do banco de dados H2

### O que é um banco de dados H2?

É um banco de dados relacional em memória, o que significa que os dados permanecerão armazenados enquanto a aplicação estiver em execução; é diferente de um banco de dados que armazena no disco rígido (HD) onde as informações são guardadas de forma permanente.

O banco de dados H2 é considerado leve e eficiente para testes.

### Onde são realizadas as configurações do banco de dados?

As configurações são realizadas no arquivo **application** presente na pasta src/main/resources. O arquivo application pode ter tanto a extensão .properties (que vem junto com o projeto) quanto .yml. Para criar um arquivo application.yml, clique com o botão direito na pasta resources -> New -> File -> coloque o nome application.yml -> Enter.

### Sintaxe do application.yml

Esta é a sintaxe presente no arquivo:

```
spring:  
  application:  
    name: Produtos API  
  datasource:  
    url: jdbc:h2:mem:produtos  
    username: sa  
    password: password  
  jpa:  
    database-platform: org.hibernate.dialect.H2Dialect  
  h2:  
    console:  
      enabled: true  
      path: /h2-console
```

A sintaxe do um arquivo.yml é formada por propriedades (spring, jpa, h2, url, etc...) e cada propriedade pode estar integrada a outra. Por exemplo: a propriedade name está integrada em application e que está integrada em spring; a propriedade datasource está integrada em spring, mas não em application.

Estas são as seguintes funções que cada propriedade tem:

- **spring.application.name** -> informa o nome da aplicação.
- **spring.datasource.url** -> define as configurações da conexão com o banco. Primeiro é estabelecido o banco de dados (jdbc:h2), depois o local onde serão armazenados os dados (mem, ou seja, memória RAM) e, por fim, o nome do banco (produtos) .
- **spring.datasource.username** -> define o nome do usuário do banco. Por padrão, o H2 tem como nome de usuário 'sa'.
- **spring.datasource.password** -> define a senha do banco.
- **spring.jpa.database-platform** -> define qual será sintaxe do banco (neste caso será a do H2).
- **spring.console.enabled** -> habilita o acesso do h2 via browser.
- **spring.console.path** -> define o caminho do H2. Por padrão, o caminho é /h2-console.

Depois de definir essas configurações, basta executar a aplicação e acessar a url localhost:8080/h2-console. Será apresentada esse caixa de login. Informe a url, o nome de usuário e a senha corretamente. Em seguida, clique em Connect.

![[Pasted image 20250321151250.png]]
### Criação de tabela no momento da execução

Para que seja criada uma tabela sempre que for iniciada a aplicação, crie na pasta src/main/resources um arquivo com este nome (e não outro): data.sql

A partir deste arquivo, crie uma tabela com os seus atributos e tipos:

```
create table produto(  
    id varchar(255) not null primary key,  
    nome varchar(50) not null,  
    descricao varchar(300),  
    preco numeric(18, 2)  
);
```

Algumas informações sobre esse código:

- **produto**: é o nome da tabela.
- **id**: será uma chave primária (logo, não terá valores repetidos) do tipo string (por isso varchar) com até 255 caracteres. Esse campo não pode ser nulo (por isso o not null).
- **nome**: uma coluna do tipo string que receberá até 50 caracteres e que não pode ser nulo.
- **descricao**: coluna que receberá valores do tipo string de até 300 caracteres.
- **preco**: coluna que receberá valores decimais de até 18 digitos, sendo 2 deles casas decimais.

Rodando o programa será possível ver a tabela produto no banco produtos. Para acessar a estrutura do banco de dados, clique no nome da tabela e depois no botão **Run**.

![[Pasted image 20250321151640.png]]

## Mapeamento JPA das entidades

### Anotação @Entity

Esta anotação serve para mapear, ou seja, relacionar uma classe POJO a uma tabela do banco de dados.

**OBS.: POJO (Plain Old Java Objects) são classes com design simples, possuindo atributos, construtores e métodos getters e setters.** 

### Anotação @Table, @Column e @Id

É necessário que tanto o nome da classe seja idêntico ao nome da tabela quanto o nome dos atributos sejam idênticos ao nome das colunas da tabela. Para isso, deve-se usar a anotação @Table para definir o nome da classe igual ao da tabela e a anotação @Column para definir o nome de cada atributo igual ao nome de cada coluna.

Já a anotação @Id tem como objetivo transformar um determinado atributo em uma chave primária. 

Veja o exemplo da classe Produto com todas essas anotações:

```
@Entity  
@Table(name="produto")  
public class Produto {  
  
    @Id  
    @Column(name="id")  
    private String id;  
    @Column(name="nome")  
    private String nome;  
    @Column(name="descricao")  
    private String descricao;  
    @Column(name="preco")  
    private Double preco;
    ....
```

**OBS.: como os atributos e a classe possuem nomes idênticos ao das colunas e da tabela, o uso de @Table e @Column foi utilizado apenas como exemplo de demonstração.**

