
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

O `AuthenticationProvider` é uma interface encarregada de processar uma solicitação de autenticação específica. Para criação de um 'fornecedor de autenticação' customizado, é necessário criar um componente que implemente a interface `AuthenticationProvider`, que possui dois métodos:

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

# 131. Eliminando o prefixo ROLE do security

Crie um bean que retorne uma instância de `GrantedAuthorityDefaults`, sendo o argumento uma String vazia:

```java
@Bean  
public GrantedAuthorityDefaults grantedAuthorityDefaults(){  
    return new GrantedAuthorityDefaults("");  
}
```

Este método deverá ficar dentro da classe de configuração de segurança (neste caso, `SecurityConfiguration`).

Só isso já será o suficiente para que esse bean seja registrado no contexto de segurança do Spring e consultado no momento em que for decidir como interpretar os nomes de roles.

# 132. Ajustando o Security Service

Dado que está sendo utilizado agora uma a classe de autenticação customizada, e não mais o `UserDetails`, o método do `SecurityService` deverá retornar um objeto `Usuario` caso o `SecurityContextHolder.getContext().getAuthentication()` retorne uma instância de `CustomAuthentication`:

```java
@Component  
@RequiredArgsConstructor  
public class SecurityService {  
  
    private final UsuarioService usuarioService;  
  
    public Usuario obterUsuarioLogado(){  
        Authentication authentication = SecurityContextHolder.getContext().getAuthentication();  
  
        if (authentication instanceof CustomAuthentication customAuth){  
            return customAuth.getUsuario();  
        }  
  
        return null;  
    }  
}
```

# 134. Adicionando campo para salvar email no cadastro de usuários

Caso deseje inserir uma nova coluna, que permita valores nulos, execute o comando:

```sql
alter table nome_tabela add column nome_coluna(100)
```

**OBS.: caso deseje inserir uma nova coluna que não permita valores nulos, apenas apague a tabela e crie novamente com a coluna já adicionada.**
# 135. Implementando lógica de customização da autenticação Google

Esta aula teve como objetivo capturar os dados que o usuário passou no login do Google e transformar esses dados em um objeto `CustomAuthetication`.

Para isso, será necessário ir até o método que define a cadeia de filtros de segurança, presente na classe de configuração de segurança, e trocar `oauth2Login(Customizer.withDefaults())` por `oauth2Login(oauth2 -> oauth2.successHandler())`, sendo `oauth2.successHandler()` responsável por executar uma ação em caso do usuário se autenticar com sucesso. 

O método `oauth2.successHandler()` irá receber como argumento uma classe que implemente o `AuthenticationSuccessHandler`. No exemplo da aula, foi criado uma nova classe que estende `SavedRequestAwareAuthenticationSuccessHandler`, sendo que ela mesma implementa o `AuthenticationSuccessHandler`.

A classe `SavedRequestAwareAuthenticationSuccessHandler` é **o manipulador de sucesso de autenticação padrão usado pelo Spring Security**. Suponha que um usuário não-autenticado tente acessar uma página da aplicação. A sua requisição será salva pela aplicação e ele será redirecionado para a página de login. Depois se autenticar com sucesso, a classe `SavedRequestAwareAuthenticationSuccessHandler` irá verificar se existe uma requisição salva e, em caso afirmativo, a classe irá redirecionar o usuário para a página que ele tentou acessar originalmente.

A interface `AuthenticationSuccessHandler` possui o método `onAuthenticationSuccess` (que possui **apenas três** parâmetros), responsável por conter dentro de si toda a lógica do que fazer após o usuário logar com sucesso. No exemplo da aula, foi aplicado a seguinte lógica:

```java
@Override  
public void onAuthenticationSuccess(  
        HttpServletRequest request,  
        HttpServletResponse response,  
        Authentication authentication) throws ServletException, IOException {  
  
    OAuth2AuthenticationToken oAuth2AuthenticationToken = (OAuth2AuthenticationToken) authentication;  
    OAuth2User oAuth2User = oAuth2AuthenticationToken.getPrincipal();  
    String email = oAuth2User.getAttribute("email");  
  
    Usuario usuario = this.usuarioService.obterPorEmail(email);  
  
    authentication = new CustomAuthentication(usuario);  
  
    SecurityContextHolder.getContext().setAuthentication(authentication);  
  
    super.onAuthenticationSuccess(request, response, authentication);  
}
```

Ao executar a aplicação, o parâmetro `authentication` irá receber um objeto `OAuth2AuthenticationToken` criado pelo Spring Security, que contém todas as informações essenciais sobre a identidade do usuário. Através do método `getPrincipal()`, é retornado um objeto `OAuth2User`, que possui os dados pessoais do usuário: nome, e-mail, foto de perfil, etc. Caso queira obter o valor referente a um determinado dado pessoal, utilize o `getAttribute()` e passe como argumento o tipo de dado pessoal (ex.: email).

Depois de capturar o usuário por meio do método `obterPorEmail()` e passá-lo como argumento para a autenticação customizada, é utilizado o comando `SecurityContextHolder.getContext().setAuthentication(authentication);` para atualizar o "contexto de segurança" da sessão atual do usuário. O `SecurityContextHolder` é uma classe central do Spring Security que armazena, de forma segura, as informações do usuário atualmente logado.

**OBS.: "Contexto de Segurança" (SecurityContext) é o objeto que guarda as informações sobre quem é o usuário atualmente logado e o que ele pode fazer naquela requisição específica.**

Por fim, é delegado para o método da classe pai (`SavedRequestAwareAuthenticationSuccessHandler`) a responsabilidade de redirecionamento do usuário para a página solicitada.

Para ver o resultado do método `onAuthenticationSuccess`, utilize o seguinte método, que irá mostrar uma mensagem de boas vindas depois que o usuário se autenticar.

```java
@GetMapping("/")  
@ResponseBody  
public String paginaHome(Authentication authentication){  
    if (authentication instanceof CustomAuthentication customAuthentication){  
        System.out.println(customAuthentication.getUsuario());  
    }  
    return "Hello " + authentication.getName();  
}
```

**OBS.: quando quiser fazer o logout da aplicação, basta digitar localhost:8080/logout**
# 136. Configurando autenticação do Google no formulário próprio

## Habilitando o formulário customizado

É necessário habilitar o método `loginPage()` tanto para o `http` como também dentro do `oauth2Login`:

```java
.formLogin(configurer -> {  
    configurer.loginPage("/login").permitAll();  
})
```

```java
.oauth2Login(oauth2 -> {  
    oauth2  
            .loginPage("/login")  
            .successHandler(successHandler);  
})
```

## Acrescentando o link do Google no formulário

Crie dentro do formulário html um link através do elemento `<a></a>`, utilizando o atributo `href` fornecido pelo Thymeleaf. É através deste atributo que será informado o link oauth2/authentication/google (que é um link padrão do Google). Você deve colocá-lo dentro de `@{}`.

```html
<a th:href="@{oauth2/authorization/google}" class="btn btn-primary w-100">Entrar com Google</a>
```

Isso é o suficiente para já testar a autenticação do Google no seu formulário customizado.

## Como se autenticar pelo Google através do Postman

Na área `Headers` do Postman, adicione a chave `Cookie` e o valor como `JSESSIONID=` mais o id da sua sessão. É possível encontrar o valor desta forma:

![[Pasted image 20251017155818.png]]

# 137. Lógica para novos usuários que só tem login Google

Anteriormente, o usuário conseguia apenas logar pelo Google, porém não conseguia se cadastrar através do Google. Com esta lógica, é possível fazer as duas coisas:

```java
private static final String SENHA_PADRAO = "321";  
private final UsuarioService usuarioService;  
  
@Override  
public void onAuthenticationSuccess(  
        HttpServletRequest request,  
        HttpServletResponse response,  
        Authentication authentication) throws ServletException, IOException {  
  
    OAuth2AuthenticationToken oAuth2AuthenticationToken = (OAuth2AuthenticationToken) authentication;  
    OAuth2User oAuth2User = oAuth2AuthenticationToken.getPrincipal();  
    String email = oAuth2User.getAttribute("email");  
  
    Usuario usuario = this.usuarioService.obterPorEmail(email);  
  
    if (usuario == null){  
        usuario = cadastrarUsuarioNaBase(email);  
    }  
  
    authentication = new CustomAuthentication(usuario);  
  
    SecurityContextHolder.getContext().setAuthentication(authentication);  
  
    super.onAuthenticationSuccess(request, response, authentication);  
}  
  
private Usuario cadastrarUsuarioNaBase(String email) {  
    Usuario usuario;  
    usuario = new Usuario();  
    usuario.setEmail(email);  
    usuario.setLogin(obterLoginAPartirDoEmail(email));  
    usuario.setSenha(SENHA_PADRAO);  
    usuario.setRoles(List.of("OPERADOR"));  
  
    this.usuarioService.salvar(usuario);  
    return usuario;  
}  
  
private String obterLoginAPartirDoEmail(String email) {  
    return email.substring(0, email.indexOf("@"));  
}
```

Em resumo: se o objeto adquirido pelo `this.usuarioService.obterPorEmail(email)` for nulo, então será criado, através do método `cadastrarUsuarioNaBase(String email)`, um novo objeto `Usuario` e, por fim, salvo no banco.

**OBS.: o método `substring()` é utilizado para capturar uma fração de uma `String`. No caso de `obterLoginAPartirDoEmail(String email)`, será capturado a primeira letra do e-mail até a última letra anterior ao @.**
## Criando métodos de forma mais prática.

Selecione uma parte da lógica do programa e, em seguida, pressione `Ctrl` + `Alt Gr` + `m`. Isso fará com que esta lógica seja transferida para o corpo de um novo método.

# 138. Variáveis de Ambiente para guardar secrets e conclusao do módulo

## Por que utilizar variáveis de ambiente?

É necessário utilizá-las no lugar do ID e da chave secreta do cliente, pois o GitHub não irá permitir subir elas em um commit. Então é preciso usar as variáveis de ambientes como forma de referência para estes dois valores.
## Como criar uma variável de ambiente?

Antes de tudo, copie os valores que serão referenciados e coloque em outro lugar. No lugar do valor referenciado, utilize `${}` e informe um nome (qualquer um) para variável dentro das chaves do `${}`.

Agora clique nos `⋮` (canto superior direito) -> `Edit...`. Será aberto a seguinte tela:

![[Pasted image 20251020151549.png]]

Clique agora no ícone de `Edit environment variables` (à direita com o círculo vermelho). Caso não apareça, clique em `Modify options` -> `Environment variables` para que apareça esta opção.

Depois clique no ícone de `+` para ir adicionando as variáveis de ambiente. Por fim, clique em `Ok` -> `Apply` -> `Ok`.

**OBS.: as variáveis de ambiente não estarão disponíveis em um projeto caso você venha cloná-lo do GitHub.**