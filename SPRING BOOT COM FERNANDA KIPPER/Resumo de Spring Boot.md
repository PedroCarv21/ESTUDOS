
Resumo baseado na aula: [CURSO DE SPRING para INICIANTES](https://www.youtube.com/watch?v=YY_hf0FOIcU&t=898s)

## O que é o Spring Initialzr ?

Uma ferramenta online para a configuração e criação de aplicações Spring Boot: https://start.spring.io/

Ao acessar o site, deve-se preencher o campo **Artificat** com o nome da sua aplicação e o campo **Group** com o domínio do seu projeto.

![[SPRING_INITIALZR.PNG]]

Em seguida, escolha as dependências que deverão estar presentes no seu projeto a partir do botão **ADD DEPENDENCIES**:

![[SPRING_INITIALZR2.PNG]]

Por fim, clique em **GENERATE** para fazer a instalação do projeto com as dependências.

![[SPRING_INITIALZR3.PNG]]

## Entendendo a estrutura Spring Boot

- pom.xml: arquivo de configuração das dependências. Cada tag ``` <dependency></dependency> ``` contém uma dependência e ela fica armazenada dentro da tag ```<dependencies></dependencies>```. Este arquivo é gerenciado pelo Maven, a ferramenta de instalação automática das dependências.
- pasta src/test/java: é onde serão armazenadas as classes do projeto. Já de início o projeto vem com uma classe para testes localizado nesta pasta. É a partir desta classe que será iniciado a execução do projeto:

![[Pasted image 20250316163445.png]]

- pasta src/main/resources: onde estarão os principais arquivos de configuração (como o **application.properties**) assim como também arquivos .css, .js e scripts SQL:
![[Pasted image 20250316163923.png]]

## O que são anotações ?

As anotações (representadas com o @ no início) servem para aplicar determinadas configurações em cima de uma classe. Por exemplo, a anotação **@SpringBootTest** indica que o contexto da aplicação é um contexto de aplicação Spring Boot.

```
@SpringBootTest
class NovoProjetoApplicationTests {
	@Test

	void contextLoads() {

	}
}
```

## Controller

É uma classe que trata das requisições HTTP (GET, PUT, POST, ...) e envia respostas ao cliente (200, 404, ....). Para que uma classe seja identificada como Controller é necessário aplicar a anotação **@RestController** da seguinte forma:

```
package com.carvalho.novo_projeto.controller;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloWorldController {

}
```

 **OBS.: foi criado um pacote específico para os controllers chamado controller.**

### Endpoints

Os endpoints são URL's que servem como mapeamento para algum controller. Por exemplo: se um controller possui um endpoint /users então, para acessar esse controller, será necessário digitar o domínio do site/users (ex.: www.ecommerce.com/users).

Para criar um endpoint para um controller é necessário usar a anotação @RequestMapping, definindo entre parênteses o caminho desejado (neste caso foi /hello-world):

```
package com.carvalho.novo_projeto.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/hello-world")
public class HelloWorldController {

  
}
```

### Requisições HTTP

Dentro de um controller é preciso criar um método que se relacione com algum tipo de requisição HTTP. No exemplo a seguir foi criado um método que retorna uma mensagem Hello World e corresponde a uma requisição GET por meio da anotação @GetMapping, definindo entre parênteses o caminho para o acesso deste método (neste caso é )
