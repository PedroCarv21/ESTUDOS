
# 128. Habilitando Login Social e Autenticando com conta Google

## Criando uma credencial

Será necessário criar esse credencial lá no [Google Cloud](https://cloud.google.com/?utm_source=google&utm_medium=cpc&utm_campaign=latam-BR-all-pt-dr-BKWS-all-all-trial-e-dr-1710136-LUAC0010101&utm_content=text-ad-none-any-DEV_c-CRE_512285710731-ADGP_Hybrid+%7C+BKWS+-+EXA+%7C+Txt_GCP-General-KWID_301173107424-kwd-301173107424&utm_term=KW_google%20cloud-ST_Google+Cloud&gclsrc=aw.ds&gad_source=1&gad_campaignid=6479359091&gclid=Cj0KCQjwrc7GBhCfARIsAHGcW5UsJZ0H52XdTcfHtdVofxvgUf1-FFHguVhy1TmSOafOllm9mLDQaJUaAp7sEALw_wcB) para que o Google saiba que a sua aplicação estará utilizando a ferramenta de autenticação deles. Depois de acessar a página clique no botão `Console`. O console é o painel utilizado para acessar os serviços do Google Cloud, tais como: criação de máquinas virtuais, bancos de dados, deploy da aplicação, entre outras.

**OBS.: alguns serviços do Google Cloud são gratuitos enquanto outros são pagos.**

![[Pasted image 20250924112952.png]]

Clique em `My Project` para criar um projeto:

![[Pasted image 20250924113931.png]]

Clique em `Novo Projeto` caso ainda não tenha nenhum.

![[Pasted image 20250924114128.png]]

Por fim, escolha o nome do projeto e clique em `Criar`:

![[Pasted image 20250924114402.png]]

Clique novamente em `My Project` e selecione o projeto que acabou de criar:

![[Pasted image 20250924115029.png]]

Acesse o menu lateral no canto esquerdo -> `APIs e serviços` -> `Credenciais`:

![[Pasted image 20250924115607.png]]

Na página de Credenciais, será necessário configurar a tela de consentimento. A tela de consentimento está relacionada a permissão que o Google tem, dada por você, de acessar os seus dados em outra aplicação através de APIs.

![[Pasted image 20250924115905.png]]

Clique em `Vamos começar`:

![[Pasted image 20250924121245.png]]

Informe o nome e email da aplicação e clique em `Avançar`:

![[Pasted image 20250924122132.png]]

Escolha a opção `Externo` e clique em `Avançar`:

![[Pasted image 20250924121644.png]]

Informe seu email e clique em `Avançar`:

![[Pasted image 20250924122313.png]]

Selecione em `Eu concordo...` e clique em `Continuar`. Por fim, clique em `Criar`

![[Pasted image 20250924122453.png]]

Agora volte para a seção credenciais através do menu lateral no canto esquerdo -> `APIs e serviços` -> `Credenciais`. Clique em `+ Criar credenciais` -> `ID do cliente OAuth`

![[Pasted image 20250924133005.png]]

A partir daí, você será direcionado para uma página com vários campos de entrada que devem ser preenchidos com os seguintes valores: 

- **Tipo de aplicativo**: Aplicativo da Web
- **Nome**: qualquer um
- **Origens JavaScript autorizadas**: http://localhost:8080
- **URIs de redirecionamento autorizados**: http://localhost:8080/login/oauth2/code/google

**OBS.: preencha os dados com os valores informados acima (com exceção do campo 'Nome').**

Por fim, clique em `Criar`.

Com isso, irá abrir uma pequena janela informando o ID do cliente e também a chave secreta do cliente:

![[Pasted image 20250924153713.png]]

Essas duas informações devem ser guardadas para a próxima configuração na aplicação Spring Boot.
## OAuth2

OAuth2 é um padrão de autorização que serve para permitir que um aplicativo acesse recursos (como dados ou serviços) em nome de um usuário, sem precisar pedir a senha desse usuário.

Exemplo:
- Você quer usar um app de agenda que mostra seus eventos do Google Calendar.
- Em vez de dar sua senha do Google para esse app (o que seria inseguro), você faz login pelo Google.
- O Google mostra uma tela de consentimento dizendo:
- “O App AgendaX quer acessar seu Google Calendar.”
- Se você aceitar, o Google entrega ao app um token de acesso (uma espécie de chave temporária).
- O app usa esse token para acessar apenas os dados autorizados, sem nunca ver sua senha.

Para usar esse tipo de autorização, use a dependência OAuth2 Client:

```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-oauth2-client</artifactId>  
</dependency>
```

Coloque também essas configurações no seu application.yml:

```yml
security:  
  oauth2:  
    client:  
      registration:  
        google:  
          client-id:  
          client-secret: 
```

Esse código conecta seu app ao Google:

- O `client-id` diz “quem é o app”.
    
- O `client-secret` prova “que o app é legítimo”.
    
Utilize o ID do cliente e a chave secreta do cliente, gerados após a criação do cliente OAuth, como valores para as propriedades `client-id` e `client-secret`.

E com isso, sua aplicação pode permitir login com Google ou consumir APIs do Google em nome do usuário.

## Habilitando a autenticação OAuth2 no form. de Login

Para habilitar a autenticação via OAuth2 Login no Spring Security, utilize comando `http.oauth2Login(Customizer.withDefaults())` na classe de configuração do Secutiry. Por ora, utilize o formulário padrão com o comando `http.formLogin(Customizer.withDefaults())`, pois este já adiciona automaticamente o link de autenticação do Google no formulário. O código deve ficar mais ou menos assim:

```java
@Bean  
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception{  
        return http  
                .csrf(AbstractHttpConfigurer::disable)  
//                .formLogin(configurer -> {  
//                    configurer.loginPage("/login").permitAll();  
//                })  
                .formLogin(Customizer.withDefaults())  
                .httpBasic(Customizer.withDefaults())  
                .authorizeHttpRequests(authorize -> {  
                    authorize.requestMatchers("/login/**").permitAll();  
                    authorize.requestMatchers(HttpMethod.POST, "/usuarios/**").permitAll();  
  
                    authorize.anyRequest().authenticated();  
                })  
                .oauth2Login(Customizer.withDefaults())  
                .build();  
    }
```

Após executar a aplicação, a página de Login irá aparecer da seguinte forma:

![[Pasted image 20250925093419.png]]

Ao clicar no link `Google` e logar com os seus dados do Google, você será autenticado, porém não será levado para página alguma:

![[Pasted image 20250925095346.png]]

Para exibir alguma mensagem, vá até a sua classe Controller (**não confundir com RestController**) e crie um novo método como este:

```java
@GetMapping("/")  
@ResponseBody  
public String paginaHome(){  
    return "Hello World";  
}
```

A anotação `@ResponseBody` serve para informar que o retorno aqui não será um arquivo, mas sim uma mensagem que deve ser exibida na página principal (já que o cominho é apenas uma barra (/)). O resultado será este após se autenticar:

![[Pasted image 20250925095945.png]]

# 129. Criando nossa própria Authentication

Na seção passada, foi dito que, ao fazer login através da autenticação do Google, seria retornado um código de autenticação (como um token) para que uma determinada aplicação tivesse acesso aos recursos/dados autorizados pelo Google.

Sendo assim, será necessário criar uma autenticação customizada, adaptada ao contexto da aplicação. Para isso, é preciso criar uma classe que implemente a interface `Authentication` do pacote `org.springframework.security.core`, que contém a principal identidade do utilizador, as credenciais (como a senha), e as autoridades (ou permissões) concedidas ao utilizador.

**OBS.: não esqueça de implementar os métodos da interface.**

## Retornando as roles de um usuário

Para isso, será criado um atributo do tipo de uma classe que carregue os seus dados (neste exemplo, será a classe `Usuario`). Assim será possível retornar as roles de um determinado usuário a partir de um dos métodos de `Authentication` que foram implementados (neste caso, o método `getAuthorities()`).

Este método retornará uma lista de `GrantedAuthority` (uma interface com um método abstrato que retorna uma role); portanto, é necessário que seja retornado uma lista de objetos do tipo de uma classe que implementa `GrantedAuthority`. Neste exemplo, será utilizado a classe `SimpleGrantedAuthority`

```java
@RequiredArgsConstructor  
@Getter  
public class CustomAuthentication implements Authentication {  
  
    private final Usuario usuario;  
  
    @Override  
    public Collection<GrantedAuthority> getAuthorities() {  
        return usuario  
                .getRoles()  
                .stream()  
                .map(role -> new SimpleGrantedAuthority(role))  
                .collect(Collectors.toList());  
    }
	...
}
```

Há também outros métodos de `Authentication` que terão o seu corpo alterado:

- `getDetails()` e `getPrincipal()`: retornarão os as informações do usuário (pode ser o próprio objeto `Usuario`).
- `isAuthenticated()`: retorna um valor booleano que informa se o usuário está autenticado ou não. O valor ser alterado para `true`, caso contrário, não será possível logar.
- `getName()`: retornará o nome do usuário.

# 130. Criando um `AuthenticationProvider` customizado

Para criação de um 'fornecedor de autenticação' customizado, é necessário criar um componente que implemente a interface `AuthenticationProvider`, que possui dois métodos:

- `supports(Class<?> authentication)`: informará qual o tipo de autenticação esse 'fornecedor de autenticação' suporta. Neste caso, como se trata do fornecimento de login e senha, será utilizado a classe `UsernamePasswordAuthenticationToken.class` como argumento do método `authentication.isAssignableFrom()`, método responsável por comparar o tipo de autenticação fornecida pelo usuário e a autenticação suportada pelo 'fornecedor de autenticação'. Caso afirmativo, retornará `true`.
- `authenticate(Authentication authentication)`: caso o método `supports` retorne `true`, será retornado um objeto `UsernamePasswordAuthenticationToken`, que também implementa `Authentication`, e injetado esse objeto no método `authenticate`. O objeto `UsernamePasswordAuthenticationToken` já estará com os dados informados pelo usuário durante o login. Por fim, será criada uma regra de negócio para fazer a validação do login, retornando um objeto `Authentication` (neste caso, será usado a classe `CustomAuthentication` que implementa esta interface).

Exemplo de classe com `AuthenticationProvider`: 

```java
@Component  
@RequiredArgsConstructor  
public class CustomAuthenticationProvider implements AuthenticationProvider {  
  
    private final UsuarioService usuarioService;  
    private final PasswordEncoder passwordEncoder;  
  
    @Override  
    public Authentication authenticate(Authentication authentication) throws AuthenticationException {  
  
        String login = authentication.getName();  
        String senhaDigitada = authentication.getCredentials().toString();  
  
        Usuario usuarioEncontrado = usuarioService.obterPorLogin(login);  
  
        if (usuarioEncontrado == null){  
            throw getErroUsuarioNaoEncontrado();  
        }  
  
        String senhaCriptografada = usuarioEncontrado.getSenha();  
  
        boolean senhasBatem = this.passwordEncoder.matches(senhaDigitada, senhaCriptografada);  
  
        if (senhasBatem){  
            return new CustomAuthentication(usuarioEncontrado);  
        }  
  
        throw getErroUsuarioNaoEncontrado();  
    }  
  
    private UsernameNotFoundException getErroUsuarioNaoEncontrado(){  
        return new UsernameNotFoundException("Usuario e/ou senha incorretos!");  
    }  
  
    @Override  
    public boolean supports(Class<?> authentication) {  
        return authentication.isAssignableFrom(UsernamePasswordAuthenticationToken.class);  
    }  
}
```

Observe que, ao executar a aplicação pelo debug e fazer uma tentativa de autenticação, é carregado um objeto `UsernamePasswordAuthenticationToken` com os dados que o usuário forneceu:

![[Pasted image 20250929165334.png]]

No entanto, mesmo que os dados estejam certos, o usuário não terá permissão de autenticar (gerando um código de status 403), pois quando são inseridas as roles em um objeto Usuario, é acrescentado a cada role um prefixo `ROLE_`. Isso será concertado na próxima aula.