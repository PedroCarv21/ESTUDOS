
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