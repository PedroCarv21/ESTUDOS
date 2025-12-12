
# 92. Adicionando validação de campos com Bean Validation

Para que as anotações a seguir sejam disponibilizadas, é necessário obter a dependência Validation:

```xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-validation</artifactId>  
</dependency>
```
## Anotações `@NotBlank` e `@NotNull`

A primeira anotação é utilizada em objetos `String` e valida se o campo não está vazio (" ") e a segunda verifica se o campo não está nulo. Exemplo:

```java
public record AutorDTO(  
        UUID id,  
        @NotBlank(message = "Campo obrigatorio")  
        String nome,  
        @NotNull(message = "Campo obrigatorio")  
        LocalDate dataNascimento,  
        @NotBlank(message = "Campo obrigatorio")  
        String nacionalidade) {  
  
    public Autor mapearParaAutor(){  
        Autor autor = new Autor();  
        autor.setNome(this.nome);  
        autor.setDataNascimento(this.dataNascimento);  
        autor.setNacionalidade(this.nacionalidade);  
        return autor;  
    }
}
```

## Anotação `@Valid`

Esta anotação é geralmente colocada em um parâmetro de algum método, de modo que o Spring Boot aciona automaticamente a validação deste parâmetro antes que o método seja invocado.

# 93. Criando um Exception Handler

## Anotação `@RestControllerAdvice`

Esta anotação, usada em uma classe, permite que as exceções sejam tratadas em qualquer lugar da aplicação. Os métodos contidos dentro de uma classe com `@RestControllerAdvice` devem conter a anotação `@ExceptionHandler`, onde será passado como argumento a exceção específica tratada por aquele método.

Por exemplo, se o método irá tratar da exceção `MethodArgumentNotValidException`, a anotação deve ficar como `@ExceptionHandler(MethodArgumentNotValidException.class)`.

**OBS.: `MethodArgumentNotValidException` é uma exceção do Spring que é lançada quando a validação de um argumento de método falha, geralmente devido a anotações de validação como `@NotNull` ou `@NotEmpty`.**
## Anotação `ResponseStatus`

É utilizado para especificar o código de status que aquele método irá retornar, seja em caso de sucesso ou de exceções. É necessário passar como argumento desta anotação uma constante fornecida pela classe `HttpStatus`. 

Por exemplo: `@ResponseStatus(HttpStatus.UNPROCESSABLE_ENTITY)`

![[Seção 5 - Desenvolvimento de API's RestFul#^53643b]]

## Mais informações sobre `MethodArgumentNotValidException`

Esta exceção possui o método `getFieldErrors`, que retorna uma lista de objetos `FieldError`. Um objeto deste tipo possui alguns atributos, entre os quais se destaca o atributo `field` (representando o campo da solicitação em que ocorreu o erro) e o atributo `defaultMessage` (representando a mensagem que as anotações de validação (como `@NotNull` ou `@NotEmpty`) devolvem).

O valor destes atributos podem ser resgatados através dos métodos `getField()` e `getDefaultMessage()`.

Exemplo do uso de todas estas anotações, exceções e métodos:

```java
@RestControllerAdvice  
public class GlobalExceptionHandler {  
  
    @ExceptionHandler(MethodArgumentNotValidException.class)  
    @ResponseStatus(HttpStatus.UNPROCESSABLE_ENTITY)  
    public ErroResposta handleMethodArgumentNotValidException(MethodArgumentNotValidException e){  
        List<FieldError> fieldErrors = e.getFieldErrors();  
        List<ErroCampo> listaErros = fieldErrors  
                .stream()  
                .map(fe -> new ErroCampo(fe.getField(), fe.getDefaultMessage()))  
                .collect(Collectors.toList());  
        return new ErroResposta(  
                        HttpStatus.UNPROCESSABLE_ENTITY.value(),  
                        "Erro validacao",  
                        listaErros);  
    }
}
```

Veja que ao passar valores incorretos para os campos `nome` e `dataNascimento` (como nulo e vazio), estes mesmos campos serão listados no corpo da resposta:

![[Pasted image 20250728124433.png]]

# 94. Explorando tipos de validação no Spring

Estas são outras anotações utilizadas para a validação de campos.

- **`@Size(min=3, max=8, message="")`**: define um tamanho mínimo e máximo de caracteres para aquele campo, além de uma mensagem que aparece quando as restrições não são atendidas.
- **`@Past(message="")`**: obriga um campo de entrada relacionado a data estar no passado (não é permitido ser uma data presente ou futura).

# 95. Melhorando a pesquisa de autores com Query By Example

## Classe `Example`

Esta classe é destinada a fazer consultas de modo mais simples do que seria com lógica de programação, query methods ou com `@Query`.

É possível definir como a consulta será feita através do método `Example.of()`, que recebe 2 parâmetros: o primeiro (obrigatório) é um objeto, do tipo de alguma entidade, que possui determinados campos preenchidos com os valores que você deseja pesquisar. Exemplo:

```java
var autor = new Autor();  
autor.setNome(nome);  
autor.setNacionalidade(nacionalidade);
```

Neste exemplo, será pesquisado na entidade Autor os registros que tiverem os mesmos dados no campo `nome` e `nacionalidade`.

Já o segundo parâmetro é opcional e deve ser do tipo `ExampleMatcher`: uma classe destinada a configurar o modo como será feito a comparação entre os dados que você passou (neste caso, dados do `nome` e `nacionalidade`) e as informações no banco.

A classe `ExampleMatcher` disponibiliza os seguintes métodos:

- **`matching()`**: cria uma instância de `ExampleMatcher` para a configuração da comparação entre os dados.
- **`withIgnoreCase()`**: ignora a diferença de letras maiúsculas e minúsculas entre os dados comparados.
- **`withIgnoreNullValues()`**: ignora os campos nulos do objeto passado como primeiro argumento.
- **`withStringMatcher(ExampleMatcher.StringMatcher.CONTAINING)`**: verifica se os caracteres informados estão **contidos** (equivalente ao `like '%texto%'` de SQL) nos dados do banco. Por exemplo: se foi informado 'pe' em um tabela que possui um registro com nome 'pedro' então este registro será selecionado, pois 'pe' está contido em 'pedro'.

Este é um exemplo do uso de `Example` e `ExampleMatcher`:

```java
public List<Autor> pesquisaByExample(String nome, String nacionalidade){  
    var autor = new Autor();  
    autor.setNome(nome);  
    autor.setNacionalidade(nacionalidade);  
  
    ExampleMatcher matcher = ExampleMatcher  
            .matching()  
            .withIgnoreCase()  
            .withIgnoreNullValues()  
            .withStringMatcher(ExampleMatcher.StringMatcher.CONTAINING);  
  
    Example<Autor> autorExample = Example.of(autor, matcher);  
    return this.autorRepository.findAll(autorExample);  
}
```

Em suma, o que este código fará é pesquisar registros na tabela Autor por meio do campo `nome` e `nacionalidade`, desconsiderando case sensitive, valores nulos e levando em consideração caracteres que podem estar contidos dentro de dados armazenados no campo `nome` e `nacionalidade`.

