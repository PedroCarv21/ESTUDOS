
## Divisão do projeto Spring Boot

O projeto é divido em módulos ou **starters**, sendo estes adicionados conforme as necessidades de cada desenvolvedor. Os starters são dependências que agruparam outras dependências para simplificar o desenvolvimento de aplicativos.

Entre os principais starters estão: 

- Starter Web: usado para o desenvolvimento de aplicações Web e para a criação de APIs Rest.
- Starter Data JPA: usado para a implementação da JPA através do Hibernate em uma aplicação. Sem este starter não é possível usar as principais anotações mostradas anteriormente.
- Starter Secutiry: é adicionado a aplicação para configurações de segurança.
- Starter Test: este starter já vem embutido na aplicação Spring Boot para testes da aplicação.

### Relação entre Spring Boot e Spring

O Spring Boot é uma extensão do framework Spring, feito com o objetivo de simplificar a criação de aplicações complexas através de, por exemplo, a Inversão de Controle (IOC): um modo de delegar tarefas (como, por exemplo, o fechamento da conexão com o banco) para o Spring Boot, realizando tal tarefa de forma automatizada.

### Configurations

Acontece que vários starters tem as classes de configuração, responsáveis por ler as configurações definidas em arquivos como application.yml ou application.properties e aplicar estas configurações.

## Spring Container

É o mecanismo do Spring Framework que cuida do ciclo de vida dos beans, ou seja, cria, inicializa e gerencia os objetos definidos como beans.
### Beans

Os **beans** são instancias de componentes gerenciados pelo Spring Container; eles podem pertencer a qualquer classe com a anotação @Component, @Controller, @Service, @Repository ou @Bean.
### Components

São classes com a anotação @Component, sendo esta anotação uma classificação genérica para qualquer classe gerenciada pelo Spring. Os tipos de componentes específicos são:

- **Services**: camada que trata da lógica de negócio da aplicação.
- **Repositories**: camada que possui interfaces com métodos para a manipulação de dados no banco (seja SQL ou NoSQL). Veja também sobre a interface JpaRepository na sessão 2:
		![[Sessão 2 - Primeiros Passos#^bdeec6]]
- **Controllers**: a definição de controllers foi dada também na sessão 2:
		![[Sessão 2 - Primeiros Passos#^fc947b]]

![[Pasted image 20250331144133.png]]

**OBS.: segundo o instrutor, o Container Spring pode ser entendido como uma alusão ao Application Context (contexto do aplicativo), que é composto pelo: Components, Configurations e os beans.**
## Características da classe Application

### Anotação @SpringBootApplication

É responsável por fazer com que a aplicação seja iniciada. Por trás desta anotação existem diversas outras anotações, tais como:

- **@SpringBootConfiguration:** responsável pela configuração do Spring Boot. 
- **@EnableAutoConfiguration**: habilita a configuração automática de vários componentes.
- **@ComponentScan:** responsável pelo **escaneamento**, ou seja, o registro dos componentes, que se encontram no mesmo pacote da classe Application, no contexto do aplicativo.

### Como mudar o nome da classe Application

Selecione o nome da classe -> pressione as teclas de atalho Shift + F6. 

Será exibido uma janela como esta:

![[Pasted image 20250331145221.png]]

Caso deseje mudar o nome da classe ApplicationTests, selecione a caixa e clique em Ok.

### Classe SpringApplicationBuilder

É uma classe utilizada para a configurar e iniciar uma aplicação Spring de modo mais flexível do que o método **SpringApplication.run()**, sendo, portanto, usada dentro da classe Application.

#### Instanciação da classe

No momento da instanciação, deve ser passado como argumento a classe Application:

```java
SpringApplicationBuilder builder = new SpringApplicationBuilder(Application.class);
```
#### Inicialização da aplicação

Utilize o método **run()** do objeto SpringApplicationBuilder, passando como argumento o parâmetro args (já presente no método main()):

```java
SpringApplicationBuilder builder = new SpringApplicationBuilder(Application.class);  
builder.run(args);
```
#### Ocultação do banner

Método **bannerMode()** para a configuração do banner. Informe Banner.Mode.OFF para que o banner seja ocultado.

```java
SpringApplicationBuilder builder = new SpringApplicationBuilder(Application.class);  
builder.bannerMode(Banner.Mode.OFF);  
builder.run(args);
```

## Problemas com o código

Em alguns casos onde há um erro na sintaxe ou na lógica do código, aparece o simbólo de uma lampada vermelha com um ponto de exclamação vermelho:

![[Pasted image 20250331163615.png]]

Nestas situações, clique na linha onde está ocorrendo o erro e use o atalho Alt + Enter. A IDE oferecerá opções para a correção do erro.

No exemplo acima, a classe HondaHRV é filha da classe Carro, que possui um método construtor personalizado somente (não possui o construtor padrão). Logo, é necessário que esta classe HondaHRV também possua um método construtor com a palavra reservada super() para que a instanciação de HondaHRV seja feita corretamente:

![[Pasted image 20250331163919.png]]

## Classe Configuration

É uma classe com a anotação **@Configuration** que registra os beans por meio de métodos com a anotação **@Bean**. Os beans nada mais são do que a instanciação de componentes que são criadas e gerenciadas pelo Spring Container.

**OBS.: sem a anotação @Configuration, o Spring não terá como escanear a classe de configuração e tampouco os beans.**

Veja este exemplo onde há uma classe de configuração com um método com a anotação @Bean para a criação de um objeto Motor:

```java
@Configuration  
public class MontadoraConfiguration {  
  
    @Bean  
    public Motor motor(){  
        var motor = new Motor();  
        motor.setCavalos(120);  
        motor.setCilindros(4);  
        motor.setModelo("XPTO-0");  
        motor.setLitragem(2.0);  
        motor.setTipo(TipoMotor.ASPIRADO);  
        return motor;  
    }  
}
```

^842577

**OBS.: A palavra-chave `var` em Java é um recurso que permite declarar variáveis locais sem precisar especificar um tipo de dado.**

A partir do momento em que a aplicação for executada, o Spring irá instanciar o bean através do método `motor` e registrá-lo no Spring Container para que possa ser utilizado.

### Injeção de dependências (DI)

O conceito de dependência aqui não diz respeito as bibliotecas externas presentes no arquivo pom.xml, mas sim um objeto ou componente que uma classe precisa para funcionar corretamente. Caso a dependência seja criada (instanciada) dentro de uma classe então isso resultará em um forte acoplamento (o que não é bom, pois dificulta a manutenção do código).

No caso do Spring Boot, a injeção de dependências será feito em uma classe por meio de uma configurations (classe com anotação @Configuration) que forneça os beans para serem injetados. Essa injeção de dependências é feita através do anotação **@Autowired** que será colocada acima de um atributo, método ou construtor, indicando aonde deve ser feita a injeção de dependência.

A injeção de dependências visa então diminuir o acoplamento ao separar as classes da criação de dependências.

```java
@RestController  
public class TesteFabricaController {  
  
    @Autowired  
    private Motor motor;  
  
    @PostMapping  
    public CarroStatus ligarCarro(@RequestBody Chave chave){  
        var carro = new HondaHRV(motor);  
        return carro.darIgnicao(chave);  
    }  
}
```

O exemplo acima mostra a injeção de dependência em um atributo chamado 'motor' com a anotação @Autowired, cuja a dependência se encontra na classe de configuração MontadoraConfiguration: 
	![[Sessão 3 - Arquitetura e Estrutura do Framework#^842577]]

## Como especificar o bean que deseja utilizar ?

Em casos onde há mais um de bean do mesmo tipo, é necessário especificar qual deles será utilizado. Esse problema é resolvido:

- Atribuindo um nome para cada bean.
- Utilizando a anotação **@Qualifier** no atributo ou método que irá receber o bean e especificando o nome do bean dentro desta anotação.

Exemplo de beans do mesmo tipo com um nome próprio:

```java
@Configuration  
public class MontadoraConfiguration {  
  
    @Bean(name = "motorAspirado")  
    public Motor motorAspirado(){  
        var motor = new Motor();  
        motor.setCavalos(120);  
        motor.setCilindros(4);  
        motor.setModelo("XPTO-0");  
        motor.setLitragem(2.0);  
        motor.setTipo(TipoMotor.ASPIRADO);  
        return motor;  
    }  
  
    @Bean(name = "motorEletrico")  
    public Motor motorEletrico(){  
        var motor = new Motor();  
        motor.setCavalos(110);  
        motor.setCilindros(3);  
        motor.setModelo("th-40");  
        motor.setLitragem(1.4);  
        motor.setTipo(TipoMotor.ELETRICO);  
        return motor;  
    }  
  
    @Bean(name = "motorTurbo")  
    public Motor motorTurbo(){  
        var motor = new Motor();  
        motor.setCavalos(180);  
        motor.setCilindros(4);  
        motor.setModelo("XPTO-01");  
        motor.setLitragem(1.5);  
        motor.setTipo(TipoMotor.TURBO);  
        return motor;  
    }  
}
```

Exemplo do uso do bean `motorEletrico` no atributo `motor`:

```java
@RestController  
@RequestMapping("/testefabrica")  
public class TesteFabricaController {  
  
    @Autowired  
    @Qualifier("motorEletrico")  
    private Motor motor;  
  
    @PostMapping("/ligarcarro")  
    public CarroStatus ligarCarro(@RequestBody Chave chave){  
        var carro = new HondaHRV(motor);  
        return carro.darIgnicao(chave);  
    }  
}
```

## Beans Primary

São beans escolhidas por padrão (graças a anotação **@Priamary**) caso não haja uma especificação de qual bean será usada (por meio da anotação @Qualifier). O exemplo a seguir mostra que a bean motorTurbo será definida como padrão entre os 3 beans.

```java
@Configuration  
public class MontadoraConfiguration {  
  
    @Bean(name = "motorAspirado")  
    public Motor motorAspirado(){  
        var motor = new Motor();  
        motor.setCavalos(120);  
        motor.setCilindros(4);  
        motor.setModelo("XPTO-0");  
        motor.setLitragem(2.0);  
        motor.setTipo(TipoMotor.ASPIRADO);  
        return motor;  
    }  
  
    @Bean(name = "motorEletrico")  
    public Motor motorEletrico(){  
        var motor = new Motor();  
        motor.setCavalos(110);  
        motor.setCilindros(3);  
        motor.setModelo("th-40");  
        motor.setLitragem(1.4);  
        motor.setTipo(TipoMotor.ELETRICO);  
        return motor;  
    }  
  
    @Bean(name = "motorTurbo")  
    public Motor motorTurbo(){  
        var motor = new Motor();  
        motor.setCavalos(180);  
        motor.setCilindros(4);  
        motor.setModelo("XPTO-01");  
        motor.setLitragem(1.5);  
        motor.setTipo(TipoMotor.TURBO);  
        return motor;  
    }  
}
```

### Como criar anotações

Clique com o botão direito em um pacote -> New -> Java Class -> informe o nome da anotação e escolha a opção Annotation:

![[Pasted image 20250404101943.png]]

Esta será a estrutura padrão de uma anotação:

```java
public @interface Aspirado {  

}
```

## Anotações padrão

É necessário agora utilizar anotações padrão, ou seja, anotações presentes dentro da estrutura de todas as anotações. Estas são:

- **@Retention**: determina se uma anotação estará disponível no momento da compilação e/ou execuação. Estas são as 3 opções de enums a serem passadas como argumentos:
	- **RetentionType.SOURCE**: a anotação será ignorada tanto pelo compilador quanto no tempo de execução.
	- **RetentionType.CLASS**: a anotação estará disponível apenas no momento de compilação, não de execução.
	- **RetentionType.RUNTIME**: a anotação estará disponível tanto no momento de compilação quanto no momento de execução. Em caso de uma anotação ser necessária para requisições POST, é preciso escolher esta opção, caso contrário, a aplicação irá optar pela bean primary.
- **@Target**: informa onde a anotação deve ser inserida (seja em um atributo, classe, pacote, entre outras opções). Neste caso, a anotação poderá ser inserida em um atributo (enum ElementType.FIELD) ou método (enum ElementType.METHOD). 

Exemplo:

```java
@Retention(RetentionType.RUNTIME)
@Target({ElementType.FIELD, ElementType.METHOD})  
public @interface Aspirado {  
}
```

Agora é só aplicar esta anotação `@Aspirado` em um atributo ou em um método:

```java
@RestController  
@RequestMapping("/testefabrica")  
public class TesteFabricaController {  
  
    @Autowired  
    @Aspirado    
    private Motor motor;  
  
    @PostMapping("/ligarcarro")  
    public CarroStatus ligarCarro(@RequestBody Chave chave){  
        var carro = new HondaHRV(motor);  
        return carro.darIgnicao(chave);  
    }  
}
```


## Estrutura de projeto MVC (Model View Controller)

É um modelo de projeto de projeto que faz a divisão da sua estrutura em 3 camadas:

- **Model**: trata do gerenciamento de dados e das regras de negócio da aplicação. Essa camada envolveria os componentes service e entities.
- **View**: é a camada dedicada a apresentação dos dados de forma compreensível ao usuário. Em uma aplicação real, ela é a parte do front-end.
- **Controller**: fará a comunicação entre a camada view e model, ou seja, recebendo as ações do usuário na camada view e tratando delas de acordo com as regras de negócio estabelecidas na camada model. É nesta camada onde se encontra o componente controller.

### Considerações sobre a arquitetura MVC

![[Pasted image 20250407095841.png]]

- O repositório não necessariamente precisa se conectar com um banco de dados; é possível que ele se conecte também com um arquivo .CSV, por exemplo, para a manipulação de dados.
- Além da injeção do repositório na camada service por meio da instanciação, é possível também a criação de componentes personalizados e, por consequência, sua injenção na camada service.

## Criação automática de ID's

Utilize a anotação **@GeneratedValue(strategy = GenerationType.IDENTITY)** em um atributo ID de uma entidade para a criação automática de ID's em cada registro inserido na tabela. Esta anotação substitui o método randomUUID() utilizado anteriormente:

![[Sessão 2 - Primeiros Passos#^9a6673]]


## Informações adicionais sobre a camada service, repository

### Repository

Ao estender a interface JpaRepository, não é necessário utilizar a anotação @Repository, pois o Spring já reconhece que tal interface, filha de JpaRepository, é um repositório. Porém, ao estender outra interface que não seja JpaRepository, é necessário utilizar a anotação @Repository.
### Service

É possível injetar mais de uma repositório em uma classe service, criando um construtor que instancie todas elas.

## Demonstração da arquitetura em funcionamento

### Exposição do código sql gerado pelo Hibernate

Para que, durante a execução da aplicação, seja apresentado o código SQL no console, insira o o comando `spring:jpa:show-sql: true` seguinte código arquivo application.yml:

```yml
spring:  
  application:  
    name: arquiteturaspring  
  jpa:  
    show-sql: true
```

O exemplo a seguir mostra a criação da tabela tb_todo e também a inserção de um registro feito através de um endpoint:

![[Pasted image 20250409122409.png]]

## Criação de componentes

Como já dito anteriormente, os componentes são classes gerenciadas pelo Spring e são criadas quando tais componentes não se encaixam na categoria de serviços, controllers ou repositórios (que também são componentes).

**OBS.: vale destacar que a anotação @Service é utilizada no lugar de @Component apenas por uma questão de semântica, pois trocando uma pela outra, o funcionamento da aplicação será igual.**

### Exemplo de componente

Uma razão para criar componentes é quando se deseja a validação de um registro de acordo com as regras de negócio. O exemplo a seguir mostra a criação de um componente que verifica se a descrição de um registro já foi inserida no banco. Em caso afirmativo, será lançada uma exceção IllegalArgumentException():

```java
@Component  
public class TodoValidator {  
  
    private TodoRepository todoRepository;  
  
    public TodoValidator(TodoRepository todoRepository) {  
        this.todoRepository = todoRepository;  
    }  
  
    public void validar(TodoEntity todoEntity){  
        if (existeTodoComDescricao(todoEntity.getDescricao())){  
            throw new IllegalArgumentException("Esta descricao ja existe");  
        }  
    }  
  
    private boolean existeTodoComDescricao(String descricao){  
        return todoRepository.existsByDescicao(descricao);  
    }  
}
```

### Método personalizado existsBy

Este método foi personalizado dentro do repositório TodoRepository da seguinte forma:

```
public interface TodoRepository extends JpaRepository<TodoEntity, Integer> {  
  
    boolean existsByDescicao(String descricao);  
}
```

Em suma, ele retorna verdadeiro, caso encontre em algum registro da tabela, a descrição passada como argumento.

Assim como o método findBy, a nomeação de um método existsBy personalizado deve obedecer as mesmas regras de sintaxe:

![[Sessão 2 - Primeiros Passos#^e2dbee]]


Por fim, tal componente deve ser instanciado em um service e aplicado em um dos seus métodos:

```java
@Service  
public class TodoService {  
  
    private TodoValidator todoValidator;  
    private TodoRepository todoRepository;  
  
    public TodoService(TodoValidator todoValidator, TodoRepository todoRepository) {  
        this.todoValidator = todoValidator;  
        this.todoRepository = todoRepository;  
    }  
  
    public TodoEntity salvar(TodoEntity novoTodo){  
        try{  
        todoValidator.validar(novoTodo);  
        return todoRepository.save(novoTodo);  
        } catch(IllegalArgumentException e){  
            throw new ResponseStatusException(HttpStatus.CONFLICT, e.getMessage());  
        }  
    }
	...
}
```

**OBS.: a exceção ResponseStatusException é utilizada para lançar exceções com um status HTTP e uma mensagem de erro. O enum HttpStatus.CONFLICT indica o código 409: quando há um conflito com o estado atual do recurso.  Ou seja, o servidor entendeu a requisição, mas não pode processá-la porque algo está em conflito com o que já existe. Outros exemplos: tentar criar um recurso com um ID que já existe; atualizar um pedido que já foi cancelado; inserir um item duplicado onde não deveria. Em suma, o que você tentou fazer bate de frente com o que já está salvo no sistema.**


## Formas de injeção de dependências

1. **Atributo**: introduzindo a anotação @Autowired no atributo de um componente. Este é a forma menos recomenda pois o Spring sempre injetará a mesma instância. Logo não é possível passar uma instância personalizada através do construtor ou mudar posteriormente a instância através de um método setter.
2. **Construtor**: criação de um método construtor para a injeção de dependência. A anotação @Autowired é opcional neste caso. Esta é a mais recomenda porque indica uma obrigatoriedade daquele bean estar presente na classe (até porque não será possível utilizar a classe sem antes chamar o seu método construtor).
3. **Setter**: a criação de um método setter par a injeção de dependência. A anotação @Autowired aqui já é necessária. Neste caso, a injeção de dependência não indica uma obrigatoriedade, mas indica uma opção.

## Escopo do bean

### O que é?

O escopo do bean é a forma de definir como um bean será criado e gerenciado pelo Spring durante o ciclo de vida da aplicação.

### Como definir o escopo de um bean?

Através da anotação **@Scope**, que receberá como argumento o tipo de tratamento que definirá como o bean será criado e gerenciado (ex.: @Scope("singleton")).

Esta anotação pode ser colocada tanto em um componente quanto em um bean.

### Tipos de escopo

- **singleton**: este é o escopo padrão e define que a instanciação de um componente ocorrerá uma única vez e atenderá a todos os usuários que precisarem utilizá-la. Em vez de @Scope("singleton"), é possivel também definir o escopo como @Scope(BeanDefinition.SCOPE_SINGLETON)
- **request**: a instanciação do componente existe somente a duração da requisição. Faz sentido usar o request se for uma aplicação web. Em vez de @Scope("request"), é possivel também definir o escopo como @Scope(WebApplicationContext.SCOPE_REQUEST)
- **session**: determina que o bean só existirá enquanto o usuário estiver logado. Pode ser útil em casos onde deseja armazenar o ID de login do usuário (que só existirá durante a sessão). Em vez de @Scope("session"), é possivel também definir o escopo como @Scope(WebApplicationContext.SCOPE_SESSION)
- **application**: é semelhante ao singleton, ou seja, cria uma única instância para vários usuários, porém é utilizada somente em aplicações web. Em vez de @Scope("application"), é possivel também definir o escopo como @Scope(WebApplicationContext.SCOPE_APPLICATION)

## Inicialização do Lazy

O lazy é uma técnica que instrui um bean a ser inicializado somente quando for solicitado. Por padrão, o lazy não é utilizado.

### Anotação @Lazy

Esta anotação permite desativar a inicialização do bean caso ele tenha anotação **@Lazy(true)**. Exemplo:

```java
@Lazy(true)  
@Component  
public class BeanGerenciado {
	...
}
```

Por padrão, esta anotação já vem com o valor `true`. Logo, não é preciso especificar o valor como true como não é exemplo anterior.

### Como definir todos os beans como lazy

#### Opção 1

Através de um objeto do tipo builder, chame o método lazy-initialization(true):

```java
@SpringBootApplication  
public class Application {  
  
    public static void main(String[] args) {  
//     SpringApplication.run(Application.class, args);  
  
       SpringApplicationBuilder builder = new SpringApplicationBuilder(Application.class);  
       builder.bannerMode(Banner.Mode.OFF);  
  
       builder.lazyInitialization(true);  
  
       builder.run(args);  
  
    }  
  
}
```

#### Opção 2

No documento application.yml, utilize as propriedades `spring:main:lazy-initialization: true`:

```yml
spring:  
  application:  
    name: arquiteturaspring  
  jpa:  
    show-sql: true  
  main:  
    lazy-initialization: true
```

Seja qual for a opção escolhida, será necessário especificar qual dos beans será inicializado automaticamente através da anotação @Lazy(false).

## Observações sobre o arquivo application.yml

É necessário que as propriedades inseridas neste arquivo sejam coerentes com as dependências disponíveis na aplicação. Por exemplo, a aplicação com as propriedades `spring:jpa:show-sql: true` em arquivo application.yml deve, por consequência, ter a dependência Spring Data Jpa.

### Onde buscar as propriedades do application.yml ?

No site estarão disponíveis todas as propriedades: https://docs.spring.io/spring-boot/appendix/application-properties/index.html

## Criação de propriedades personalizadas

É possível criar propriedades personalizadas dentro de application.yml com o nome de sua preferência e que podem ser lidas em qualquer parte da sua aplicação. Por exemplo:

```yml
sistema:  
  montadora: 200  
  config:  
    variavel: testando propriedade
```

Estes são alguns exemplos de como usuar estas propriedades:

### Como parâmetro

Utilize a anotação **@Value**, responsável por atribuir valores padrão a variáveis e parâmetros de métodos. Coloque logo após a anotação, dentro de parênteses, uma propriedade do application.yml e crie um parâmetro conectado a ela. A propriedade deve estar em formato String dentro de chaves e depois de $. Exemplo:

```java
@Configuration  
public class MontadoraConfiguration {  
  
    @Bean(name = "motorAspirado")  
    public Motor motorAspirado(@Value("${sistema.montadora}") Integer cavalos){  
        var motor = new Motor();  
        motor.setCavalos(cavalos);  
        motor.setCilindros(4);  
        motor.setModelo("XPTO-0");  
        motor.setLitragem(2.0);  
        motor.setTipo(TipoMotor.ASPIRADO);  
        return motor;  
    }
    ...
}
```

Em suma, isso significa que o objeto `motor` sempre será inicializado com o 200 cavalos (como demonstrado no arquivo application.yml).

### Impressão do valor de uma propriedade

Utilize um objeto do tipo **ConfigurableApplicationContext**, responsável por representar o gerenciamento de beans feitos pelo Spring. O seu método getBean() é usado para pegar um objeto gerenciado pelo Spring manualmente. Exemplo na classe Application:

```java
SpringApplicationBuilder builder = new SpringApplicationBuilder(Application.class);  
  
builder.run(args);  
  
ConfigurableApplicationContext applicationContext = builder.context();  
ExemploValue value = applicationContext.getBean(ExemploValue.class);  
value.imprimirVariavel();
```

Neste caso, foi utilizado a classe ExemploValue, que também apresenta a anotação @Value que faz referência a um propriedade do application:

```java
@Component  
public class ExemploValue {  
  
    @Value("${sistema.config.variavel}")  
    private String variavel;  
  
    public void imprimirVariavel(){  
        System.out.println(variavel);  
    }  
}
```

É por meio do método `imprimirVariavel()` que será possível imprimir uma mensagem no final do programa quando ele estiver rodando.

## Como acessar os valores das propriedades de application.yml por meio de classes

Antes de tudo, é necessário habilitar na classe Application o reconhecimento e utilização da classes de Configuration Properties por meio da anotação **@EnableConfigurationProperties**:

```java
@SpringBootApplication  
@EnableConfigurationProperties  
public class Application {  
  
    public static void main(String[] args) {
	    ...
	}
}
```

### O que são classes de Configuration Properties ?

São classes vinculadas a alguma propriedade do application.yml e que tem como finalidade o acesso e gerenciamento dos valores de certas propriedades.

Para criar este tipo de classe, é necessário definir os seus atributos de acordo com as propriedades presentes em application.yml:

```yml
sistema:  
  montadora: 200  
  config:  
    valor1: 500  
    variavel: testando propriedade
```

As propriedades escolhidas para serem transformadas em atributos serão 'valor1' e 'variavel'. É necessário também criar getters e setters para estes atributos:

```java
public class AppProperties {  
  
    private String variavel;  
    private Integer valor1;  
  
    public String getVariavel() {  
        return variavel;  
    }  
  
    public void setVariavel(String variavel) {  
        this.variavel = variavel;  
    }  
  
    public Integer getValor1() {  
        return valor1;  
    }  
  
    public void setValor1(Integer valor1) {  
        this.valor1 = valor1;  
    }  
}
```

Agora é preciso indicar para o Spring Boot que tal classe oferece configurações. Isto é feito através da anotação @Configuration

Por fim, indique esta classe como sendo uma classe de Configuration Properties através da anotação @ConfigurationProperties. Esta anotação possui o atributo prefix, que deve receber o caminho das propriedades vinculadas a classe. Neste caso, o caminho para as propriedades 'valor1' e 'variavel' é 'sistema.config':

```java
@Configuration  
@ConfigurationProperties(prefix = "sistema.config")  
public class AppProperties {
	...
}
```

Agora é possível esta classe de Configuration Properties em alguma outra classe e manipular as propriedades do application.yml.

