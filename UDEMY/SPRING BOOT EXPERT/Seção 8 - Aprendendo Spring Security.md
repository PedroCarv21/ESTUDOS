
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