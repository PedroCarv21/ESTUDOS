
# Análise de Algoritmo

## O que são subrotinas/subprogramas?

Blocos de instruções que realizam tarefas específicas, reduzindo as chances de erro e de complexidade. Outras vantagens são:

- Construção independente.  
- Testes individualizados.
- Reaproveitamento de algoritmos.

A sub-rotina nada mais é do que uma função.

## Como é chamado o acionamento de uma sub-rotina?

Chamada ou ativação.
## Como os valores das variáveis originais podem ser alterados por sub-rotinas?

Através da passagem por referência, onde os endereços de memória das variáveis são acessados diretamente.
## Qual seria a diferença entre uma função e um procedimento?

- **Função:** recebe parâmetros e **retorna um valor** para o programa principal.
- **Procedimento:** recebe parâmetros e **não retorna nenhum valor** para o programa principal.

**OBS.: às vezes, procedimento também pode ser chamado de função.**

## Algumas regras em relação ao vetor?

Entrada e saída de dados manipuladas em um vetor são processados um elemento por vez. Estes processos são executados através de loops de repetição.

### Como deve ser o formato do vetor?

```
tipo < nome_do_vetor > [tamanho] ;
```

## O que é um deslocamento em relação a estrutura de dados?

Quando o acesso aos elementos é direto por meio de um índice. O endereço de memória de um elemento é calculado multiplicando o deslocamento (índice) pelo tamanho do tipo de dado e somando ao endereço base.
## O que são estrutura de dados registros?

Consiste em trabalhar vários dados de tipos diferentes (inclusive os tipos compostos (vetores, matrizes e registros)), em uma mesma estrutura. Essa múltipla alocação de variáveis é chamada de dados compostos heterogêneos, estruturas ou registros, na qual os elementos de um registro são alocados em posições de memória adjacentes (um ao lado do outro).

### Como devem ser declarados os registros?

```
tipo r = registro
     {Descrição dos campos e seus tipos}
   fim registro;
r = REG;
```

Um exemplo mais concreto:

```
tipo r = registro
     texto: NOME;
     real: NOTA1;
     real: NOTA2;
     real: NOTA3;
     real: NOTA4;
  fim registro;
r = ALUNO.
```

### Atribuição de valores

```
FUNC . NOME ← “Joana Curadora”;
FUNC . ENDEREÇO . RUA ← “Avenida das Americas”;
FUNC . ENDEREÇO . NRO← 4200;
FUNC . ENDEREÇO . CEP← 22640102;
FUNC . CIDADE ← “Rio de Janeiro”;
FUNC . ESTADO ← “RJ”;
FUNC . SALARIO ← 1.00;
```

## O que é ponteiro?

Ponteiro é um tipo especial de variável para conter o endereço de memória de outra variável.
## Razões para a utilização de ponteiros

- As funções podem realmente modificar os argumentos que recebem (passagem por referência).
- Criar estruturas de dados complexas, como listas encadeadas e árvores binárias, em que um item deve conter referências a outro.
- Alocar e desalocar memória dinamicamente do sistema.

### Como deve ser feita a declaração?

Quando se declara um ponteiro, deve-se declará-lo com o mesmo tipo (int, char, etc.) do bloco a ser apontado. Por exemplo, se queremos que um ponteiro aponte para uma variável int (bloco de 4 bytes em alguns ambientes), devemos declará-lo como int também.
## Qual o método mais adequado para aplicar a técnica de decomposição de problemas?

É o método Top-down, sendo um quadro geral de um problema complexo e o divide passo a passo em subproblemas menores e mais fáceis de resolver.

![[Pasted image 20260804112040.png]]

## Segundo Moacir, quais características um algoritmo deve possuir?

- Desempenho.
- Simplicidade.
- Clareza (podendo utilizar documentação).
- Segurança.
- Implementação de funcionalidades de acordo com o que foi exigido.
- Modularidade (permitindo a manutenção e o reuso).
- Interface amigável para os usuários.

## Quais recursos computacionais deve ser levada em conta para medir a eficiência?

- Quantidade de espaço de armazenamento utilizado.
- Quantidade de tráfego gerado em redes.
- Quantidade de dados transferidos entre os discos.

## Quais são os dois tipos de complexidade considerados em uma análise de um algoritmo?

- **Espacial:** espaço de memória usado para executar o algoritmo.
- **Temporal:** é o mais usado e pode ser dividido em dois grupos:  
	- Tempo (real) necessário à execução do algoritmo.  
	- Número de instruções necessárias à execução.

## O que é análise assintótica?

É tomado como premissa nessa análise que cada operação leva o mesmo tempo constante e que a memória da máquina é eficiente. A eficiência assintótica descreve a eficiência de um algoritmo quando n torna-se grande.
## Notação Big O

É um cálculo matemático para determinar a **eficiência**, ou seja, a capacidade de execução e o espaço requerido (memória) na medida que o volume de dados de entrada vai crescendo, descrevendo o **pior caso** de desempenho para a execução. Pode-se pensar em uma **notação como uma função.**

Esse tipo de cálculo se enquadra dentro da categoria da **análise assintótica**.

As principais notações de Big O são:

- **O(1) ou constante:** algoritmos que mantém o mesmo tempo de resposta, independente da quantidade de dados de entrada. 
- **O(log n) ou logaritmo:** o crescimento da quantidade de operações é inferior ao volume de dados de entrada. Exemplo é o caso da busca binária: se houver uma lista ordenada de 15 números (de 1 até 15) e preciso encontrar o número 3, eu irei capturar o número do meio (8). Caso não encontre de primeira precisaria dividir a lista novamente até encontrar. Porém, na maioria dos casos seria bem mais rápido ir consultando cada um dos números.
- **O(n) ou linear:** algoritmo cuja a quantidade de operações realizadas aumenta conforme o volume de dados de entrada.
- **O(n log n) ou complexidade loglinear:** significa que o algoritmo executa um trabalho **linear** (_n_) e, para cada parte desse trabalho, há um fator **logarítmico** (_log n_), ou vice-versa. Exemplo é o **Merge Sort** divide uma lista repetidamente em partes menores (log n) até que cada parte contenha apenas um elemento. Em seguida, ele intercala essas partes de forma ordenada O(n), formando sublistas cada vez maiores, até reconstruir a lista original completamente ordenada.
- ![[Pasted image 20260709093223.png]]
- **O(n^2) ou quadrática:** quando a operações realizadas aumentam *quadraticamente* (ou elevado a 2) em relação ao volume de dados de entrada. Um exemplo é o o loop aninhado.
- **O(2^n) ou exponencial:** significa que a cada novo dado adicionado, o o número de operações do programa dobra. Um exemplo é uma função de **fibonacci**:
  
  ```java
  int fibonacci(int n) {
    if (n <= 1)
        return n;

    return fibonacci(n - 1) + fibonacci(n - 2);
}
  ```
  
- **O(n!) ou fatorial:** aparece quando um algoritmo precisa testar todas as possíveis ordens dos elementos. Exemplo: descobrir todas as formas possíveis de colocar 3 pessoas em uma fila. O resultado é 3! = 3.2.1 = 6.

![[Pasted image 20260708193108.png]]

# Como calcular a complexidade de um código?

Os três passos para calcular a complexidade são:

1. Levar em consideração os loops de repetição do código.
2. Verificar a complexidade das funções/métodos do linguagem. Por exemplo: a complexidade do método `size()` é O(1) ou constante.
3. Ignorar as constantes (O(1)) e utilizar o termo de maior grau ou a de maior quantidade de operações realizadas.

Exemplo:

```cpp

int exemplo3(vector<int> v){
	int tamanho = v.size();
	int bla = 0;
	for (int i = 0; i < tamanho; i++){ // O(n)
		for (int j = 0; j < tamanho; j++){ //O (n)
			if (v[i] == v[j]) bla++; // O(1)
		}
	}
	
	// O(n) * O(n) + O(1) = O(n²)
	
	int ble = 0;
	for (int i = 0; i<tamanho; i++){ // O(n)
		if (v[i] == 10){
			ble = 2*ble;
		}
	}
	
	int bli = 0;
	for (int i = 0; i<tamanho; i++){ // O(n)
		if (v[i] == 5){
			ble += 5;
		}
	}
	
	return bla+ble+bli;
}

// O(n²) + O(n) + O(n) = O(n²) + 2.O(n)
```

Analisando cada uma das partes do código você tem:

- `size()`: constante.
- Loops aninhados: cada loop vai percorrer elemento por elemento do array. Então cada loop desse sozinho tem uma complexidade O(n). Como são loops aninhados então a complexidade é O(n) * O(n) ou O(n * 2).

Há então: 
- Uma constante (complexidade O(1))
- Um loop aninhado (O(n * 2))
- Dois loops simples (complexidade de O(n) + O(n)). A razão de haver uma adição e não uma multiplicação é porque um loop não está encadeado em outro loop, portanto, é preciso realizar uma soma apenas.

O resultado seria então: O(1) + O(n * 2) + O(n) + O(n) ou O(1) + O(n * 2) + 2O(n). Como o 3° passo é ignorar constantes (o O(1) e 2 de 2O(n)) e utilizar o termo de maior grau então o resultado é O(n * 2).

Exemplo 2:

```cpp
bool exemplo4(vector<int> v, vector<int> w){
	int tamanho = v.size();
	int tamanho2 = w.size();
	for (int i = 0; i < tamanho; i++){
		for (int j = 0; j < tamanho2; j++){
			if (v[i] == v[j]){
				return true;
			}
		}
	}
	return false;
}
```

Neste caso em especial, o tamanho do vetor v **independe** do tamanho do vetor w. Portanto, não é correto dizer O(n * 2) ou O(n) * O(n), mas sim O(n) * O(m). Resultado: O(n) * O(m).

## Bubble Sort

Um algoritmo com complexidade de tempo O(n^2) responsável por trocar a posição do elemento da esquerda pela posição do elemento da direita, caso o primeiro seja maior que o segundo. No final, todos os elementos do array devem estar ordenados. Exemplo do código:

  ```java
  //código
  ```

**OBS.: no entanto, caso o array já esteja ordenado, esse algoritmo terá uma complexidade O(n).**

### Complexidade de espaço

Bubble Sort é um **algoritmo in-place**, ou seja, não precisa de memória extra proporcional ao tamanho do vetor, utilizando apenas algumas variáveis auxiliares. Por isso, **sua complexidade de espaço é O(1).**

## O que é um componente conjuntivo?

É dito conjuntivo quando ela é sempre executada em qualquer execução do algoritmo. 

## O que são componentes disjuntivos?

É dito disjuntivo quando são executadas dependendo do conjunto entrada de valores do algoritmo.
# Recursividade

## O que é definição recursiva (ou indutiva)?

Descreve uma função ou conceito em termos de si mesmo, utilizando um ponto de parada para evitar repetições infinitas.

Uma definição recursiva é formada por duas partes:
- **Caso base:** A situação mais simples que é resolvida diretamente, sem precisar de mais recursão. É o critério de parada.
- **Passo recursivo:** A regra que divide um problema complexo em uma versão menor e mais simples dele mesmo, aproximando-se do caso base.

## O que é uma sequência?

Uma lista de objetos, enumerados, segundo uma ordem. O denota o k­ésimo elemento da sequência. 

Uma **sequência recursiva** explicita seu primeiro valor (ou primeiros valores) e define outros valores na sequência em termos dos valores iniciais.

## O que é a definição recursiva de função?

Conjunto dos inteiros não negativos dividido em duas partes:

- **Passo básico:** especificar o valor da função em zero.
- **Passo recursivo:** fornecer uma regra para encontrar o valor da função em um inteiro a partir dos seus valores em inteiros menores.

### Exemplo: fatorial

Suponha que f é definida recursivamente por:

$$
\begin{aligned}
f(0)=3 \\
f(n+1)=2⋅f(n)+3
\end{aligned}​
$$

Encontre f(1),f(2),f(3) e f(4).

**Solução**:

f(1)=2f(0)+3=2.3+3=9  
f(2)=2f(1)+3=2.9+3=21  
f(3)=2f(2)+3=2.21+3=45  
f(4)=2f(3)+3=2.45+3=93
## O que é somatório?

Adição de uma sequência de quaisquer tipos de números, chamados parcelas ou somando; o resultado é sua soma ou total. 

O somatório de uma sequência de um único elemento tem como resultado o próprio elemento, enquanto o de uma sequência vazia − sem elementos − resulta, por convenção, em 0.

O somatório é representado pelo símbolo:

$$
\sum_{i\ =\ m}^{n} x_i
$$
​
Sendo que:

- **∑** → símbolo que significa **"some"**.
- **i** → é o **contador/índice**.
- **m** → indica onde o contador começa.
- **n** → indica onde o contador termina.
- **$x_i$** → representa o valor que será somado em cada passo.

### Exemplo

Imagine:

$$
\sum_{i\ =\ 1}^{5} x_i
$$

Lemos:

> "Somatório de xi​, com i variando de 1 até 5."

O i vai assumindo cada valor:

i=1,i=2,i=3,i=4,i=5

Então o somatório vira:

$x_1$​ + $x_2$ ​+ $x_3$ ​+ $x_4$ ​+ $x_5$

## Diferença entre conjunto e sequências

O conjunto é formado por números finitos e **desordenados** enquanto que as sequências/funções possuem uma série de objetos **ordenados**.

## Quais são as duas partes das definições recursivas de conjuntos?

- **Passo básico:** coleção inicial de elementos é especificada.
- **Passo recursivo:** regras para formar novos elementos a partir daqueles que já se sabe que estão no conjunto.

### ##### Exemplo

Considere o subconjunto S dos inteiros definido por:  

- Passo básico: 2∈S  
- Passo indutivo: Se x∈S e y∈S, então x+y∈S

Elementos que estão em S :

- Passo básico: 2  
- Aplicando o passo indutivo/recursivo:

2+2=4 (primeira aplicação do passo indutivo).
2+4=4+2=6 e 4+4=8 (segunda aplicação passo indutivo), e assim por diante.

## O que é recursão?

Relacionada com a definição recursiva, pode ser também compreendido como uma estratégia que envolve quebrar um problema em subproblemas menores e menores, até chegar a um pequeno o suficiente para que possa ser resolvido trivialmente. Geralmente, recursão envolve uma função que chama a si mesma. 

## Diferença entre algoritmo recursivo e iterativo

O algoritmo recursivo chama a própria função dentro dela mesma para que haja um ciclo de repetição, que será concluído quando for alcançado uma determinada condição. Já o algoritmo iterativo utiliza palavras reservadas (`while`, `for`, etc...) para criar esses loops de repetição.

### Qual é o melhor?

Em termos de eficiência, a iteração é mais rápida em muitos casos. Isso porque, em sua forma mais simples e genérica, ela consiste na reexecução de um conjunto de instruções, enquanto que cada chamada recursiva necessita da criação de uma nova sub-rotina em memória − que pode conter endereços de parâmetros e endereço de retorno. 

Portanto, os valores dos parâmetros não podem ser perdidos e a recursão deve funcionar adequadamente para cada chamada como se fosse uma nova função totalmente à parte da que está em execução.

Isso que significa um **procedimento recursivo**, ou seja, aquele em que é possível ter várias chamadas abertas ao mesmo tempo.

**OBS.: Lembre-se de que memória é consumida cada vez que o computador faz uma chamada a uma função. Portanto, com funções recursivas, a memória do computador pode se esgotar rapidamente.**
## Quais são as três leis da recursão?

- **Lei 1 -** Um algoritmo recursivo deve ter um caso básico.
- **Lei 2 -** Um algoritmo recursivo deve mudar o seu estado e se aproximar do caso básico.
- **Lei 3 -** Um algoritmo recursivo deve chamar a si mesmo.

## O que é a recursão em cauda?

Diferente da recursão anterior (chamada de pilha), que acaba criando uma pilha de chamadas da função para que, no fim, seja desempilhado tudo e retornado o valor desejado, a recursão em cauda é um tipo de função que chama a si mesma como a última operação. Nada mais é calculado após essa chamada.

Exemplo de função que utiliza recursão em pilha:

```python
object Factorial {
  def factorial(num: Long): Long = {
    if (num==0) return 1;
    return num * factorial(num-1);
  }

  def main(args: Array[String]): Unit = {
    println(factorial(11_000));
  }

}
```

Perceba que a pilha que começa com `num` igual a 3 e retorna para `num` igual a 3.

```
factorial(num = 3) -> 3 * factorial(2)
factorial(num = 2) -> 2 * factorial(1)
factorial(num = 1) -> 1 * factorial(0)
factorial(num = 0) = 1 (agora a gente desempilha)
factorial(num = 1) -> 1 * 1
factorial(num = 2) -> 2 * 1
factorial(num = 3) -> 3 * 2 = 6
```

Agora esse é um exemplo de função com recursão em cauda:

```python
import scala.annotation.tailrec

object FactorialTail {

  @tailrec
  def factorialTail(num: Long, acc:Long): Long =
    if (num == 0) acc
    else factorialTail(num - 1, acc * num)

  def factorial(num: Long): Long = {
    return factorialTail(num, 1);
  }

  def main(args: Array[String]): Unit = {
    println(factorial(40))
  }

}
```

O resultado é retornado sem precisar desempilhar.

```
factorial(3) -> 
factorialTail(num = 3, acc = 1 * 3) ->
factorialTail(num = 2, acc = 3 * 2) ->
factorialTail(num = 1, acc = 6 * 1) ->
factorialTail(num = 0, acc = 6) -> 6
```

## O que é recursão indireta?

As funções podem ser recursivas (invocar a si próprias) indiretamente, fazendo isso através de outras funções: "P" pode chamar "Q", que chama " R ", e assim por diante, até que " P " seja novamente invocada.
## O que é recursão aninhada?

Uma função recursiva pode receber um argumento que inclui outra função recursiva (algo parecido com o loop aninhado). Exemplo:

```
1  Função ackermann(n: inteiro, m: inteiro)
2  inicio
3      se n = 0 então
4          retorno m + 1
5      senão se n > 0 e m = 0 então
6          ackermann(n - 1, 1)
7      senão
8          ackermann(n - 1, ackermann(n, m - 1))
9      fim se
10 fim
```

Na linha (8), é realizada a recursão aninhada dentro da chamada ackermann ( n−1, ackermann(n−1,ackermann(n,m−1)).