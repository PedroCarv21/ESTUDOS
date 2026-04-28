
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

# Por que, no plano cartesiano, o eixo X é chamado de variável independente e o eixo Y de variável dependente?

Porque o eixo X representa um valor que varia livremente, sem consideração de um valor associado, enquanto o eixo Y é influenciado pelo eixo X. Por exemplo: a altura é influenciada pela idade de uma pessoa, porém a idade independe da altura.

# O que é função?

É uma tabela bem organizada, sendo apresentado os valores de eixo X de um lado e os valores do eixo Y de outro.

| **Idade (x)** | **Altura (y)** |
| ------------- | -------------- |
| 12            | 1,50           |
| 20            | 1,75           |
| 32            | 1,80           |

É chamado de gráfico de função **as retas verticais o tocam em um único ponto.** Exemplo:

![[Pasted image 20260317184809.png]]

Somente o gráfico C não é um gráfico de função, pois a reta vertical toca em mais de um ponto:

![[Pasted image 20260317185254.png]]

# O que é raiz da função em um gráfico?

Também chamado de **zero da função**, é quando a linha toca o eixo X (também chamado de OX). Raízes da função também podem ser descritos da seguinte forma: são os valores de x tais que **f(x) = 0**. Exemplo:

![[Pasted image 20260317191739.png]]

A resposta é 19 raízes, pois a linha do gráfico toca o eixo X 19 vezes.

# O que é função constante?

É quando há um gráfico cuja a linha nunca toca o eixo X:

![[Pasted image 20260317192413.png]]

# O que são valores mínimos e máximos, locais e globais?

Valores máximos e mínimos são pontos extremos de uma função. O **máximo/mínimo local** é o maior ou menor valor em uma vizinhança específica (pico ou vale), enquanto o **máximo/mínimo global** é o maior ou menor valor absoluto em todo o domínio da função.

# O que é função?

Relação matemática entre dois conjuntos, sendo que cada valor de um conjunto possui um único valor correspondente em outro conjunto. Quando um valor de um conjunto possui dois ou mais valores em outro conjunto, **isso já não é uma função.**

![[Pasted image 20260324160930.png]]

**OBS.: a função é representada como $f(x)$, em que $f$ é o nome da função e $x$ é a variável independente.**

# O que é domínio (D), contradomínio (CD) e imagem (Im)?

![[Pasted image 20260324161846.png]]


O **conjunto do domínio** é de onde saem as setas do conjunto X. Por isso o conjunto X é chamado de **domínio**. O conjunto contradomínio é o conjunto Y, pelo simples fato de ele estar recebendo as setinhas. Já o conjunto imagem é formado pelos elementos de Y que recebem as setinhas.

Com base na imagem anterior:

D={1,2,3,4,5,6}
CD = {10,11,12,13,14,15,16}
Im ={10,11,12,13,14,15}​

# Como se dá a relação entre domínio e contradomínio?

Através da função $f(x)$, sendo $x$ um número do domínio e o resultado de $f(x)$ o número do contradomínio ou, como também poderia ser dito, a imagem. Pode-se dizer também  No exemplo da foto anterior, a função era $f(x) = x + 9$.

# Representação de imagens no gráfico

Observe a seguinte imagem:

![[Pasted image 20260324171538.png]]

**OBS.: o domínio é representado pelo $Dom(f)$ e a imagem pelo $Im(f)$.**

Acima do gráfico há 3 condições que determinam qual será o valor da imagem com base no valor de X. 

A primeira condição é que Y = 1 se X < 0, ou seja, qualquer valor negativo. Por essa razão, a linha em negrito presente no gráfico acompanha os números negativos. A linha em negrito também está posicionada em em cima do número 1 da linha vertical Y, pois sempre que X é negativo, o valor de Y (a imagem) é 1.

Assim também ocorrerá com as duas outras regras ($Y = x + 1\ se\ 0 <= x <= 2$ e $Y = 3\ se\ x >= 2$).

# O que é uma função injetora (ou injetiva)?

É aquela em que elementos distintos do domínio possuem imagens distintas no contradomínio. Em outras palavras, cada elemento do conjunto de chegada (imagem) recebe, no máximo, uma "flechada" do conjunto de saída, garantindo que não existam dois diferentes com o mesmo.

![[Pasted image 20260331162817.png]]


Para que a função seja injetora, é necessário que f(a) = f(b) e, portanto, a = b. Por exemplo: a função f(x) = 3x+2. Agora, baseado nessa fórmula, as funções f(a) e f(b) devem ficar da seguinte forma:

f(a)=3a+2 = f(b)=3b+2
f(a)=3a = f(b)=3b

Simplificando ainda mais, é possível dividir cada um dos lados da equação pelo mesmo valor que multiplica a variável a e b:

$$
\frac{3a}{3} = \frac{3b}{3}
$$

O resultado será a = b.


![[Pasted image 20260331164520.png]]

O mesmo poderia ser tentado com x², mas o problema é que tanto -1 quanto 1 elevado ao quadrado, o resultado é 1. Portanto, há dois números que levam a mesma imagem. Por essa razão, não pode ser definido como função injetora.

![[Pasted image 20260331163924.png]]

# O que é função sobrejetora?

É uma função cujo os elementos do contradomínio são referenciados pelos elementos do domínio. Exemplo de função sobrejetora:

![[Pasted image 20260331171152.png]]

Embora ela não possa ser considerada uma função injetora, ela ainda assim é sobrejetora, pois **todo elemento do conjunto B (contradomínio)** é imagem de **pelo menos um elemento de A**.

Já a imagem a seguir não é uma função sobrejetora:

![[Pasted image 20260331171252.png]]

Quando há uma linha no plano cartesiano que mostra a relação de todos os números do eixo Y com o eixo X, se trata de função sobrejetora. Caso a linha exclua certos números, não é possível que seja sobrejetora. Exemplo onde não há uma função sobrejetora:

![[Pasted image 20260331171535.png]]

Essa função não é sobrejetora, pois os valores negativos do contradomínio não interagem com os elementos do domínio.

# O que é uma função bijetora?

É uma função que é injetora e sobrejetora ao mesmo tempo.


# Como é possível definir as seguintes funções?

- **Crescente:** quanto maior o valor de X, **maior** o valor Y.
- **Decrescente:** quanto maior o valor de X, **menor** o valor Y.

Suponha que haja o seguinte gráfico e seja solicitado os intervalos descrente e crescente.

![[Pasted image 20260331190152.png]]

O resultado deveria expresso da seguinte forma:

- **Crescente:** [-3, 0] U [3, 5]
- **Decrescente:** [0, 3] U [5, 6]

# Função periódica

É aquela que repete seus valores em intervalos regulares. Sendo o período = p, f(x + p) = f(x), ou seja, de acordo com uma quantidade p de tempo, o valor f(x) se apresenta.
## O que é período da função?

Parte do gráfico da função que se repete ao longo dos valores de X.


# Quais são os tipos de proposições?

- **Simples (atômicas):** composto por apenas um sujeito e predicado.
- **Compostas (moleculares):** composto por mais de um sujeito e predicado.

# O que é o valor lógico de uma proposição?

São atributos de Verdadeiro (V) ou Falso (F) atribuídos a proposições lógicas. Exemplo: a frase "o número 15 é ímpar", representada pela letra p, poderia ser tratada como V(p) = V.

# Quais são os 3 princípios da lógica matemática?

- **3° excluído:** ou é verdadeiro ou é falso, não há uma terceira opção.
- **Não contradição:** não é possível ser verdadeiro e falso ao mesmo tempo.
- **Identidade:** uma proposição é igual a ela mesma.

# O que são conectivos ou juntores?

São símbolos lógicos para a realização de cálculos entre as proposições. Os principais símbolos são:

- **Conjunção** representado pelo ^ que significa 'e'. Pode também ser representado por um ponto (.), representado uma multiplicação dentro da álgebra booleana:
- ![[Pasted image 20260407183516.png]]
- **Disjunção:** representado pelo v que significa 'ou'. Há dois tipos de disjunção:
	- **Inclusiva:** se uma proposição é verdadeira, isso não impede que a outra também seja verdadeira. Por exemplo: ou Ana é estudante ou Ana é estagiária. As duas proposições podem ser verdadeiras ao mesmo tempo. Na álgebra booleana, é representado por +.
	- **Exclusiva (represtado por <u>v</u> ):** se uma proposição é verdadeira, a outra deve ser falsa. Por exemplo: ou a luz está ligada ou está desligada.
	- ![[Pasted image 20260407175915.png]]
- **Condicional:** representado por uma → que simboliza o **se ..., então**, ou seja, se uma proposição é verdadeira, a outra proposição também deve ser verdadeira. Exemplo: se chover, então a rua ficará molhada.
- ![[Pasted image 20260407180004.png]]
- **Bicondicional:** representado por uma ↔ que smboliza **se, e somente se**. Por exemplo: um número é par se, e somente se, ele for divisível por 2.
- ![[Pasted image 20260407180025.png]]
- **Negação:** representado por ~ ou por ¬. Por exemplo: se a frase "José é engenheiro" é representado por p, então ¬p equivale a "José não é engenheiro". Pode também ser representado por um traço em cima da letra (ex.: $\bar{A}$)
- **NAND:** representado pelo ↑ e significa que a operação booleana que combina AND e NOT, produzindo um resultado falso apenas quando todas as entradas são verdadeiras. Por exemplo: p = "Maria vai ao clube"; q = "Maria vai estudar"; p ↑ q equivale a "Não é verdade que Maria vai ao clube e Maria vai estudar".
- ![[Pasted image 20260407181235.png]]
- **NOR:** representado pelo ↓ e significa que a operação booleana que combina OR e NOT, produzindo um resultado falso apenas quando uma das entradas é verdadeira. Por exemplo: p = "Maria vai ao clube"; q = "Maria vai estudar"; p ↓ q equivale a "Não é verdade que Maria vai ao clube ou Maria vai estudar".
- ![[Pasted image 20260407181154.png]]


# Classificações de proposições lógicas

- **Tautologia:** se seu valor lógico é V, independentemente dos valores lógicos das proposições que a compõem. Exemplo: (¬q∧p)↔(¬p∨¬q)
- **Contradição:** se seu valor lógico é F (falso), independentemente dos valores lógicos das proposições que a compõem. Exemplo: (p∧q)↔( p∨¬q)
- **Contingência:** toda proposição composta que não é tautologia nem contradição.

# O que é equivalência lógica?

Equivalência lógica ocorre quando duas proposições compostas possuem tabelas-verdade idênticas, significando que expressam a mesma ideia e possuem os mesmos valores de verdade (ambas verdadeiras ou ambas falsas). Representada pelo símbolo “↔”, permite substituir uma proposição por outra sem alterar o sentido lógico. 

## Exercício

Muitas vezes, a demonstração de uma proposição do tipo P→Q não possui uma abordagem simples. Entretanto, há proposições logicamente equivalentes (mesma tabela-verdade) cuja demonstração pode ser mais facilmente abordada.  
 

Dadas as proposições:

  
I. ∼Q→∼P  
 
II. P ou ∼Q  
  
III. ∼P ou Q  
 

Entre essas três proposições, quais são equivalentes à proposição P→Q ?

Resposta:

Basta analisar as tabelas-verdade das proposições envolvidas:

![[Pasted image 20260421120259.png]]
# Regras de inferência

## Regras de adição (AD)

$$
\frac{p(premissa)}{p\ v\ q(conclusão)}
$$

## Regra da simplificação (SIMP)

$$
\frac{p ∧ q}{p}
$$
## Modus ponens (MP)

$$
\begin{align}
p → q \\
\frac{p}{q}
\end{align}
$$
## Modus tollens (MT)


$$
\begin{align}
p→q \\
\frac{∼p}{∼q}
\end{align}
​$$
 
​
## Silogismo hipotético (SH)

$$
\begin{align}
p→q \\
\frac{p→r}{q→r}​​
\end{align}
$$
## Silogismo disjuntivo (SD)

 $$
\begin{align}
p ∨ q \\
\frac{∼ p}{q} \\
p ∨ q \\
\frac{∼ q}{p}
\end{align}
​$$

Exemplo:

p: A temperatura está baixa. 
q: Há nevoeiro. 
p ∨ q: A temperatura está baixa ou há nevoeiro. 
∼p: A temperatura não está baixa.

Conclusão:

q: Há nevoeiro.
## Regra da conjunção (CONJ)

$$
\begin{align}
p \\ 
q \\
p∧q
\end{align}​
$$




# Como verificar a validade de um argumento?

As seguintes proposições lógicas formam um conjunto de premissas de um argumento:

```
Se Pedro não é músico, então André é servidor da ABIN. 
Se André é servidor da ABIN, então Carlos não é espião. 
Carlos é um espião.
Conclusão: Pedro é músico.
```

## 1° passo: Consideramos todas as premissas e a conclusão verdadeiras.

```
1. Se Pedro não é músico, então André é servidor da ABIN. (V)  
     
2. Se André é servidor da ABIN, então Carlos não é espião. (V)  
     
3. Carlos é um espião. (V)

Conclusão: Pedro é músico (V)
```

Agora, começaremos a analisar a partir da proposição simples “Carlos é um espião”. Depois, é necessário prosseguir de baixo para cima uma análise da relação entre as proposições por meio da tabela verdade. Por exemplo: se a última proposição `Carlos é um espião.` é verdadeira então a penúltima proposição `então Carlos não é espião` deve ser falsa. Para que a premissa `Se André é servidor da ABIN, então Carlos não é espião` seja verdadeira, é necessário que `André é servidor da ABIN` seja falso, pois F → F é verdadeiro na tabela verdade. E assim por diante. Resultado:

```
Se Pedro não é músico (F), então André é servidor da ABIN (F). V
Se André é servidor da ABIN (F), então Carlos não é espião (F)⋅(V).
Carlos é um espião. (V)
Se Pedro não é músico (F), então André é servidor da ABIN (F). V
Se André é servidor da ABIN (F), então Carlos não é espião (F)⋅(V).
Carlos é um espião. (V)
```

Logo, concluímos que Pedro é músico. O argumento é válido.

# Qual a diferença entre proposição e sentença aberta?

- **Proposição:** sentença declarativa que pode ser classificada com verdadeira ou falsa. Exemplo: O Sol é uma estrela.
- **Sentença aberta:** sentença que depende de um valor x para que ela seja classificada como verdadeira ou falsa. Exemplo: x² - 5x + 6 = 0. **Conjunto verdade** é o conjunto de valores que tornam esse sentença verdadeira, sendo representado por $Vp$. Neste caso, apenas o valor 2 tornaria essa sentença verdadeira. É possível utilizar também uma frase como, por exemplo, 'Ela é uma boa professora'. A variável 'Ela' também pode ser alterada para se tornar verdadeira ou falsa.

# O que é conjunto universo (ou domínio da sentença aberta)?

Representado pela letra U, é o conjunto que contém todos os elementos possíveis em um determinado contexto ou situação de estudo, servindo como base para a definição de outros subconjuntos.

Exemplo: considere a expressão x + 15 = 8 uma sentença aberta do conjunto dos números inteiros (Z).

Resultado de x é -7 e faz parte dos números inteiros. Portanto, uma sentença verdadeira.

# Quais são as duas condições que uma sentença aberta pode assumir?

- **Universal:** quando **todos** os elementos de um determinado conjunto implicam em uma coerência caso sejam aplicados naquela sentença. Por exemplo: seja 2x + 1 > x uma sentença aberta no conjunto de números naturais (N). O resultado da equação é x > -1, portanto, qualquer número natural pode representar x.
- **Possível:** quando **alguns** dos elementos de um determinado conjunto implicam em uma coerência caso sejam aplicados naquela sentença. Por exemplo: seja 2x + 3 > 6 uma sentença aberta no conjunto de números naturais (N). O resultado é x > 1,5, portanto, apenas os números inteiros a partir do dois em diante tornam a sentença aberta verdadeira.
- **Impossível:** quando a sentença aberta, mesmo sem apresentar o valor, já demonstra uma inconsistência. Por exemplo: x + 3 = x.

# Exemplo de sentença aberta com duas variáveis

Considere a sentença aberta x+2>y em A×B, em que A={1,2,3} e B={4,5}. O conjunto verdade é:

$$
Vp​={(x,y)∈A×B∧x+2>y}={(3,4)}
$$
Isso pode ser lido da seguinte forma: Vp é o conjunto dos valores x e y pertencentes aos conjuntos A e B, tais que x mais dois é maior que y, e esse conjunto é igual a 3 e 4.

Ou seja, se eu tomar x igual ao número 3 do conjunto A e o y igual ao número 4 do conjunto B, o reusltado é:

$$
\begin{aligned}
x + 2 > y \\
3 + 2 > 4 \\
5 > 4
\end{aligned}
$$


# O que é predicado?

São expressões lógicas que atribuem propriedades ou características a variáveis, formando sentenças abertas que se tornam proposições verdadeiras ou falsas quando as variáveis são substituídas por elementos específicos. Na lógica dos predicados, essas expressões são representadas por símbolos predicativos, como p,q,r, e variáveis, como x,y,z.

# Como se dá as operações lógicas com sentenças abertas?

## Negação

Se a sentença aberta diz p(x) :  x + 2 < 6 então a negação dessa sentença seria p(x): x + 2 >= 6. Neste caso, o Vp = {4, 5, 6, ...}
## Conjunção

É a interseção entre dois conjunto verdades. Por exemplo: considerando o conjunto de números inteiros, Vp de p(x): x2+6x+5=0 é {-1, -5} e o Vp de q(x): x2+5x=0 é {0, -5}. Qual seria a conjunção Vp^q ? {-5} , pois é o elemento comum entre os dois conjunto verdades.
## Disjunção

Seriam todos os elementos presentes nos dois conjunto verdades. No caso do exemplo anterior, Vpvq é {-5, -1, 0}.

## Condicional

Para calcular p(x) → q(x) é possível utilizar, em vez disso, a fórmula ¬p(x) V q(x). Por exemplo:

p(x): x + 1 < 6; portanto ¬p(x): x + 1 >= 6. O conjunto verdade é N - {1, 2, 3, 4}
q(x) x é divisor de 10. O conjunto verdade é {1, 2, 5, 10}

¬p(x) V q(x) é N - {3}

## Bicondicional

Vp(x) ⇔ Vq(x) equivale a Vp→q​ ∩ Vq→p​.


# Como descrever a relação entre uma sentença e um conjunto

Exemplo de sentença e de conjunto: 
p(x): x² > 4
A = {3, 4, 5, 6, 7}

Neste caso todos os elementos de A podem ser aplicados na sentença para que ela se torne verdadeira. Uma forma de dizer isso é: Vp = A. 

Outra forma de dizer isso é através de uma sentença quantificada:  ∀x ∈ A: x² > 4. Isso pode ser lido como: para todo elemento que pertence ao conjunto A, a sentença x² > 4 é verdadeira. Esse ∀ é descrito como **quantificador universal**. Outras formas de dizer que para todo x,p(x) é verdadeira:

- (∀x∈A)(p(x))
- ∀x∈A, p(x)
- ∀x∈A: p(x)

Agora se o conjunto A fosse {0, 1, 2, 3, 4}, então a relação deveria ser expressa como Vp = {3, 4} ou 
Ǝx ∈ A: x² > 4. Isso pode ser lido como: para alguns elementos que pertence ao conjunto A, a sentença x² > 4 é verdadeira. Esse Ǝ é descrito como **quantificador existencial**.

- (Ǝx∈A)(p(x))
- Ǝx∈A, p(x)
- Ǝx∈A: p(x)

Agora se o conjunto A fosse {-1, 0, 1, 2, 3}, então a relação deveria ser expressa como Vp = {3} ou Ǝ! ∈ A: x² > 4. Isso pode ser lido como: apenas um elemento que pertence ao conjunto A, a sentença x² > 4 é verdadeira.

# O que são variáveis ligadas e livres

- **Ligada:** aquela variável relacionada a um conjunto.
- **Livre:** aquela variável que não está relacionada a nenhum valor ou conjunto, ou seja, totalmente desconhecida.

# Como funciona a negação de proposições?

A negação implica alterar o 'todo' por 'algum' (ou vice-versa) e o cópula 'é' por 'não é'

Exemplo: 

Proposição: Todo computador da Apple é bom.
Negação: pelo menos um computador da Apple não é bom

## Em fórmulas matemáticas

Aqui, a negação trocará o ∀ por Ǝ e o >= por < ou <= por >.

Exemplo:

p(x): (Ǝx ∈ N)(x + 1 > 0)

Negação:

~p(x): (∀x ∈ N)(x + 1 <= 0)

Exemplo 2:

(Ǝx)(x + 3 = 0)
(∀x)(x + 3 ≠ 0)

Exemplo 3:

(∀x ∈ A)(p(x)) ^ (Ǝx ∈ A)(q(x))
(Ǝx ∈ A)(~p(x)) v (∀x ∈ A)(~q(x))

# Como são definidas as afirmações na linguagem Prolog?

Deve seguir a seguinte estrutura:

predicado (objeto 1, objeto 2, ...).

Exemplo:

amigo(paulo, carlos) significa que Paulo é amigo de Carlos.

É possível ter apenas um único objeto:

engenheiro(luis). Significa: Luis é engenheiro.

Caso se trate de uma pergunta, é necessário colocar uma '? -' antes:

? – carioca(carlos).

Significa: Carlos é carioca?

**OBS.: tudo deve estar com letra minúscula.**

# O que é demonstração por vacuidade?

A demonstração por vacuidade (ou verdade vazia) é um método lógico onde se prova que uma implicação "p → q" (se p, então q) é verdadeira simplesmente mostrando que o antecedente (p) é falso.

# O que é redução ao absurdo ou contradição?

Consiste em duas coisas:

- Naquela estratégia utilizada por Sócrates, que mostrava as implicações da tese defendida pelo o oponente, sendo que estas implicações apontava para um absurdo.
- O princípio de não contradição defendido por Aristóteles.