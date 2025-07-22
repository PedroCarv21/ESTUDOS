	 
## 41. Introdução ao Spring Data JPA

### Como funciona a JPA

A JPA possui a seguinte estrutura:

![[Pasted image 20250416151022.png]]

1. **Banco de dados**: deve ser escolhido algum banco de dados como MySQL, SQL Driver, entre outros.
2. **Data Source**: uma fonte escolhida para extrair dados (seja um banco de dados, arquivos, API, etc...). Neste caso, é um banco de dados.
3. **EntityManagerFactory**: é uma interface responsável por criar instâncias de Entity Managers.
4. **EntityManager**:  é uma ferramenta do JPA que gerencia as entidades durante as operações CRUD. ^0d3afc

Em suma, haverão entidades representando tabelas do banco e, para que sejam feitas operações CRUD, será necessário um EntityManager criado através de um EntitytManagerFactory.

Por meio da utilização do JPA, o framework Spring Data JPA consegue fornecer outros recursos que simplificam a manipulação de dados. Entre eles está os JPA Repositories (que armazenam dentro de si o EntityManager).


![[Pasted image 20250416160337.png]]

## Criação do projeto

### Escolha de dependências

Serão necessárias apenas as dependências Lombok, Spring Data JPA e PostgreSQL Driver.

### Build da aplicação com o plugin Maven

Como será exigido uma conexão com o banco de dados, é necessário clicar em 🚫 para desativar a operação teste. Assim será possível fazer o build da aplicação.

![[Pasted image 20250428114638.png]]

## O que é o Docker ?

Uma ferramenta capaz de empacotar uma aplicação, junto com todas os outros programas e configurações que ele precisa para funcionar, dentro de uma espécie de caixa (conhecido como **container**). 

Com isso, é possível transportar este container para qualquer computador com qualquer configuração que ele vai funcionar do mesmo jeito.
### O que são imagens Docker e onde baixá-las ?

Uma imagem docker equivale a um conjunto de instruções que o Docker deve seguir para que ele consiga criar e rodar um container. É possível tanto criar as imagens como também utilizar de imagens já prontas. No caso desta segunda opção, acesse o site https://hub.docker.com/
### docker run --name nome_container -p 123:123 nome_da_imagem:versao

Utilize este comando no CMD para criar e rodar um novo container vinculada a uma determinada imagem. 

**OBS.: o comando abaixo NÃO está correto, logo, não execute. Para criar e executar o container corretamente, veja as instruções a partir da aula 46. NO ENTANTO, as informações sobre do que se trata cada parte do comando estão corretas**

Como funciona ?

- `docker run`: cria e inicia um novo container.
- `--name firstcontainer`: informa qual será o nome do container (neste exemplo é firstcontainer).
- `-p 123:123`: faz o mapeamento das portas. O primeiro número é referente a porta do seu PC enquanto que o segundo é referente ao container.
- `imagem:12.5`: indica qual será a imagem usada e a sua versão. Se não tiver ainda imagem instalada, o Docker fará o download automaticamente. **Coloque sempre o nome da imagem como o último parâmetro do comando**.

### O que é PostgreSQL ?

É uma banco de dados relacional (assim como o MySQL ou SQL Server) para o gerenciamento de dados.

Para criar e rodar um container do postgre, é necessário executar o comando `docker run --name librarydb -e POSTGRES_PASSWORD=password -e POSTGRES_USER=postgres -e POSTGRES_DB=library -p 5432:5432 postgres:16.3`

**OBS.: POSTGRES_USER, POSTGRES_PASSWORD e POSTGRES_DB são conhecidas como variáveis de ambiente, definidas após o `-e`**
### docker ps

Utilize este comando no CMD para verificar se algum container está em execução.

## 45. Subindo uma instancia do client do PostgreSQL

### O que é a imagem dpage/pgadmin4 ?

É uma imagem docker que contém a ferramenta web PgAdmin4 responsável pela administração do banco de dados PostgreSQL.

O PgAdmin permite interagir com servidores PostgreSQL, oferecendo recursos como edição de dados, execução de consultas SQL e criação de backups e restaurações.

O comando para criar e rodar o container é este: `docker run --name pgadmin4 -p 15432:80 -e PGADMIN_DEFAULT_EMAIL=pedro8.carvalho@gmail.com -e PGADMIN_DEFAULT_PASSWORD=admin dpage/pgadmin4`
### Como acessar o pgAdmin ?

É necessário rodar tanto o container do postgre quanto do pgAdmin.

Em seguida, acesse no navegador o localhost mais a porta que foi definida para o seu computador acessar o pgAdmin (no exemplo anterior foi definido a porta 15432): localhost:15432

Deve aparecer uma página semelhante a essa:

![[Pasted image 20250507162620.png]]

Coloque o e-mail e a senha que foram definidos durante a criação do container por meio das variáveis de ambiente e clique em login. Você será direcionado para a página inicial do pgAdmin:

![[Pasted image 20250508150803.png]]
## 46. Criando uma network para conectar os containers

### Outros comandos

#### docker stop

Este comando para a execução container ao passar o nome ou o id após o `docker stop`. Exemplo: `docker stop pgadmin4`

#### docker ps -a

Lista os containers que estavam em execução, mas agora estão parados.

#### docker container rm

Ao utilizar este comando mais o nome do container, ele será excluído. Exemplo: `docker container rm librarydb`
### library-network

A library-network é uma rede de conexão responsável por criar uma comunicação entre dois containers. Ela será necessária para a conexão do pgAdmin com o Postgres.

Parar criar uma library-network, utilize o comando `docker network create library-network` no CMD.

**OBS.: library-network é apenas um nome escolhido para a rede, mas poderia ser qualquer outro.**

Para criar o container conectado a esta rede, utilize o comando `--network` mais o nome que foi escolhido para a rede. Insira este comando da seguinte forma na criação do Postgres:

`docker run --name librarydb -e POSTGRES_PASSWORD=password -e POSTGRES_USER=postgres -e POSTGRES_DB=library -p 5432:5432 --network library-network postgres:16.3`

Também acrescente o comando na criação do container do pgAdmin:

`docker run --name pgadmin4 -p 15432:80 -e PGADMIN_DEFAULT_EMAIL=pedro8.carvalho@gmail.com -e PGADMIN_DEFAULT_PASSWORD=admin --network library-network dpage/pgadmin4`

### Conectando o pgAdmin com o Postgres

Depois de iniciar ambos os container e logar na página do pgAdmin, vá até o canto superior esquerdo e clique com o botão direito do mouse em Servers -> Register -> Server. Será aberto a seguinte janela:

![[Pasted image 20250508162718.png]]

No campo de entrada Name, coloque o nome do container do postgres (neste caso é librarydb).

Em seguida, vá até **Connection** e passe os valores nos seguintes campos de entrada:

- **Host name/address**: o nome do container do postgres.
- **Port**: a porta que o container do postgres está acessando.
- **Maintenance database**: o nome do banco de dados definido pela variável de ambiente POSTGRES_DB.
- **Username**: o nome do usuário definido pela variável de ambiente POSTGRES_USER.
- **Password**: a senha do usuário definido pela variável de ambiente POSTGRES_PASSWORD.

Por fim, clique em **Save**.

![[Pasted image 20250508163807.png]]

## 47. Solucionando problemas que podem ocorrer com o ambiente no Docker

Caso a porta escolhida para a conexão com algum dos containers já esteja sendo usada, é possível checar isso através do comando no CMD `netstat -aof | findstr` mais a porta do container. Para listar todas as portas em uso, utilize o comando `netstat -aof`.

## 50. Criando e rodando os scripts no banco de dados

### Criação das tabelas

Clique na seta ao lado de Servers -> clique em library.

![[Pasted image 20250509120312.png]]

Em seguida, vá até o menu e clique em Tools -> Query Tool

![[Pasted image 20250509120520.png]]

Será aberto este editor onde será possível inserir códigos SQL e executá-los por meio da seta no topo do editor. O resultado irá aparecer em **Data Output**.

![[Pasted image 20250509120853.png]]
#### Tabela autor

Esta tabela é formada pelas seguintes colunas:

```sql
create table autor(  
    id uuid not null primary key,  
    nome varchar(100) not null,  
    data_nascimento date not null,  
    nacionalidade varchar(50) not null  
);
```

A coluna id, geralmente definida como int, possui um tipo uuid, cujo conceito está relacionado com aquilo já demonstrado na sessão 2:

![[Sessão 2 - Primeiros Passos#^9a6673]]

#### Tabela livro

Esta tabela é formada pelas seguintes colunas:

```sql
create table livro(  
    id uuid primary key not null,  
    isbn varchar(20) not null,  
    titulo varchar(150) not null,  
    data_publicacao date not null,  
    genero varchar(30) not null,  
    preco numeric(18, 2) not null,  
    id_autor uuid not null references autor(id),  
    constraint chk_genero check (genero in ('FICCAO', 'FANTASIA', 'MISTERIO', 'ROMANCE', 'BIOGRAFIA', 'CIENCIA'))  
);
```

Algumas informações sobre determinadas colunas:

- **genero**: a princípio, esta coluna é do tipo varchar com um limite de 30 caracteres e que não pode ser nulo. No entanto, é estabelecido para esta coluna um restrição através do comando `constraint`, cujo o nome será chk_genero e que irá verificar (por isso o comando `check`) se o valor passado se encontra em (`in`) algum daqueles listados: 'FICCAO', 'FANTASIA', 'MISTERIO', 'ROMANCE', 'BIOGRAFIA', 'CIENCIA'.
- **id_autor**: coluna que referencia (`references`) a coluna id da tabela autor. Logo, se trata de uma chave estrangeira.

Depois de executar os comandos, é possível verificar o local onde elas estão em Databases -> library -> Schemas -> public -> Tables.

![[Pasted image 20250509123724.png]]

## 51. Configurando conexão com o banco de dados através da aplicacao

Estas são as seguintes configurações do banco Postgres presentes no arquivo application.yml

```yml
spring:  
  application:  
    name: libraryapi  
  datasource:  
    username: postgres  
    password: password  
    url: jdbc:postgresql://localhost:5432/library  
    driver-class-name: org.postgresql.Driver
```

Algumas informações sobre determinadas propriedades:

- **url**: neste contexto, a url é formada pelo banco que está sendo utilizado (`jdbc:prostgresql`) mais o caminho do banco que será conectado (`//localhost:5432/library`).
- **driver-class-name**: a partir desta propriedade é informado qual driver JDBC a aplicação Spring Boot deve usar (neste caso, o Postgres). Logo, o valor é `org.postgresql.Driver`.

**OBS.: um driver é basicamente um intérprete que traduz os comandos da sua aplicação para uma linguagem que o banco de dados entende e vice-versa. Cada banco (MySQL, PostgreSQL, Oracle, etc.) tem seu próprio driver, pois cada um tem suas particularidades.**

## 52. Como configurar um DataSource e um Pool de conexões

O código anterior já é o suficiente para criação de um datasource com as demais configurações no banco, pois o Spring utiliza por padrão a classe HikariDataSource. No entanto, é possível também definir essas configurações através das classes HikariConfig e HikariDataSource.

### HikariConfig

É uma classe utilizada para receber as configurações do datasource (username, password, url, etc...):

```java
HikariConfig config = new HikariConfig();  
  
config.setJdbcUrl(url);  
config.setUsername(username);  
config.setPassword(password);  
config.setDriverClassName(driver);
```

Cada método deste receberá um argumento contendo alguma informação específica do datasource. 
### HikariDataSource

A classe HikariDataSource representa um pool de conexões: um mecanismo de gerenciamento de conexões de banco de dados que permite que estas conexões possam ser reutilizáveis.

Em suma, enquanto o HikariConfig representa as configurações do pool, a HikariDataSource representa a criação do pool baseado nas configurações:

```java
@Configuration  
public class DatabaseConfiguration {  
  
    @Value("${spring.datasource.url}")  
    String url;  
    @Value("${spring.datasource.username}")  
    String username;  
    @Value("${spring.datasource.password}")  
    String password;  
    @Value("${spring.datasource.driver-class-name}")  
    String driver;  
  
    @Bean  
    public DataSource hikariDataSource(){  
  
        HikariConfig config = new HikariConfig();  
  
        config.setJdbcUrl(url);  
        config.setUsername(username);  
        config.setPassword(password);  
        config.setDriverClassName(driver);  
  
        return new HikariDataSource(config);  
    }
}
```

### Outras configurações quanto ao pool

Esta configurações por meias de um objeto HikariConfig.

- **setMaximumPoolSize()**: receberá como argumento um valor inteiro que determina o máximo de conexões que um pool pode ter.
- **setMinimumIdle()**: receberá como argumento um valor inteiro que determina o mínimo de conexões que já serão liberadas desde o início.
- **setPoolName()**: define o nome do pool através de uma String como argumento.
- **setMax()**: define em milissegundos o tempo máximo que uma conexão irá ter através de um argumento inteiro.
- **setConnectionTimeOut()**: define o tempo limite para uma conexão através de um valor inteiro como argumento. Caso esse tempo limite seja ultrapassado, será realizado uma tentativa com outra conexão.
- **setConnectionTestQuery()**: verifica previamente se uma conexão com o banco de dados está ativa através de um comando SQL (como por exemplo "SELECT 1") para que depois a conexão possa ser usada.

## 53. Como mapear entidades JPA

### Esquemas

Em um banco de dados, existe algo chamado **esquema**, que tem como causa final a organização dos dados em um banco de dados relacional, é como uma pasta organizadora. No PostgreSQL, o esquema recebe por padrão o nome **public**.

É possível dizer em qual esquema tal entidade se encontra:

```java
@Entity  
@Table(name = "autor", schema = "publico")  
public class Autor {  
  ...
}
```

**OBS.: no caso do esquema ser 'public', não é obrigatório informar o esquema na anotação @Table()**

### Geração automática de ID UUID

Além do enum `GenerationType.IDENTITY`, é possível gerar automaticamente um id do tipo UUID através do enum `GenerationType.UUID`. Exemplo:

```java
@Entity  
@Table(name = "autor", schema = "publico")  
public class Autor {  
  
    @Id  
    @GeneratedValue(strategy = GenerationType.UUID)  
    @Column(name = "id")  
    private UUID id;
}
```

### Atributos length e nullable da anotação @Column

O atributo `length` especifica a quantidade máxima de caracteres que um atributo pode ter (deve ser equivalente ao número passado dentro varchar()). O atributo `nullable` diz se um atributo pode ou não ser nulo. Exemplo:

```java
@Entity  
@Table(name = "autor", schema = "public")
public class Autor {  
  
    @Id  
    @GeneratedValue(strategy = GenerationType.UUID)  
    @Column(name = "id")  
    private UUID id;  
    @Column(name = "nome", length = 100, nullable = false)  
    private String nome;  
    @Column(name = "data_nascimento", nullable = false)  
    private LocalDate dataNascimento;  
    @Column(name = "nacionalidade", length = 58, nullable = false)  
    private String nacionalidade;  
  
  
}
```

### Anotações @Getter e @Setter do Lombok

Estas anotações devem ser colocadas em cima da entidade e serão responsáveis por criar automaticamente os métodos getters e setters durante a compilação. Para ver isso acontecer, utilize o plugin do Maven e realize o build da aplicação como demonstrado anteriormente. Abra o link abaixo: 

![[Sessão 2 - Primeiros Passos#^219b34]]

Em seguida, vá até a pasta **target/classes** e procure pelo arquivo da entidade compilado. Você verá a criação dos métodos getters e setters dentro deste arquivo.

**OBS.: caso ocorra algum erro, verifique se o plugin do Lombok está instalado.**

## 54. Mapeamento da entidade Livro e utilização do Lombok

### Relações entre tabelas

Suponha que exista uma tabela Autor e uma tabela Livro. Um autor pode ter um ou mais livros vinculados a ele e um livro deve estar vinculado a um único autor. Como poderia ser feito esta relação ? 

No caso da entidade Livro, será necessário criar um atributo do tipo Autor e utilizar a anotação `@JoinColumn(name = "")`. Esta anotação indica quem é a chave estrangeira e permite informar o nome correto da chave.

Como vários livros podem pertencer a um único autor (ou seja, muitos para um), então é necessário indicar esta relação entre as entidades através da anotação `@ManyToOne`.

Este atributo deve ficar dentro da entidade Livro:

```java
@ManyToOne  
@JoinColumn(name = "id_autor")  
private Autor autor;
```

**OBS.: se não for utilizada a anotação `@JoinColumn` então o nome gerado automaticamente para a chave estrangeira pode não bater com o nome lá na tabela.**

Já no caso da entidade Autor é necessário utilizar a anotação `@OneToMany`, pois um autor poderá estar vinculado a muitos livros. Esta anotação possui o atributo `mappedBy`, que deverá receber como valor o nome do objeto que representa a chave estrangeira (no exemplo do código anterior, o nome do atributo que representa a chave estrangeira é `autor`). 

Este atributo deve ficar dentro da entidade Autor:

```java
@OneToMany(mappedBy = "autor")  
private List<Livro> livros;
```

### Limitação de casas em um atributo Double

Em um atributo Double, utilize dentro da anotação `@Column` o atributo `precision` para indicar um número de casas totais e o atributo `scale` para indicar a quantidade de casas decimais. No exemplo a seguir, o atributo terá no total 18 casas, sendo que 2 são decimais:

```java
@Column(name = "preco", precision = 18, scale = 2, nullable = false)  
private Double preco;
```

### Criação de atributos com enums

Utilize a anotação `@Enumerated` em um atributo com enum e, dentro da anotação, informe como deverá ser exibido os valores deste atributo lá na tabela: como String (utilize o `EnumType.STRING`) ou de acordo com a posição de cada constante lá no enum (utilize o `EnymType.ORDINAL`).

No exemplo a seguir, o atributo `genero` é do tipo `GeneroLivro` (um enum) e os valores deste atributo serão expostos lá na tabela como strings por causa do `@Enumerated(EnumType.STRING)`.

```java
@Enumerated(EnumType.STRING)  
@Column(name = "genero", length = 30, nullable = false)  
private GeneroLivro genero;
```

### Anotação @Data

Esta anotação carrega dentro de si diversas outras anotações responsáveis pela criação de métodos padrão: `toString()`, `equals()`, `hashCode()`, getters e setters, entre outros. Ela deve ser colocada na entidade.

### Anotação @AllArgsConstructor

Cria um construtor com todos os atributos. Esta anotação é nível de classe.

## 55. Como gerar as tabelas automaticamente com JPA

Em application.yml, utilize a propriedade  `jpa:hibernate:ddl-auto` que define a maneira como a criação e atualização das tabelas será manipulada. Alguns valores que podem ser passados para esta propriedade são:

- **update**: cria uma nova tabela caso não haja uma e também atualiza as configurações na tabela caso tenham sido feitas alterações.
- **none**: nenhuma ação é feita no banco.
- **create-drop**: cria uma nova tabela ao iniciar a aplicação e destrói a tabela quando fecha a aplicação.

Ao rodar a aplicação, é possível verificar as configurações da tabela de duas formas:

### Propriedades

Vá até o pgAdmin e clique com o botão direito na tabela desejada -> clique em **properties...**

![[Pasted image 20250514152309.png]]

Por fim, clique em **Columns** para ver as configurações em cada coluna.

![[Pasted image 20250514152413.png]]

### Script SQL

Selecione com o botão direito a tabela desejada -> **Scripts** -> **CREATE Script**

![[Pasted image 20250514152601.png]]

## 58. Aplicando testes no repository

Os testes tem como finalidade verificar o funcionamento de partes da aplicação separadamente. Para isso, é necessário criar novas classes no mesmo pacote que `ApplicationTests`, presente na pasta `test`. Na imagem a seguir, foi criado uma classe de teste `repository.AutorRepositoryTest` dentro do pacote solicitado:

![[Pasted image 20250519085714.png]]

### Anotações necessárias

#### @SpringBootTest

Esta anotação nível de classe é responsável por criar o contexto da aplicação Spring, o que permitirá a injeção de dependências e demais funcionalidades do framework.

**OBS.: o contexto da aplicação nada mais é do que um local onde os beans são gerenciados.**

```java
@SpringBootTest  
public class AutorRepositoryTest {  

}
```

#### @Test

Esta anotação nível de método indica que um determinado método deve ser executado como um caso de teste.

Exemplo de um método que deve inserir um registro em uma tabela.

```java
@SpringBootTest  
public class AutorRepositoryTest {  
  
    @Autowired  
    private AutorRepository autorRepository;  
  
    @Test  
    public void exemploSalvarAutorTest(){  
        Autor autor = new Autor();  
        autor.setNome("Jose");  
        autor.setNacionalidade("Brasileira");  
        autor.setDataNascimento(LocalDate.now());  
  
        var autorSalvo = this.autorRepository.save(autor);  
        System.out.println("Autor salvo: " + autorSalvo);  
    }
}
```

Para executar um teste específico, clique na seta ao lado do método de teste:

![[Pasted image 20250519100834.png]]
### Testes com entidades relacionadas entre si

Caso deseje ignorar no momento do teste a relação que uma entidade possui com outra entidade, use a anotação `@Transient` no lugar de `@OneToMany`, indicando que um determinado atributo não será considerado durante a criação da tabela de um banco de dados. Exemplo:

```java
@Entity  
@Table(name = "autor", schema = "public")  
@Getter  
@Setter  
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
  
//    @OneToMany(mappedBy = "autor"  
    @Transient  
    private List<Livro> livros;  
}
```

## 59. Operações básicas para entidades simples


Este são outros métodos da interface `JpaRepository`
### Método count()

Retorna a quantidade de registros em uma determinada tabela:

```java
@Test  
public void contarAutoresTest(){  
    System.out.println("Quantidade de autores: " + autorRepository.count());  
}
```

### Método delete()

Recebe a instância de alguma entidade como argumento e então deleta. Exemplo:

```java
@Test  
public void deletarTest(){  
    Autor autor = this.autorRepository.findById(UUID.fromString("24192aed-b2c9-418b-8429-c0a8dd3f969b")).orElse(null);  
    if (autor != null){  
        this.autorRepository.delete(autor);  
        System.out.println("Autor deletado: ");  
        System.out.println(autor);  
    }    else{  
        System.out.println("Autor nao encontrado!");  
    }
}
```

## 60. Trabalhando com relacionamentos - Entidade Livro

### Como criar uma classe teste de forma prática

Vá até uma classe ou interface e coloque o cursor em cima do nome -> pressione `Alt + Enter` -> escolha a opção `Create Test`:

![[Pasted image 20250521084013.png]]

Perceba que o nome da nova classe de teste equivale ao nome da interface/classe mais o sufixo 'Test'. Clique em `Ok` para que a classe de teste seja criada.

![[Pasted image 20250521084250.png]]

### Como inserir um registro em uma tabela com chave estrangeira?

Neste exemplo, a entidade Livro possui uma chave estrangeira com a entidade Autor. É necessário, portanto, que haja pelo menos um registro na tabela Autor para que este seja referenciado em um registro da tabela Livro.

O código abaixo mostra um exemplo a partir de uma classe de teste:

```java
@SpringBootTest  
class LivroRepositoryTest {  
  
    @Autowired  
    AutorRepository autorRepository;  
  
    @Autowired  
    LivroRepository livroRepository;  
  
    @Test  
    void salvarTest(){  
        Autor autor = autorRepository.findById(UUID.fromString("5f607f77-44ec-4ab2-a2b2-c366b6fc176a")).orElse(null);  
  
        Livro livro = new Livro();  
        livro.setIsbn("1234-6588");  
        livro.setPreco(BigDecimal.valueOf(100L));  
        livro.setGenero(GeneroLivro.FICCAO);  
        livro.setTitulo("UFO");  
        livro.setDataPublicacao(LocalDate.of(2025, 10, 3));  
        livro.setAutor(autor);  
  
        livroRepository.save(livro);  
    }}
```

É possível agora ver a relação entre ambos os registros:

![[Pasted image 20250521085718.png]]

## 61. Operações utilizando cascade

### Atributo cascade

É utilizado dentro das anotações como `@OneToMany` e `@ManyToOne` para especificar como as alterações nos registros de uma entidade A afetam também os registros de uma entidade B relacionada a entidade A. É passado como valor para o atributo `cascade` o enum `CascadeType` com as seguintes opções (**estas são apenas algumas**):

- `PERSIST`: persiste (salva) não só a entidade principal como também as entidades relacionadas a ela.
- `MERGE`: atualiza não só a entidade principal como também as entidades relacionadas a ela.
- `REMOVE`: remove não só a entidade principal como também as entidades relacionadas a ela (mas isso somente se houver **um único** registro da tabela relacionada com um registro da tabela principal; se houver mais de um então não funcionará).
- `ALL`: realiza todas as operações anteriores além de outras não mencionadas.

Exemplo do uso deste atributo na entidade Livro:

```java
@ManyToOne(cascade = CascadeType.ALL)  
@JoinColumn(name = "id_autor")  
private Autor autor;
```

Agora, é possível inserir um registro na tabela Livro e ao mesmo tempo inserir um registro na tabela Autor que esteja associado. Exemplo:

```java
@Test  
void salvarCascadeTest(){  
  
    Livro livro = new Livro();  
    livro.setIsbn("67676-57667");  
    livro.setPreco(BigDecimal.valueOf(80L));  
    livro.setGenero(GeneroLivro.BIOGRAFIA);  
    livro.setTitulo("Minha Vida");  
    livro.setDataPublicacao(LocalDate.of(2022, 5, 1));  
  
    Autor autor = new Autor();  
    autor.setNome("Pedro");  
    autor.setNacionalidade("brasileiro");  
    autor.setDataNascimento(LocalDate.parse("2000-01-03"));  
  
    livro.setAutor(autor);  
  
    livroRepository.save(livro);  
}
```

**OBS.: o recomendado é NÃO usar cascade, mas sim realizar manualmente as operações CRUD por uma questão de segurança.**

## 63. Entendendo sobre Lazy e Eager initializations

Quando é realizado uma consulta em uma tabela vinculada a outra (ex.: tabela Livro vinculada a tabela Autor) será gerado um código SQL que fará um `join` entre as tabelas, independente se você precisar dos dados de uma só tabela ou de ambas.

Por exemplo, o código a seguir busca os dados apenas da tabela Livro, mas, de qualquer forma, é feito um `join` nas tabelas Livro e Autor:

```java
@Test  
void buscarLivroEAutor(){  
    Livro livroEncontrado = livroRepository.findById(UUID.fromString("6f90046b-64e7-4138-a434-a85bcb1414ad")).orElse(null);  
    System.out.println("ID do livro: " + livroEncontrado.getId());  
    System.out.println("Genero do livro: " + livroEncontrado.getGenero());  
}
```

Ao executar este teste, o código SQL gerado será este:

```sql
select l1_0.id,a1_0.id, a1_0.data_nascimento, a1_0.nacionalidade, a1_0.nome,l1_0.data_publicacao,l1_0.genero,l1_0.isbn,l1_0.preco,l1_0.titulo 
from livro l1_0 
left join public.autor a1_0 on a1_0.id=l1_0.id_autor 
where l1_0.id=?

```

A razão disso acontecer ocorre por causa do atributo `fetch = FetchType.EAGER` **ser padrão** na anotação `@ManyToOne()`. Caso deseje que o código SQL gerado faça uma busca apenas da tabela solicitada então defina como `@ManyToOne(fetch = FetchType.LAZY)`.

Ao executar o mesmo teste Java, será gerado um código SQL diferente, que consulta apenas a tabela livro:

```sql
select l1_0.id, l1_0.id_autor, l1_0.data_publicacao, l1_0.genero, l1_0.isbn, l1_0.preco, l1_0.titulo 
from livro l1_0
where l1_0.id=?
```

**OBS.: há casos onde uma tabela possui relacionamento diversas outras tabelas. Portanto, às vezes pode ser importante 'filtrar' quais tabelas serão consultadas de modo que a consulta não fique tão pesada.**

Agora, se tentar acessar alguma informação da tabela Autor (ex.: `System.out.println("Autor:" + livroEncontrado.getAutor().getNome());`) então será lançada a exceção `LazyInitializationException`: ocorre justamente quando se tenta acessar um objeto carregado de forma preguiçosa (que só é carregado quando necessário) em um ponto do código onde a sessão do Hibernate já foi fechada ou não está mais ativo.

**OBS.: enquanto uma entidade `@ManyToOne`  vem com `FetchType.EAGER` por padrão, uma entidade `@OneToMany` vem com `FetchType.LAZY` por padrão.**
### Consultado tabelas relacionadas de forma separada

Mesmo com `@ManyToOne(fetch = FetchType.LAZY)` é possível ainda consultar dados em tabelas relacionadas através da anotação `@Transactional` do caminho `org.springframework.transaction.annotation.Transactional`:

```java
@Test  
@Transactional  
void buscarLivroEAutor(){  
    Livro livroEncontrado = livroRepository.findById(UUID.fromString("6f90046b-64e7-4138-a434-a85bcb1414ad")).orElse(null);  
    System.out.println("ID do livro: " + livroEncontrado.getId());  
    System.out.println("Genero do livro: " + livroEncontrado.getGenero());  
    System.out.println("Autor:" + livroEncontrado.getAutor().getNome());  
}
```

Com esta anotação, é possível consultar tanto a tabela Livro quanto a tabela relacionada Autor, porém de forma separada:

```sql
select l1_0.id, l1_0.id_autor, l1_0.data_publicacao, l1_0.genero, l1_0.isbn, l1_0.preco, l1_0.titulo
from livro l1_0
where l1_0.id=?
```

```sql
select a1_0.id, a1_0.data_nascimento, a1_0.nacionalidade, a1_0.nome
from public.autor a1_0
where a1_0.id=?
```

Veja que agora as consultas foram realizadas de modo separado: a primeira da tabela Livro e a segunda da tabela Autor.

## 64. Trabalhando com relacionamento OneToMany

Serão demonstrados dois exemplos de inserção de registros com relacionamentos: o primeiro sem o atributo `cascade` e o segundo com o atributo `cascade`.
### Sem o atributo `cascade`

Neste exemplo, será inserido um registro na tabela Autor (`@OneToMany`) e dois registros na tabela Livro (`@ManyToOne`). Para isso, será necessário passar o objeto Autor como argumento para os dois objetos Livro e depois os dois objetos Livro devem ser inseridos em uma lista, sendo esta passada como argumento para o objeto Autor.

Por fim, será realizada uma operação de persistência primeiro com o objeto Autor (através do método `save` ) e depois com os objetos Livro (através do método `saveAll` ).

```java
@Test  
void salvarAutorComLivrosTest(){  
    Autor autor = new Autor();  
    autor.setNome("Antonio");  
    autor.setNacionalidade("Americana");  
    autor.setDataNascimento(LocalDate.of(1978, 8, 5));  
  
    Livro livro = new Livro();  
    livro.setIsbn("20292820-13213131");  
    livro.setPreco(BigDecimal.valueOf(204L));  
    livro.setGenero(GeneroLivro.MISTERIO);  
    livro.setTitulo("O roubo na casa assombrada");  
    livro.setDataPublicacao(LocalDate.of(1999, 1, 2));  
    livro.setAutor(autor);  
  
    Livro livro2 = new Livro();  
    livro2.setIsbn("5656544-4564654");  
    livro2.setPreco(BigDecimal.valueOf(658L));  
    livro2.setGenero(GeneroLivro.FICCAO);  
    livro2.setTitulo("Nova Espécie");  
    livro2.setDataPublicacao(LocalDate.of(1999, 1, 2));  
    livro2.setAutor(autor);  
  
    autor.setLivros(new ArrayList<>());  
    autor.getLivros().add(livro);  
    autor.getLivros().add(livro2);  
  
  
    autorRepository.save(autor);  
    livroRepository.saveAll(autor.getLivros());  
}
```

## 65. Estratégia de fetching para relacionamentos OneToMany

```java
//@OneToMany e FetchType.LAZY
//QUERY METHOD
//@ToString(exclude = "")
```

### Considerações sobre `@OneToMany`

Da mesma forma que `FetchType.EAGER` é padrão em `@ManyToOne`, o enum `FetchType.LAZY` é padrão em `@OneToMany`.

### Impressão dos registros de entidades relacionadas

Ao capturar um registro por meio de algum método `findBy` e armazená-lo em uma variável, é provável que se deseje imprimir tal objeto (se ele possuir um método `toString`). Porém, em casos de entidades relacionadas, isso só funcionará se for ignorado os atributos responsáveis por referenciar a outra entidade (seja no atributo com `@OneToMany` ou com `@ManyToOne`).

É necessário então informar qual atributo deve ser excluído de `toString`  da seguinte forma:

```java
@ToString(exclude = "nome_do_atributo")
```

Só assim será possível fazer a impressão dos registros corretamente:

```java
@Test
@Transactional
void listarLivrosAutor(){  
	UUID id = UUID.fromString("be6fd499-ed35-45d1-952e-f442040867aa");  
	Autor autor = autorRepository.findById(id).orElse(null);  
	System.out.println(autor);  
	autor.getLivros().forEach(System.out::println);  
}
```

### Query Methods

No exemplo anterior foi utilizado `@Transactional` para que fosse possível consultar também os registros da tabela Livro. Porém, outra forma de fazer isso sem esta anotação é através de **query methods**: métodos com a finalidade de consultar com base em algum critério específico. Este métodos podem ser personalizados como no seguinte exemplo:

```java
public interface LivroRepository extends JpaRepository<Livro, UUID> {  
  
    List<Livro> findByAutor(Autor autor);  
  
}
```

Acontece que a entidade Livro possui uma coluna chamada 'autor', logo, é obrigatório, caso deseje consultar os registros da tabela Livro com base na coluna 'autor', criar um método chamado `findByAutor` (obedecendo as regras camelCase).

Este método equivale ao seguinte código sql:

```sql
select * from livro where id_autor = ?
```

Agora é possível fazer uma consulta da seguinte forma:

```java
@Test  
void listarLivrosAutor(){  
	UUID id = UUID.fromString("be6fd499-ed35-45d1-952e-f442040867aa");  
	Autor autor = autorRepository.findById(id).orElse(null);  
	System.out.println(autor);  
	List<Livro> autorList = livroRepository.findByAutor(autor);  
	autorList.forEach(System.out::println);  
}
```

## 66. Implementação de pesquisas com Query Methods

### Outras formas de métodos personalizados

#### And

Utilize este palavra entre o nome dos atributos se desejar consultar um registro por meio de dois ou mais atributos. Por exemplo, se deseja consultar um registro por meio do atributo `titulo` e `genero` então o nome do método deve ser `findByTituloAndGenero`:

```java
List<Livro> findByTituloAndGenero(String titulo, GeneroLivro generoLivro);
```
#### Or

Utilize este palavra entre o nome dos atributos se deseja consultar por meio de um atributo ou outro. Por exemplo, se deseja consultar um registro por meio do atributo `nome` ou `dataNascimento` então o nome do método deve ser `findByNomeOrDataNascimento`:

```java
List<Autor> findByNomeOrDataNascimento(String nome, LocalDate localDate);
```

### Formatação do código SQL 

Utilize o comando `spring:jpa:properties:hibernate.format-sql:true` para formatar (organizar) o código SQL que aparece impresso no momento da execução do código. Veja um exemplo:

![[Pasted image 20250528121319.png]]

## 67. Variações de métodos de busca declarativos

Para mais dicas sobre query methods, acesso o site https://docs.spring.io/spring-data/jpa/reference/jpa/query-methods.html onde será encontrada uma lista de opções de consultas.


## 68. Trabalhando com consultas JPQL e @Query

### O que é JPQL

JPQL é uma linguagem de consulta específica da JPA, utilizada para fazer consultas em entidades armazenadas em um banco de dados. Ou seja, a pesquisa não será realizada com base no nome das colunas e da tabela, mas com base no nome de uma entidade e seus atributos.

Vale lembrar que a JPQL possui uma sintaxe própria e que deve ser colocada em uma anotação `@Query` e esta anotação ficará em cima do método de algum repositório. Exemplo:

```java
@Query("select l from Livro as l order by preco")  
List<Livro> listarTodosOrdenadosPorPreco();
```

Perceba que `Livro` e `preco` fazem referência ao nome da entidade e do atributo (não necessariamente ao nome da tabela e da coluna).

**OBS.: caso deseje utilizar SQL normal, e não JPQL, adicione na anotação `@Query` o atributo `nativeQuery = true`. É preciso também que sejam retornados todos os valores da classe cujo o método com `@Query` irá retornar. Exemplo: se há um método com `@Query` que irá retornar um objeto `Autor` então é necessário selecionar ( `select`) todos os atributos referentes a tabela `autores`.**
## 69. Utilizando Named e Positional Parameters

Há duas opções de como utilizar parâmetros em um método com anotação `@Query`:

### Named Parameters

Será fornecido uma espécie de 'apelido' para o parâmetro da consulta que ficará após os dois pontos (:) e esse parâmetro será referenciado dentro da assinatura do método através da anotação `@Param`.

No seguinte exemplo, o apelido do parâmetro é `paramentoNacionalidade` e deve ser colocado após os dois pontos dentro da consulta. Para que este apelido esteja relacionado a um parâmetro do método é necessário utilizar a anotação `@Param` e passar o apelido como argumento:

```java
@Query("""  
        select a from Autor a  
        where a.nacionalidade = :paramentoNacionalidade  
        """)  
List<Autor> findByNacionalidade(@Param("paramentoNacionalidade") String nacionalidade);
```

### Positional Parameters

Neste caso, o parâmetro do método terá como referência não mais um apelido, mas a posição dos parâmetros. Exemplo:

```java
@Query("""  
        select a from Autor a   
        where a.nacionalidade = ?1
        order by ?2""")  
List<Autor> findByNacionalidade(String nacionalidade, String nomePropriedade);
```

Veja que o parâmetro `nacionalidade` é referenciado por `?1` (logo ele deve ser o primeiro parâmetro) e `nomePropriedade` por `?2` (este deve ser o segundo parâmetro). O resultado seria o mesmo se o código fosse escrito assim:

```java
@Query("""  
        select a from Autor a
        where a.nacionalidade = ?2
        order by ?1""")  
List<Autor> findByNacionalidade(String nomePropriedade, String nacionalidade);
```

## 70. Operacoes delete e update utilizando Queries

Para realizar essas operações com a anotação `@Query` são necessárias duas outras anotações:

- `@Modifying`: serve para indicar que um método de repositório não é uma consulta de leitura (SELECT), mas sim uma consulta de modificação (INSERT, UPDATE, DELETE, etc...).
- `@Transactional`.

Exemplo da criação de métodos abstratos em um repositório:

```java
@Modifying  
@Transactional  
@Query("delete from Livro where genero = :generoLivro")  
void deleteByGenero(@Param("generoLivro") GeneroLivro generoLivro);  
  
@Modifying  
@Transactional  
@Query("update Livro set dataPublicacao = ?1 where titulo = ?2")  
void updateDataPublicao(LocalDate dataPublicacao, String titulo);
```

Implementação dos métodos em uma classe de teste:

```java
@Test  
void deletarPeloGeneroTest(){  
    livroRepository.deleteByGenero(GeneroLivro.CIENCIA);  
}  
  
@Test  
void atualizarDataPorTituloTest(){  
    livroRepository.updateDataPublicao(LocalDate.parse("2022-03-01"), "Nova Espécie");  
}
```

## 71. Conhecendo os estados das entidades

### O que é uma transação?

É uma soma de operações no banco de dados que devem ser executadas por inteiro (e não apenas parte delas). Caso contrário, as operações já realizadas serão desfeitas como garantia de preservação dos dados.

### O que é um objeto transiente?

Quando um objeto, instância de uma entidade, ainda não possui uma representação no banco de dados e nem é reconhecido pelo `EntityManager`. Lembrando do que se trata:

![[Sessão 4 - Acesso a Dados com Spring Data JPA#^0d3afc]]

### O que é um objeto managed?

Quando a entidade passa a ser associada ao `EntityManager`. Caso a entidade venha a ser removida então ela ficará no estado **removed**.

## 72. Entendendo como funcionam as transações do Spring

### Mais informações sobre transações

A linguagem SQL disponibiliza estes comandos para a realização de transações:

- `begin`: inicia uma nova transação.
- `commit`: confirma as alterações realizadas durante a abertura da transação e, por fim, fecha a transação.
- `rollback`: desfaz as alterações realizadas durante a abertura da transação e, por fim, fecha a transação.

Exemplo:

```sql
begin;

update livro set preco = 355.20 where id = 'e31a85be-d0b7-44a7-9272-b69abc3f8773';
```

Este comando diz que uma transação foi iniciada (por causa do `begin`) e solicita a atualização do valor da coluna `preco` onde houver um registro com o `id` informado.

Agora, para que as atualizações sejam mantidas ou desfeitas será necessário o uso de `commit` ou `rollback`.

```sql
commit;

rollback;
```

### Como funcionaria uma transação em aplicação Spring Boot ?

Exemplo:

```java
@Transactional  
public void executar(){  
    Autor autor = new Autor();  
    autor.setNome("Manuel");  
    autor.setNacionalidade("mexicano");  
    autor.setDataNascimento(LocalDate.of(1978, 8, 5));  
  
    autorRepository.saveAndFlush(autor);  
  
    Livro livro = new Livro();  
    livro.setIsbn("20292820-13213131");  
    livro.setPreco(BigDecimal.valueOf(204L));  
    livro.setGenero(GeneroLivro.CIENCIA);  
    livro.setTitulo("Livro X");  
    livro.setDataPublicacao(LocalDate.of(1999, 1, 2));  
    livro.setAutor(autor);  
  
    livroRepository.saveAndFlush(livro);  
  
    if (livro.getTitulo().equals("Livro X")){  
        throw new RuntimeException("Este livro nao e aceito");  
    }
}
```

**OBS.: todos os métodos de transação devem ser públicos.**

```java
@SpringBootTest  
public class TransacoesTest {  
  
    @Autowired  
    TransacaoService transacaoService;  
  
    @Test  
    void transacaoSimples(){  
        transacaoService.executar();  
    }
}
```

Será realizada a tentativa de inserir um objeto da entidade Autor e outro objeto da entidade Livro. No entanto, se o título do objeto Livro for igual a 'Livro X', ocorrerá uma exceção e isso representará um `rollback`. Se não ocorresse a exceção devido ao nome do livro, seria realizado um `commit`.

### Método `saveAndFlush`

No exemplo anterior, se fosse utilizado `saveAndFlush()` em vez de `save()`, o resultado seria a inserção dos dados no banco e, posteriormente, quando fosse detectado a exceção, a realização de um `rollback`.

No caso do método `save()`, o processo de salvar os dados ocorre apenas no final da transação.

Resultado com método `save()`:

![[Pasted image 20250606133405.png]]

Resultado com método `saveAndFlush`:

![[Pasted image 20250606133633.png]]

## 73. Aplicando os conceitos de transações e estados na prática

### Atualização em uma transação

Neste caso, não é necessário utilizar o método `save()` do `JpaRepository` para uma operação de atualização dentro de uma transação. Exemplo:

```java
@Transactional  
public void atualizacaoSemAtualizar(){  
    Livro livro = livroRepository.findById(UUID.fromString("519979fc-60cb-43bc-a3a5-f49b389d48b5")).orElse(null);  
    livro.setDataPublicacao(LocalDate.of(1784, 9, 3));  
}
```

Quando esse método for chamado, ele irá atualizar sem o auxílio do método `save()`. Isso acontece porque o objeto que foi resgatado pelo Id já se encontra no estado managed.