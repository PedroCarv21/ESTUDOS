
# Teoria dos conjuntos

## O que é?

É uma linguagem da matemática utilizada para descrever conjuntos de objetos. A teoria dos conjuntos trata dos seguintes temas:

- **Representação dos conjuntos:** como representar objetos de um conjunto (através de certas figuras ou desenhos).
- **Intervalos:** conjunto de números (geralmente do conjunto de números reais) definidos pela ordem "menor que / maior que".
- **Operações entre conjuntos:** as diversas interações que podem ocorrer entre dois (ou mais) conjuntos como, por exemplo, a interseção.


# Representação dos conjuntos

A representação dos conjuntos é realizada através da inclusão, por exemplo, de números dentro de um figura geométrica (como um círculo):

![[Pasted image 20260210212940.png]]

Um conjunto também é representado através de { } e a representação do conteúdo do conjunto pode ser feita de duas maneiras:
## Explícita

É informado quais são exatamente os números daquele conjunto. Com base no exemplo anterior:

$$
\{1; 2; 3; 4; 5\}
$$

> [!NOTE]
> Utilize ponto e vírgula em vez de virgula para separar os elementos do conjunto, pois, caso contrário, poderá criar uma confusão quando os elementos forem números decimais.

## Implícita

Descreve os objetos daquele conjunto através de uma propriedade. No exemplo anterior, os objetos poderiam ser descritos implicitamente da seguinte forma:

$$
\{A ∈ N\* | 0 < A < 6\}
$$

Pode ser lido da seguinte forma: o conjunto de A pertence ao conjunto de números naturais não nulos, **tal que** (representado pela barra | ) o conjunto de A é maior que 0 e menor que 6. Há outras duas formas de representar implicitamente este mesmo conjunto:

$$
\{ A | A ∈ N\*\ e\ 0 < A < 6 \}
$$
$$
\{ A\ |\ A\ \text{é natural não nulo e}\ 0 < A < 6 \}
$$

## Intervalos

Os intervalos entre o conjunto de números podem ocorrer de 3 formas:

- **Reais entre dois números dados.**
- **Reais além de um número dado.**
- **Reais aquém de um número dado.**

### Representação de intervalos em uma reta

Nessa representação, há duas formas de representar a extremidade do conjunto:

- **Extremidade excluída/aberta:** quando o número não está dentro do conjunto.
- **Extremidade incluída/fechada:** quando o número está dentro do conjunto.

Exemplo da seguinte reta:

![[Pasted image 20260210224619.png]]

Suponha que o número -6 está excluído do conjunto e o -4 está incluído. Portanto, a representação poderia ser feita da seguinte forma:

$$
] -6; -4]
$$

O colchete invertido (que também pode ser usado parênteses) significa que ele está excluído enquanto que o colchete normal significa que ele está incluído. Outra forma de representar as extremidades é esta:

![[Pasted image 20260210225037.png]]

A seta e a circunferência (em cima do número -6) indicam que o número está excluído enquanto que a reta e o ponto (em cima do número -4) indicam que o número está incluído.

A representação implícita dos objetos do conjunto ficariam da seguinte forma:

$$
\{X ∈ R\ |\ -6 < X <= -4\}
$$

### Intervalo ilimitado

São intervalos referente ao infinito. Por exemplo:

![[Pasted image 20260210233007.png]]

Neste caso, esse intervalo poderia ser representado como:

$$
]1; +∞[
$$

### Módulo

O módulo de um número é a distância de um número até o zero na reta numérica. Por exemplo:

![[Pasted image 20260211183734.png]]

Qual seria a distância entre o -3 e o zero? A distância seria 3 (este é o módulo de y). Já o módulo de x seria 4. Para representar de forma algébrica, coloque o número (ou a letra que o representa) entre duas linhas verticais (ex.: | y | ). Uma das formas de representar o cálculo do módulo é a seguinte: 

$$
|y| = \sqrt{y²}
$$

Independente se o número y for positivo ou negativo, o resultado será o mesmo módulo. Por exemplo, seja a raiz quadrada de 3 (ou -3) elevado ao quadrado, o resultado para ambos os casos é 3.

E qual seria o módulo de x - y ou | x - y | ? O resultado seria 4 - (-3) = 7. Esse valor representa a distância entre x e y.

## Operações entre conjuntos

As possíveis operações entre conjuntos são:

### Interseção

Refere-se aos objetos que dois conjuntos tem em comum. Exemplo:

![[Pasted image 20260211191415.png]]

Os objetos que o conjunto X e Y tem em comum são: {g; e; f}. A interseção é representada pelo ∩.
### União

É a soma dos objetos pertencentes a dois conjuntos. Exemplo:

![[Pasted image 20260211191536.png]]

A união entre o conjunto X e Y é: {a; b; c; ...; k}. A união é representado pelo U.
### Diferença

É a eliminação dos objetos de um conjunto que são comuns a outro conjunto. Exemplo:

![[Pasted image 20260211191837.png]]

Os objetos que ambos os conjuntos tem em comum são {e; f; g}, portanto X - Y é igual a {a; b; c; d}.

### Exercício

Dado os conjuntos:

A = [-3; 2]
B = ]-∞; 1]
C = [-1; 4[

Determine quantos são os números inteiros do conjunto X =  (A ∩ B) U C.

**Resposta:**

Na seguinte imagem, o conjunto A é representado pela cor azul, conjunto B pela cor verde e o conjunto C representado pela cor amarela:

![[Pasted image 20260211221240.png]]

A interseção entre A ∩ B = {-3; -2; -1; 0; 1; 2}

Já a união entre o conjunto anterior (A ∩ B) e o conjunto C seria dos números a partir de -3 até 3, pois o número do conjunto C está excluído. Portanto, X = {-3; -2; -1; 0; 1; 2; 3}

# Conjunto de números

- **Naturais (ℕ):** números utilizados para contar. **Alguns incluem o número 0 e outros não.**
- **Inteiros (ℤ):** números naturais e também negativos.
- **Racionais (ℚ):** números inteiros e aqueles que podem ser escritos como fração.
- **Irracionais (I):** somente aqueles que não podem ser escritos como fração. Exemplo é o π.
- **Reais (ℝ):** inclui os números racionais e irracionais.

![[Pasted image 20260211225359.png]]

# Princípios de contagem

Este princípio é formado por outros princípios:

- **Princípios básicos**
	- **Adição:** a adição auxiliará em como contar a união de dois ou mais conjuntos de objetos. No caso dos conjuntos, é apresentado as seguintes fórmulas para descobrir a união entre dois conjuntos:
		- n(A U B) = n(A) + n(B) - (A ∩ B)
		- n(A U B) = n(A) + n(B) se (A ∩ B) for vazio, ou seja, não há uma interseção entre os conjuntos.
	- **Multiplicação:** a multiplicação auxiliará em descobrir quantas combinações possíveis entre os objetos podem ser feitas. Exemplo: se eu tenho 4 calças e 3 camisas, de quantas maneiras eu posso me vestir? 4 x 3 = 12.
	- **Casa dos pombos/gavetas**: é baseado no seguinte conceito: se você quer abrigar 10 pombos com 9 casas, a conclusão é que 2 pombos deverão ficar na mesma casa. Outro exemplo: a fração 1/7 produz uma dízima periódica com somente 6 números diferentes após a vírgula (0,142857). Se alguém quiser que essa mesma dízima tenha 7 (ou mais) números após a vírgula, a conclusão é que dois números terão de ser iguais
- **Agrupamento simples:** oferece três tipos de agrupamentos (permutação, combinação e arranjo) para solucionar questões de contagem que são bastante comuns.

## Exercício

Determine quantos são os números de 3 algarismos **distintos** que podem ser formados com os algarismos de 0 à 6.

**Resposta:**

Deve-se determinar a quantidade de números que cada casa pode ter:

- **Centena:** não é possível utilizar o 0, pois aí não seria uma centena, mas uma dezena. Portanto, é possível apenas 6 números (excluindo o 0).
- **Dezena:** aqui é possível utilizar o número 0 (logo 7 opções), porém não mais o mesmo número escolhido na casa da centena. As opções são 6.
- **Unidade:** já não é possível escolher nem o número da dezena e nem da centena. Portanto, apenas 5 opções.

O cálculo então fica 6 x 6 x 5 = 180 possibilidades de criar um número de 3 algarismos distintos com números de 0 à 6.

# Agrupamento simples

Envolve a seleção de elementos de um conjunto sem repetição e sem restrições adicionais. O agrupamento simples se divide em dois tipos:

## Combinação simples (ordem NÃO importa)

Quando queremos apenas formar grupos, e a ordem dos elementos não altera o grupo. Exemplo: Formar uma comissão com 3 pessoas dentre 5.

A fórmula é:


$$
C(n,k) = \frac{n!}{k!(n - k)!}
$$

Nesta fórmula, $n$ representa o total de elemento e $k$ o tamanho do grupo. Portanto:

$$
\frac{5!}{3!2!}
$$

O resultado seria 120 / 12 = 10
## Arranjo simples (ordem IMPORTA)

Usamos quando a posição dos elementos faz diferença. Exemplo: escolher presidente, vice e secretário entre 5 pessoas.

A fórmula é essa:

$$
A(n, k) = \frac{n!}{(n-k)!}
$$

Portanto:

$$
A(5, 3) = \frac{5!}{(5-3)!}
$$

O resultado é 120 / 2 = 60

### Permutação

Diferente do arranjo, a permutação é quando o total de elementos equivale ao tamanho do grupo. Portanto, a fórmula é simplesmente $n!$. Exemplo: como organizar 3 livros diferentes em uma prateleira. O cálculo seria $3! = 6$.

# Comparação clara

|Situação|Usa todos os elementos?|Ordem importa?|
|---|---|---|
|Permutação|✅ Sim|✅ Sim|
|Arranjo|❌ Só parte|✅ Sim|
|Combinação|❌ Só parte|❌ Não|

# Agrupamentos especiais

Diferente do agrupamento simples, o agrupamento especial possibilita que os elementos sejam repetidos no mesmo agrupamento. Estes são os casos de agrupamentos especiais:

## Permutação com repetição

É quando queremos contar de quantas maneiras podemos organizar elementos, **sabendo que alguns deles são iguais**. 

Exemplo: Quantas palavras diferentes podemos formar com a palavra **MATEMÁTICA**?

**Resposta:**

É necessário saber:

- A quantidade total de letras (neste caso é 10).
- A quantidade de vezes que cada letra se repete ('A' se repete 3 vezes; 'M' duas vezes e 'T' duas vezes ).

Portanto:

$$
\frac{10!}{3!2!2!}
$$

O resultado é 151.200.

## Combinação com repetição

é quando queremos escolher elementos de um conjunto **sem se importar com a ordem** e **permitindo repetir elementos**.

Exemplo: Suponha que uma loja possui tabletes (barras) de chocolate de **três** marcas diferentes e você deseja comprar **oito** tabletes. De quantas formas diferentes podem ser escolhidos os tabletes em sua compra?

**OBS.: a resposta a seguir visa utilizar de um macete para chegar a uma conclusão (embora não faça muito sentido a maneira em que se chega ao resultado).**

**Resposta:**

A quantidade de tabletes (T) é 8 e há 3 opções de chocolate, portanto, é possível dividir os tabletes da seguinte forma:

TTT - TTT - TTTT

A quantidade de traços que separam os conjuntos de tabletes por marca é sempre, independentemente da maneira como os tabletes são distribuídos:

TTTTTTT - T - 

Sempre haverá a mesma quantidade de traços nessa questão.

Quantos traços existem? Dois.

Somando esse dois com a quantidade de tabletes, o resultado é 10. A partir daí, é possível chegar a uma fórmula:

$$
\frac{10!}{8!2!}
$$

O resultado é 45.

# Conceitos relacionados a gráficos 

## Reta real

![[Pasted image 20260311175615.png]]

É representado por uma linha vertical que expressa a sequência de números reais, sendo o número 0 é chamado de **origem** e, partir dele, será feito todas as dimensões.

## Como representar um intervalor de números na reta real?

Exemplo: uma reunião ocorreu das 17h às 20h. Represente na real o intervalo de tempo da reunião.

**Resposta:**

Essa é a representação implícita do conteúdo do conjunto:

$$
{x ∈ R\ |\ 17 \le x \le 20}
$$

Ou seja, por conta dos sinal $\le$ , isso significa que os números 17 e 20 estão incluídos dentro do conjunto. A representação na reta real se daria dessa forma:

![[Pasted image 20260311181023.png]]

Devem ser utilizados um ponto em cima dos dois números para indicar a sua inclusão e também esse tracejado (//////) informando que os números entre esses dois intervalos também estão dentro do conjunto.

# Classificação dos intervalos

![[Pasted image 20260311181535.png]]

- **Intervalor fechado**
- **intervalo semiaberto (ou semifechado)**
- **intervalo semiaberto (ou semifechado)**
- **Intervalo aberto**
- **Semirreta à direita com origem em a**
- **Semirreta à direita sem incluir a**
- **Semirreta à esquerda incluindo b**
- **Semirreta à esquerda sem incluir b**
- **Conjunto de números reais**

# Plano cartesiano

![[Pasted image 20260311204301.png]]

