
## 114. Conceitos Básicos sobre segurança de API's

### Diferença entre autenticação e autorização

A autenticação tem como finalidade a identificação de um usuário enquanto que a autorização define as ações permitidas (**authority**) que um usuário pode realizar com base no grupo (**role**) ao qual ele pertence.

O **Spring Security** é um framework que fornece as ferramentas necessárias para o tratamento de autenticações e autorizações.

## 116. Atualizando a versão do projeto e adicionando o Security

Para incluir o Spring Security no seu sistema, inclua a seguinte dependência:

```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-security</artifactId>  
</dependency>
```

Só por incluir essa dependência, o sistema já será configurado de um modo que exija a autenticação do cliente (seja pelo navegador ou Postman) para que então ele execute qualquer uma das requisições do sistema.

Ao executar a aplicação, irá aparecer uma mensagem semelhante a esta informando a senha necessária para autenticação:

```
Using generated security password: 1b30bdc7-8124-4808-b6ca-00f726302b9c
```

Caso tente executar uma requisição sem fazer a autenticação, será apresentado o código de status 401:

![[Pasted image 20250901111517.png]]

### Autenticação no Navegador

Para fazer a autenticação no navegador, acesse o console do Postman e copie e cole o link da requisição no navegador:

![[Pasted image 20250901111820.png]]
![[Pasted image 20250901111935.png]]

![[Pasted image 20250901112235.png]]

Essa é a pagina de autenticação. Digite `user` no campo `Username` e a senha gerada durante a execução da aplicação no campo `Password`. Por fim, clique em `Sign in`.

O resultado deve ser a execução da requisição.
### Autenticação no Postman

Vá até a aba `Authorization` do Postman -> escolha a opção `Basic Auth` na aba `Auth Type` -> defina o usuário e a senha nos campos `Username` e `Password`. Por fim, clique em `Send`.

![[Pasted image 20250901112738.png]]

## 117. Criando a configuração básica do Security com SecurityFilterChain

Como visto anteriormente, um sistema Spring, apenas por incluir a dependência do Spring Security, é capaz de oferecer uma segurança padrão. No entanto, é possível configurar essa segurança.
### Anotações `@Configuration` e `@EnableWebSecurity`

É necessário criar uma classe de configuração através da anotação `@Configuration`. No entanto, para habilitar essa classe de configuração como uma classe de segurança web, é preciso usar a anotação `@EnableWebSecurity`.

### Interface `SecurityFilterChain`

Esta interface representa uma cadeia de filtros de segurança, determinando como as requisições HTTP serão processadas antes que cheguem nos controladores.

Para que esses filtros possam ser aplicados, é necessário utilizar a classe `HttpSecurity` para definir como a `SecurityFilterChain` se comporta.

A classe `HttpSecurity` oferece alguns métodos:

- `csrf()`: utilizado como mecanismo de proteção contra ataques CSRF: um ataque que obriga o usuário final a executar ações indesejadas em um site que já concedeu autenticação a ele. Se for utilizado `AbstractHttpConfigurer::disable` como argumento, isso significa que este mecanismo de proteção estará desabilitado.
- `formLogin()`: habilita a autenticação baseada em um formulário. O argumento `Customizer.withDefaults()` habilita a página de login padrão.
- `httpBasic()`: habilita a autenticação HTTP Basic, que verifica a identidade de alguém através do fornecimento de um nome e uma senha codificada em Base64. O argumento `Curstomizer.withDefaults()` garante que as configurações padrão para este tipo de autenticação sejam aplicadas.
- `authorizeHttpRequests()`: define as regras de autorização das requisições. A expressão lambda `authorize -> authorize.anyRequest().authenticated()` como argumento implica que todas as requisições devem ter um usuário autenticado.
- `build()`: finaliza a configuração do `SecurityFilterChain`, da mesma forma o método `build` utilizado pelo `ResponseEntity`.

Exemplo:

```java
@Configuration  
@EnableWebSecurity  
public class SecurityConfiguration {  
  
    @Bean  
    public SecurityFilterChain securityFilterChain(HttpSecurity hhtp) throws Exception{  
        return hhtp  
                .csrf(AbstractHttpConfigurer::disable)  
                .formLogin(Customizer.withDefaults())  
                .httpBasic(Customizer.withDefaults())  
                .authorizeHttpRequests(authorize -> authorize.anyRequest().authenticated())  
                .build();  
    }  
}
```

Somando todos esses filtros, o resultado é a mesma autenticação já utilizada na aula 116. Ou seja, o código acima representa a autenticação padrão do Spring Security.

## 118. Como funciona a autenticação HTTP BASIC

### Autenticação Http Basic sem formulário

É possível ainda fazer autenticação em uma página web sem que o formulário login esteja habilitado por meio do `formLogin(Customizer.withDefault())`. Sem ele, o navegador irá criar um **prompt de autenticação Http Basic** semelhante a este:

![[Pasted image 20250903120414.png]]

### Forma alternativa de se autenticar no Postman

Em vez de definir o usuário e a senha na aba Authorization do Postman, é possível se autenticar ao passar na aba Header a chave `Authorization`. Já o valor deve ser `Basic ` mais a codificação de `user:<senha gerada pela aplicação>`.

Por exemplo, acesse o site https://www.base64encode.org/ e digite `user:` mais a senha gerada pela aplicação e, por fim, clique em `encode`.

![[Pasted image 20250903121312.png]]

Copie o código gerado e passe como valor depois da palavra `Basic `:

![[Pasted image 20250903121609.png]]

## 119. Habilitando e customizando formulario de login

### Biblioteca Thymeleaf

Esta é uma biblioteca que permite a criação de páginas em aplicações Spring. Esta é a sua dependência:

```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-thymeleaf</artifactId>  
</dependency>
```

### Criação de páginas Web

Por convenção, as páginas web ficam dentro de uma pasta chamada `templates`. A página que foi criada é um formulário de Login.

Na tag `<html></html>` adicione o atributo `xmlns:th="http://www.thymeleaf.org"`. O comando `xmlns` permite você definir um nome que servirá como indicador de que certos atributos pertencem ao Thymeleaf (neste caso, foi escolhido o nome `th`). Por fim, a URL é utilizada como uma forma identificador para reconhecer os atributos especiais do Thymeleaf.

Os atributos especuiais do Thymeleaf (também chamados de diretivas) serão responsáveis por capacitar uma interação do código java com os documentos HTML, trazendo um comportamento dinâmico que os atributos HTML padrão não tem a capacidade de fazer.

Uma dessas diretivas é o `action`, que define a URL de destino para onde os dados do formulário deverão ser enviados. Por exemplo, caso os dados tenham que ser enviados para a URL `/login` então essa URL deverá ficar dentro de `@{}` como é mostrado no código abaixo:

```html
<form th:action="@{/login}" method="post">
```

**OBS.: perceba que o `th:` é usado como prefixo para identificar que o `action` utilizado é, na verdade, uma diretiva.**

### Anotação `@EnableWebMvc`

Essa anotação é responsável desligar a auto-configuração do Spring MVC (que já vem por padrão no Spring Boot) e habilitar a sua configuração manual.

**OBS.: Spring MVC é um módulo do Spring que organiza a aplicação de acordo com o modelo MVC.**

Uma das interfaces que fornece métodos para a configuração do MVC é a `WebMvcConfigurer`. Um dos seus métodos, `addViewControllers(ViewControllerRegistry registry)`, permite registrar rotas simples (URLs) que apontam direto para uma view (página).

Através do parâmetro `registry`, é possível definir uma rota com o método `addViewController()` e, em seguida, definir através de `addViewName()` qual será a página HTML acessada através desta rota. Exemplo:

```java
@Override
public void addViewControllers(ViewControllerRegistry registry){  
    registry.addViewController("/login").setViewName("login");
}
```

Caso você tenha vários controladores ou `ViewControllerRegistry` que respondem à mesma URL, e queira priorizar a execução de um mapeamento específico, utilize o comando `registry.setOrder(Ordered.HIGHEST_PRECEDENCE)`. Exemplo:

```java
@Override
public void addViewControllers(ViewControllerRegistry registry){  
    registry.addViewController("/login").setViewName("login");
	registry.setOrder(Ordered.HIGHEST_PRECEDENCE);
}
```

O código inteiro ficaria deste jeito:

```java
@Configuration  
@EnableWebMvc  
public class WebConfiguration implements WebMvcConfigurer {  
  
    @Override  
    public void addViewControllers(ViewControllerRegistry registry){  
        registry.addViewController("/login").setViewName("login");  
        registry.setOrder(Ordered.HIGHEST_PRECEDENCE);  
    }  
}
```

### Alternativa ao código anterior

Observe o código seguinte:

```java
@Controller  
public class LoginViewController {  
  
    @GetMapping("/login")  
    public String paginaLogin(){  
        return "login";  
    }  
}
```

Ele praticamente substitui a classe de configuração mostrada anteriormente. Em vez de um `@RestController` (que lida com API's), é usado um `@Controller`, responsável por retornar páginas (views). Ou seja, o código acima irá retornar uma página `login.html` quando for acessado a URL `/login`.