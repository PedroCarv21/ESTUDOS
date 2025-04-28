
## Aula 1: O que são testes unitários?

Os testes são representados por métodos criados com o objetivo de validar o funcionamento de uma parte do código do seu programa. 

Alguns testes unitários receberão parâmetros válidos enquanto outros receberão intencionalmente parâmetros inválidos para ver se em ambos os casos é gerado o resultado esperado.

**OBS.: deve ser criado um teste unitário para uma determinada funcionalidade ou método e não para diversos métodos.**

Os testes unitários são desenvolvidos através da ferramenta **JUnit**.

Quando o teste for executado e ele ocorrer como esperado então será marcado com a cor verde, caso contrário será marcado com a cor vermelha.

## Aula 2: Sobre testes de regressão

São testes criados para verificar se as alterações feitas nas funcionalidades não produziram resultados inesperados. Caso tenha produzido, isso será chamado de **regressão**.

## Aula 4: Teste do código de forma isolada

Em muitos casos ocorrerá de um método, que precisa ser testado, possuir dependências, ou seja, instâncias de outras classes que fazem o método funcionar. Isso não é algo bom, pois é desejado verificar apenas os erros que podem ou não acontecer com os métodos, e não as dependências presentes no método.

Por exemplo, veja o seguinte código:

```java
public void checkout(Cart cart){
	PayoutProcessor payoutProcessor = new PayoutProcessor();
	payoutProcessor.proccessPayment(cart);
}
```

Entenda que, para o método checkout funcionar, é necessário também o funcionamento da dependência payoutProcessor, caso contrário, não será possível realizar o checkout.

A solução para isso é a injeção de dependências, ou seja, um objeto do tipo PayoutProcessor será passado como argumento:

```java
public void checkout(Cart cart, PayoutProcessor payoutProcessor){
	payoutProcessor.proccessPayment(cart);
}
```


## Aula 10: Criando um JUnit Test Case

Clique com o botão direito em um pacote da pasta **src/test/java** do projeto -> New -> JUnit Test Case

A classe gerada deverá gerar um código mais ou menos assim:

```java
package br.com.erudio;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;

class FooBarTest {

	@Test
	void test() {
	
		fail("Not yet implemented");
	
	}
}
```

## Aula 12: Exemplo de testes

No pacote **src/main/java** é onde se encontram as classes comuns e no caminho **src/test/java** é onde se encontram as classes de teste. 

No caso da classe comum, este é um de classe que realiza as principais operações aritméticas:

```java
public class SimpleMath {

	public Double sum(Double firstNumber, Double secondNumber) {
	
		return firstNumber + secondNumber;
	
	}
	
	public Double subtraction(Double firstNumber, Double secondNumber) {
	
		return firstNumber - secondNumber;
	
	}
	
	public Double multiplication(Double firstNumber, Double secondNumber) {
	
		return firstNumber * secondNumber;
	
	}
	
	public Double division(Double firstNumber, Double secondNumber) {
	
		return firstNumber / secondNumber;
	
	}
	
	public Double mean(Double firstNumber, Double secondNumber) {
	
		return (firstNumber + secondNumber) / 2;
	
	}
	
	public Double squareRoot(Double number) {
	
		return (Double) Math.sqrt(number);
	
	}

}
```

Esta classe possui o nome de SimpleMath, portanto, deverá ser nomeado a classe que irá testar os métodos de SimpleMath como SimpleMathTest:

```java
class SimpleMathTest {

	@Test	
	void testSoma() {
	
		SimpleMath simpleMath = new SimpleMath();
		
		Double actual = simpleMath.sum(6.5, 3.5);
		
		Double expected = 10.0;
		
		Assertions.assertEquals(expected, actual);
	
	}
}
```

A classe de teste possui um método chamado testSoma (poderia ser qualquer nome) com uma anotação **@Test**, indicando que este método será executado como um teste.

É então criada uma instância de SimpleMath para que possa ser utilizado o seu método sum(). 

O resultado esperado por esse método é 10.0 (por isso a variável expected). Para confirmar o funcionamento do método sum(), será utilizado o método **assertEquals()** que compara o valor esperado (neste caso 10.0) com o valor que o método sum() de fato retorna.

## Aula 13: Produção de mensagens

É possível passar uma mensagem, como argumento de assertEquals(), que será devolvida em caso onde o resultado esperado não seja igual com o resultado real retornado pelo método. Exemplo:

```java
Assertions.assertEquals(expected, actual, String.format("%.1f isn't equal to %.1f", expected, actual));
```

Assim que executar o teste, será possível ver a mensagem (em caso de erro) clicando em **Show Stack Trace in Console View**:

![[Pasted image 20250423111449.png]]

## Aula 14: Outros métodos asserts

Além da comparação entre o valor esperado e o valor retornado pelo método, há também outros tipos de validação através dos seguintes métodos:

- **assertNotEquals()**: verifica se o valor esperado é diferente do valor retornado pelo método.
- **assertNull()**: verifica se o valor passado não é nulo.





### junit

- Comentários com as anotações:
	- {@link ...}
	- @return
	- @param
	- @author
	- @date
- **@Test**
- @Before
- @After
- Métodos como:
	- assertThat()
	- **assertEquals()**
	- is()
	- assertFalse()
	- assertNull()
	- assertTrue()

### MOCKITO

- Classes:
	- TesteCase
	- Test
	- TestSuite
- Anotações:
	- @ExtendWith(MockitoExtension.class)
	- @Mock
	- @InjectMocks
- Método:
	- when()
	- thenReturn()
	- Assertions.assertEquals()