# Pesquisa Operacional Como Ferramenta de Apoio
## O que é pesquisa operacional (PO)?

É uma área que se dedica a aplicar métodos matemáticos para otimizar a tomada de decisões com problemas complexos.

## Quais são os 6 passos principais da metodologia da PO?

- **Definição do problema**
- **Construir o modelo:** traduzir um problema do mundo real para a linguagem matemática, criando equações que representem os objetos do mundo real (ex.: carros, distancias, etc.).
- **Solução do modelo:** calcular essas expressões matemáticas através do software.
- **Análise da solução:** verificar se a solução obtida está realmente condizente com a realidade concreta.
- **Implementação da solução:** aplicar a solução dentro da organização e monitorar o resultado.
- **Validação da solução:** verificar se os resultados esperados foram atingidos.

## Quais são algumas das técnicas utilizadas pela PO?

- **Teoria das filas:** otimiza sistemas de espera como filas em banco e supermercados.
- **Programação linear:** otimiza o uso de recursos em problemas com variáveis reais e relações lineares (significa que, quando uma variável sofre uma alteração, a outra também se altera em uma proporção constante e fixa).
- **Simulação:** cria uma programa para testar diferentes cenários, permitindo analisar o comportamento desses cenários ao longo do tempo.
- **Redes de Petri:** é uma técnica de modelagem que permite a representação de sistemas, utilizando como alicerce uma forte base matemática. Exemplo:
  
  Imagine que você quer organizar o funcionamento de uma estação de trem. Há pessoas esperando na plataforma, trens chegando, passageiros embarcando e desembarcando. Tudo precisa acontecer em uma ordem correta para evitar confusão.
  
  Uma **Rede de Petri** é uma forma de representar esse tipo de sistema, mostrando **quem pode fazer o quê, quando e sob quais condições**.

## Quais áreas a PO é aplicada?

- **Indústria:** define a quantidade e o momento ideal de produção de cada item.
- **Logística:** irá tratar do gerenciamento da entrega, considerando fatores como tempo, distância e capacidade dos veículos.
- **Saúde:** é utilizado para o agendamento de consultas, otimizando o calendário de consultas e exames para reduzir o tempo de espera dos pacientes.
- **Finanças:** utiliza a PO para definir a melhor alocação de recursos em diferentes investimentos, considerando risco, retorno e objetivos do investidor.

## O que é abordagem científica para tomada de decisão?

Ela utiliza de um método científico para análise de dados e escolha de decisões. Esse método se apoia em cinco fundamentos:

- Definição clara do problema.
- Coleta e validação dos dados.
- Desenvolvimento de sistemas.
- Identificação de alternativas (identificar e avaliar as diferentes alternativas de solução).
- Escolha da melhor solução.

## Quais são os conceitos matemáticos utilizados na modelagem?

- **Álgebra linear:** permitindo a representação de relações entre variáveis, através de vetores e matrizes, e a manipulação de sistemas.
- **Cálculo diferencial e integral:** fornece ferramentas para analisar funções (relação matemática entre as variáveis), calcular taxas de mudança e otimizar soluções.
- **Programação linear:** técnica matemática usada para maximizar lucro ou minimizar custos, composta por três elementos principais: variáveis de decisão, função objetivo e restrições. Ela serve para encontrar a melhor solução em problemas práticos de recursos limitados, logísticas e produção.
- **Probabilidade e estatística:** permitem analisar a incerteza e o risco, estimar parâmetros e fazer previsões. 

## Qual a forma da modelagem linear?

$$
Ax = b
$$

Sendo:

- A = matriz de coeficientes.
- x = vetor de variáveis.
- b = vetor de termos constantes.

## Quais são alguns modelos probabilísticos bastante utilizados?

- **Modelos de regressão:** Relacionam uma variável dependente a uma ou mais variáveis independentes, considerando a aleatoriedade dos dados.
- **Modelos de cadeias de Markov:** Descrevem a evolução de um sistema ao longo do tempo, considerando a probabilidade de cada estado.
- **Processos estocásticos:** Representam a evolução de variáveis aleatórias ao longo do tempo.

## Quais são as três perguntas que devem ser feitas em PO?

- Os dados são confiáveis?
- O modelo se comporta como esperado?
- A solução funciona ou não no mundo real?

## O que é um projeto piloto ou projeto modelo?

É um teste feito em escala menor antes de lançar uma ideia ou um sistema novo para todo mundo. Isso permite encontrar erros e corrigi-los gastando pouco dinheiro e correndo menos risco.

## Quais são os modelos matemáticos utilizados em PO?

- **Linear:** trata de relações em que uma variável varia **de maneira proporcional a outra.**
- **Inteiro:** utilizado quando as variáveis de decisão precisam assumir **valores inteiros**.
- **Probabilístico:** é utilizado quando existe **incerteza** no problema. Em vez de assumir que tudo acontecerá de uma determinada maneira, ele considera diferentes possibilidades e suas probabilidades.
- **Híbrido:** combina diferentes tipos de modelos ou técnicas para representar **um problema que possui características variadas.**
- **Simulação:** o **modelo de simulação** tenta **imitar o funcionamento de um sistema real** ao longo do tempo. Em vez de necessariamente procurar diretamente uma solução matemática ótima, você cria uma representação do sistema e observa como ele se comporta em diferentes situações.

## O que é programação linear (PL)?

É uma técnica matemática de otimização usada para encontrar a melhor solução (máxima ou mínima) para um problema em que as relações entre as variáveis são lineares.

### Em quais cenários a programação linear é amplamente utilizada?

Quando quer:
- Maximizar lucro, produção, quantidade de recursos.
- Minimizar custos, tempo, desperdícios.

### Quais são os componentes da PL?

- **Variáveis de decisão:** são valores desconhecidos que você pode controlar para chegar à meta (quantidade de produtos a fabricar, horas trabalhadas etc.).
- **Função objetivo (FO):** define qual valor você quer maximizar (lucro, produção) ou minimizar (custo, tempo).
- **Restrições:** regras que as variáveis de decisão precisam seguir. Por exemplo: alguém possui certa quantidade de matéria-prima que não pode ser ultrapassada. Tipos de restrições:
	- **Igualdade:** representam equilíbrios
	- **Desigualdade:** definem limites (ex.: x+y≤2, em que a soma de x e y não pode ultrapassar 2 unidades).
	- **Não negatividade:** algumas variáveis não podem ser negativas (ex.: x≥0, você não pode ter uma quantidade negativa de ingredientes).
- **Região viável:** conjunto de valores possíveis para as variáveis de decisão que respeitam todas as restrições.
- **Solução ótima:** É o conjunto de valores para as variáveis de decisão que atinge a meta da função objetivo (maximizar lucro ou minimizar custo) dentro da região viável. É a combinação de todos esses componentes que te dá o melhor resultado possível.

## Exercício de PL

Uma empresa fabrica dois produtos, A e B. O lucro por unidade de A é R$ 2,00 e o lucro por unidade de B é R$ 3,00. 

A empresa tem 10 horas de mão de obra disponíveis por dia e 12 horas de máquina disponíveis por dia. 

O produto A exige 1 hora de mão de obra e 2 horas de máquina por unidade, enquanto o produto B exige 2 horas de mão de obra e 1 hora de máquina por unidade. 

A empresa deseja determinar a quantidade de cada produto a ser fabricada para maximizar o lucro total.

**Resposta:**

As variáveis de decisão são:

- x1 = quantidade que deve ser produzida do Produto A.
- x2 = quantidade que deve ser produzida do Produto B.

A função objetivo é: Z = 2x1 + 3x2, sendo 2 e 3 referente ao lucro que cada produto obter.

As restrições são:

Mão de obra: 1x1 + 2x2 <= 10
Máquinas: 2x1 + 1x2 <= 12

**Como x1 e x2 se referem a quantidade de produtos A e B, esses valores não podem ser negativos. Portanto: x1, x2 >= 0.**

Para encontrar a região viável, é possível utilizar o https://www.geogebra.org/calculator, colocando As equações e suas restrições:

- x+2y=10
- 2x+y=12
- a: x≥0 ∧ y≥0 ∧ x+2 y≤10 ∧ 2 x+y≤12

**OBS.: ∧ representa o &&**

### Por que colocar  x+2y=10 e não  x+2y≤10?

Porque é preciso informar o valor máx. da mão de obra e da máquina.

A partir desses valores, será gerado a região viável (marcada de azul):

![[Pasted image 20260810112215.png]]

Para encontrar a solução ótima, ou seja, entender qual é a maior quantidade de produtos A e B possível que resultará no maior lucro.

Primeiro clique em Ferramentas → Ponto. Clique agora em cada um dos quatro vértices.

![[Pasted image 20260810121029.png]]

Para isso, clique em Ferramentas → Controle Deslizante. Será aberto essa aba:

![[Pasted image 20260810115811.png]]

Esse controle deslizante irá representar a variação de lucro de acordo com a quantidade de produtos A e B. Neste acaso aconselhado escolher o lucro máx. mais ou menos proporcional ao lucro que cada produto pode obter por unidade. Foi escolhido 20, mas poderia ser outro valor.

Por fim, clique novamente em Álgebra e coloque a função objeto 2x + 3y = (nome do controle deslizante), ou seja, 2x + 3y = L. Agora é possível descobrir o lucro máximo, posicionando a reta em um dos vértices.

![[Pasted image 20260810121646.png]]

Na seção de Álgebra, você pode descobrir os valores presentes no vértice referentes a quantidade de cada produto.

![[Pasted image 20260810121624.png]]

Como o exercício era descobrir a quantidade de cada produto, o resultado foi:

- x1 = 4,67
- x2 = 2,67

E a função objetivo será calculada como:

Z = 2(x1) + 3(x2)
Z = 2.4,67 + 3.2,67
Z = 9,34 + 8,01
Z = 17,3

## Principais métodos para resolver problemas PL

- **Método gráfico:** é recomendado para problemas simples com duas variáveis, permitindo uma visualização direta da solução através de gráficos. No entanto, sua aplicação é limitada a problemas com apenas duas variáveis, sendo desafiador encontrar a solução ótima em problemas mais complexos que envolvem mais variáveis ou restrições.
- **Método simplex:** busca a solução ótima passo a passo, explorando iterativamente os vértices do espaço de solução. Apesar de sua eficácia, pode ser lento para problemas com muitas variáveis ou restrições complexas.
- **Dns Branch-and-bound:** método utilizado para resolver problemas de PL com variáveis inteiras, dividindo o problema em subproblemas menores. Embora seja eficaz, pode ser demorado para problemas que envolvam muitas variáveis inteiras ou complexas.
- **Programação linear inteira mista (MILP):** combina elementos da PL tradicional e da programação linear inteira, abrangendo inúmeros problemas de otimização. A MILP é adequada para problemas que envolvem variáveis tanto contínuas quanto inteiras, mas pode ser mais desafiadora de resolver do que problemas de PL pura.
- **Softwares de otimização:** métodos dedicados à resolução de problemas de otimização, como GAMS, LINGO, CPLEX, Solver, AMPL, além de linguagens de programação como Python com bibliotecas como PuLP e Pyomo.

## Quais são as múltiplas interpretações de um problema (PL)?

- **Solução ótima.**
- **Valores da função objetivo.**
- **Sensibilidade:** a análise de sensibilidade avalia como a solução ótima muda em resposta a alterações nos parâmetros do problema, como coeficientes da função objetivo
- **Interpretação de sombras:** revela o impacto de relaxar cada restrição em uma unidade e podem ser utilizadas para identificar gargalos e oportunidades de otimização.
- **Relatórios e outputs:** os softwares de PL geralmente fornecem relatórios detalhados com a solução, valores da função objetivo, sensibilidade, sombras e coeficientes.

# Aplicações da Programação Linear

## Quais são os 4 elementos principais da programação linear?

- **Função objetivo**
- **Parâmetros:** valores numéricos fixos e conhecidos de antemão que definem o problema. Eles representam as constantes do cenário matemático, diferenciando-se das variáveis (que são os valores desconhecidos que tentamos descobrir).
- **Coeficientes de decisão**
- **Restrições**
## O que é o problema de misturas (ou de dietas)?

É um modelo de otimização linear usado para combinar diferentes ingredientes ou matérias-primas de modo a fabricar um produto final ao **menor custo possível**, respeitando limites de proporção e qualidade.
## Exercício

Uma mãe deseja que seu filhos tenham uma alimentação equilibrada. Por isto, consultou uma nutricionista que lhe recomendou que eles comam, no mínimo, 10 mg de vitamina A, 70 mg de vitamina C e 250mg de vitamina D por dia. Essa mãe deseja oferecer aos seus filhos essa dieta equilibrada, porém ao menor custo possível. Logo, ela fez uma pesquisa e descobriu as informações nutricionais para diferentes tipos de alimento, conforme apresentado a seguir.

|Vitamina|Leite (l)|Carne (kg)|Peixe (kg)|Salada (100g)|
|---|--:|--:|--:|--:|
|A|2|2|10|20|
|C|50|20|10|30|
|D|80|70|10|80|
A mãe foi ao supermercado e verificou que um litro de leite custa R$2,00, 1 kg de carne custa R$20,00, 1 kg de peixe custa R$25,00 e para preparar 100g de salada ela gastaria R$3,00.

### Quais são as variáveis de decisão?

A variável de decisão deve ser xᵢ, sendo x a quantidade de alimento do tipo “i” a ser consumida por dia. Logo, temos:

- **x₁ =** litros de leite a serem consumidos por dia pelas crianças
- **x₂ =** quilos de carne a serem consumidos por dia pelas crianças
- **x₃ =** quilos de peixe a serem consumidos por dia pelas crianças
- **x₄ =** 100g de salada a serem consumidos por dia pelas crianças

### Qual a função objetivo?

Sabemos que a mãe deseja gastar o menor valor possível (representado aqui por Min Z). Portanto:

Min Z = 2x₁ + 10x₂ + 25x₃ + 3x₄

### Qual é o conjunto de restrições?

2x₁ + 2x₂ + 10x₃ + 20x₄ ≥ 10 → Vitamina A
50x₁ + 20x₂ + 10x₃ + 30x₄ ≥ 70 → Vitamina C
80x₁ + 70x₂ + 10x₃ + 80x₄ ≥ 250 → Vitamina D
Restrição de não negatividade das variáveis de decisão: **x₁, x₂, x₃, x₄ ≥ 0**

### Fazendo o cálculo com o Solver

O solver será um tipo de extensão do Excel utilizado para calcular problemas de misturas. Para saber como usar, veja o segundo vídeo da aula **Problema da mistura** no módulo **Modelagem Linear**.

## Problema estático

Aqui, considera-se a produção em determinado horizonte de programação finito, de modo que as formulações contemplam apenas um período.

## Exercício

Uma empresa fabrica um único produto e precisa planejar sua produção para os próximos três meses (janeiro, fevereiro e março). A demanda esperada para cada mês é de 100 unidades em janeiro, 150 unidades em fevereiro e 120 unidades em março. O custo de produção é de R$10 por unidade, e o custo de armazenagem de unidades em estoque **de um mês para o próximo** é de R$1 por unidade. A capacidade máxima de produção em cada mês é de 130 unidades. A empresa não possui estoque inicial e deseja atender a toda a demanda com o menor custo total (produção + armazenagem).

Formular uma solução onde a Função Objetivo é minimizar o custo total levando em consideração a produção e o armazenamento.

### Variáveis de Decisão

Vamos definir variáveis para cada mês:

- **Xᵢ:** Quantidade produzida entre os meses de janeiro a março (onde i=1,2,3).
- **Eᵢ:** estoque no final de janeiro e fevereiro (onde i=1,2).

**OBS.: o estoque de março não foi considerado porque cada estoque representa a quantidade de produtos que sobrou para o próximo mês e, consequentemente, o estoque de março seria utilizado para o mês de abril, mas não está sendo considerado no exercício.**

**Min Z = 10x₁ + 10x₂ + 10x₃ + 1E₁ + 1E₂**

Demanda de Janeiro:

x1 = 100 + 1E1

Onde

X1 representa a quantidade que a empresa produz no mês de janeiro.
100 é a demanda esperada para o mês de janeiro
E1 representa o estoque que sobra no final do mês de janeiro.
Demanda de Fevereiro:

x2 + E1 = 150 + E2

Onde

X2 é a quantidade produzida em fevereiro.
150 é a demanda esperada para o mês de fevereiro
E1 representa o estoque que sobra no final do mês de janeiro e está disponível no início de fevereiro
E2 é o estoque que sobra no final de fevereiro
Demanda de Março

x3 + E2 = 120

X3 é a quantidade produzida em março.
E2 é o estoque que sobra no final de fevereiro e que está disponível no início de março.
120 é a demanda esperada para o mês de março.
Restrições de capacidade de produção:

x1 <= 130
x2 <= 130
x3 <= 130

### Restrições de não negatividade

x1; x2; x3; E1; E2 >= 0

## Exercício

Uma fábrica de bicicletas acaba de receber um pedido de R$ 750.000,00. Foram encomendadas 3.000 bicicletas do modelo 1, 2.000 do modelo 2 e 1.000 do modelo 3.

São necessárias 2 horas para a montagem da bicicleta do modelo 1 e 1 hora para sua pintura. Para a bicicleta do modelo 2, leva-se 1,5 horas para a montagem e 2 horas para a pintura. Para a bicicleta do modelo 3, são necessárias 3 horas de montagem e 1 hora de pintura. A fábrica tem disponibilidade de 10.000 horas para montagem e 6.000 horas para pintura até a entrega da encomenda.

Os custos para a fabricação das bicicletas são: R$ 350,00 para a bicicleta 1, R$ 400,00 para a bicicleta 2 e R$ 430,00 para a bicicleta 3.

A fábrica teme não ter tempo hábil para produzir toda a encomenda e, por isso, cotou o custo de terceirizar a sua fabricação. O custo para comprar uma bicicleta do modelo 1 seria de R$ 460,00, de R$ 540,00 para a bicicleta do modelo 2 e de R$ 580,00 para a bicicleta do modelo 3.

Desenvolva o modelo de programação linear para minimizar o custo de produção da encomenda de bicicletas.

|                        | Modelo 1 | Modelo 2 | Modelo 3 |
| ---------------------- | -------- | -------- | -------- |
| Encomenda              | 3000     | 2000     | 1000     |
| Tempo para montagem    | 2h       | 1,5h     | 3h       |
| Tempo para pintura     | 1h       | 2h       | 1h       |
| Custos                 | 350      | 400      | 430      |
| Custo de terceirização | 460      | 540      | 580      |

Tempo máx. para montagem = 10.000 horas.
Tempo máx. para pinturas  = 6.000 horas.
### Variáveis de decisão

Para cada modelo i ∈ {1, 2, 3}
Xi >= 0: quantidade **produzida** internamente do modelo i.
Yi >= 0: quantidade **comprada (terceirizada)** do modelo i.

### Função objetivo
Min , Z = 350x1 + 400x2 + 430x3 + 460y1 + 540y2 + 580y3

### Restrições  

1. Atendimento da demanda (Fazer + comprar = pedido)  

x1 + y1 = 3000 
x2 + y2 = 2000
x3 + y3 = 1000

Capacidade de Montagem:  

2x1 + 1,5x2 + x3 <= 6.000

Capacidade de Pintura:  

x1 + 2x2 + 3x3 <= 10.000

Não Negatividade  

xi >= 0, y1 >= 0 (i = 1,2,3)

## Problema de transporte

O problema de programação linear para o problema clássico de transportes consiste em definir o melhor caminho (ou rota) para fazer com que determinada quantidade de produtos de um ponto de suprimento chegue a um ponto de demanda. 

O objetivo pode ser minimizar as distâncias percorridas, o custo de transporte ou até mesmo maximizar os níveis de serviço ou o lucro com vendas.
### Exercício

Uma empresa possui duas fábricas (F1 e F2) e três centros de distribuição (C1, C2 e C3). Cada fábrica tem uma capacidade de produção, e cada centro de distribuição tem uma demanda a ser atendida. O custo de transporte por km entre cada fábrica para cada centro de distribuição é dado em reais conforme a tabela a seguir. O objetivo é minimizar o custo total de transporte, atendendo a todas as demandas sem ultrapassar a capacidade das fábricas.

| **  <br>Centro 1** | **Centro 2** | **Centro 3** | **Capacidade** |         |
| ------------------ | ------------ | ------------ | -------------- | ------- |
| **F1**             | **R$ 4**     | **R$ 5**     | **R$ 7**       | **130** |
| **F2**             | **R$ 3**     | **R$ 6**     | **R$ 12**      | **160** |
| **Demanda**        | **80**       | **100**      | **90**         |         |
Formule um problema de programação linear com o objetivo de minimizar os custos de transporte da empresa.

### Variáveis de decisão

Como em todo modelo de PL, o primeiro passo é definir as variáveis de decisão. Neste caso, em que buscamos reduzir os gastos com transporte, essas variáveis representarão as quantidades a serem transportadas de cada ponto de origem para cada destino, conforme descrito a seguir.

Cada transporte sai de uma fábrica (i) para chegar a um destino (j). Podemos representar essa situação por meio de uma matriz, na qual temos Xij, ou seja, quero sair de um ponto e chegar ao outro.

|             | **Centro 1** | **Centro 2** | **Centro 3** | **Capacidade** |
| ----------- | ------------ | ------------ | ------------ | -------------- |
| **F1**      | **R$ 4x₁₁**  | **R$ 5x₁₂**  | **R$ 7x₁₃**  | **130**        |
| **F2**      | **R$ 3x₂₁**  | **R$ 6x₂₂**  | **R$ 12x₂₃** | **160**        |
| **Demanda** | **80x₁₂**    | **100x₁₂**   | **90x₁₂**    |                |

### Função objetivo 

Será a soma de todos os caminhos percorridos entre as fábricas e os centros de distribuições, com o objetivo de minimizar o custo total de transporte.

### Restrições

#### Restrição de capacidade das fábricas

x11​+x12​+x13​≤130 Restrição da fábrica 1
x21+x22+x23≤160 Restrição da fábrica 2
#### Restrição de capacidade dos centros de distribuição

- x11​+x21​=80 Restrição do centro de distribuição 1
- x12​+x22​=100 Restrição do centro de distribuição 2
- x13​+x23​=90 Restrição do centro de distribuição 3

## Problema de transbordo

O problema de transbordo segue lógica semelhante ao problema de transportes, porém este não é um modelo fluxo em grafo bipartido, pois existem nós intermediários de transbordo ou de transição para fluxo.
### Exercício

Uma empresa possui duas fábricas (F1 e F2), um armazém central (A), e dois centros de venda (C1 e C2). Os produtos são enviados das fábricas para o armazém e, depois, do armazém para os centros de venda.

Capacidades:
- F1 pode enviar até 100 unidades.
- F2 pode enviar até 150 unidades.

Demandas:
- C1 precisa de 120 unidades.
- C2 precisa de 130 unidades.

Cada custo de transporte por km está indicado no esquema a seguir.

![](https://cdn-conteudo.ensineme.com.br/Sem_Titulo_1_823d665db1.jpg "Renata Albergaria de Mello Bandeira")

Modele o problema por meio de programação linear com a finalidade de minimizar os custos de transporte.
### Variáveis de decisão

As variáveis de decisão são os caminhos que as fábricas fazem até o armazém ($x_{F_1A}$ e  $x_{F_2A}$) e o caminho que o armazém faz até os centros de distribuição com seus respectivos valores ($x_{AC1}$ e $x_{AC2}$).
### Função objetivo

$$
Min\ Z = 4x_{F_1A} + 6x_{F_2A} + 5x_{AC1} + 3x_{AC2}
$$
### Restrições

Temos como restrição os limites das fábricas, o fluxo de entrada e saída do armazém, o atendimento das demandas do centro e as restrições de não negatividade. Separando cada uma delas, temos:

#### Restrição de limite das fábricas
$$
\begin{aligned}
x_{F1A} \leq 100 \\
x_{F2A} \leq 150
\end{aligned}
$$
#### Restrição de demanda

$$
\begin{aligned}
x_{AC1} = 120 \\
x_{AC2} = 130
\end{aligned}
$$
#### Restrição de não negatividade:

$$
x_{F_1A},\ x_{F_2A},\ x_{AC1},\ x_{AC2} \geq 0
$$

## Problema de alocação (designação ou matching)

Este problema lida com dois conjuntos e a criação de pares através dos elementos destes dois conjuntos, considerando a minimização e respeitando as restrições.

### O que são variáveis de decisão?

Uma empresa precisa alocar funcionários para três turnos diários (manhã, tarde e noite). Cada turno exige uma quantidade mínima de trabalhadores. A empresa dispõe de 3 funcionários (A, B e C), e cada um tem uma disponibilidade e um custo/hora diferente.

Demandas por turno:
- Manhã: 2 funcionários
- Tarde: 2 funcionários
- Noite: 1 funcionário

Custos por hora:

|   |   |   |   |
|---|---|---|---|
||**Manhã**|**Tarde**|**Noite**|
|**Funcionário A**|**8**|**10**|**11**|
|**Funcionário B**|**11**|**12**|**14**|
|**Funcionário C**|**9**|**7**|**15**|

Regras:
- Cada funcionário pode trabalhar no máximo em 2 turnos.
- Um funcionário só pode ser alocado uma vez por turno (0 ou 1).

### Variáveis binárias

No problema de alocação criamos variáveis binárias xiJ​ em que:

i: representa o funcionário (por exemplo: A,B ou C).  
j: representa o turno (por exemplo: manhã, tarde ou noite).

Por ser uma variável binária, xiJ​ só pode valer 0 ou 1 , ou ele está alocado ou não está alocado.

xiJ​=1 o funcionário foi alocado no turno j.  
xiJ​=0 o funcionário não foi alocado no turno j.

Com isso, temos as seguintes variáveis:

$$
X_A,m​,\ X_B,m​,\ X_C,m​,\ X_A,t​,\ X_B,t​,\ X_C,t,\ X_A,n​,\ X_B,n​,\ X_C,n​
$$

### Função objetivo:

$$
MinZ=8X_A,m​+11X_B,m​+9X_C,m​+10X_A,t​+12X_B,t​+7X_C,t​+11X_A,n​+14X_B,n​+15X_C,n
$$

### Restrições:

Manhã: xA,m​+xB,m​+xC,m​≥2  
Tarde: xA,t​+xB,t​+xC,t​≥2  
Noite: xA,n​+xB,n​+xC,n​≥1  
Funcionário A: xA,m​+xA,t​+1xA,n​≤2  
Funcionário B: xB,m​+xB,t​+xB,n​≤2

Funcionário A: xC,m​+xC,t​+xC,n​≤2

xiJ​∈{0,1}

# Tema 4 - Dualidade e Análise de Sensibilidade

## O que é problema dual?

é um modelo matemático associado a um problema original (**chamado de primal**) na programação linear. Enquanto o primal maximiza lucros ou minimiza custos diretos, o dual inverte o objetivo (de máx. para min.), transformando restrições em variáveis e revelando limites de valor e custos de oportunidade.

**OBS.: o número de variáveis do problema dual é igual ao número de restrições do problema primal.**

Existe um conjunto de regras para se obter o dual de um problema de programação linear, sintetizado na tabela a seguir.

| Par assimétrico                             |                                             |
| ------------------------------------------- | ------------------------------------------- |
| Problema primal (dual)                      | Problema dual (primal)                      |
| Maximizar                                   | Minimizar                                   |
| Termos independentes                        | Coeficientes da Função Objetivo (FO)        |
| Coeficientes da Função Objetivo (FO)        | Termos independentes                        |
| i-ésima linha de coeficientes tecnológicos  | i-ésima coluna de coeficientes tecnológicos |
| j-ésima coluna de coeficientes tecnológicos | j-ésima linha de coeficientes tecnológicos  |
| **Restrição com relação tipo:**             | **Variável tipo:**                          |
| ≤                                           | Não negativa                                |
| ≥                                           | Não positiva                                |
| =                                           | Sem restrição de sinal                      |
| **Variável tipo:**                          | **Restrição com relação tipo:**             |
| Não negativa                                | ≥                                           |
| Não positiva                                | ≤                                           |
| Sem restrição de sinal                      | =                                           |
## Exemplo

### 1. Problema primal

O problema dado é:

$$
Max ZP​=6X_1​+4X_2​+10X_3​
$$

Sujeito a:

$$
\begin{aligned}
X_1​+3X_2​+2X_3​≤15 \\
2X_2​−X_3​≥5 \\
2X_1​+X_2​−5X_3​=10 \\
X_1​,X_2​,X_3​≥0
\end{aligned}
$$

### 2. Variáveis do dual

Como o problema primal possui **3 restrições**, o problema dual terá **3 variáveis**:

- $Y_1$​ → associada à primeira restrição;
- $Y_2$​ → associada à segunda restrição;
- $Y_3​$ → associada à terceira restrição.

Como o primal é um problema de **maximização**, analisamos o tipo de cada restrição:

| Restrição primal | Variável dual |
| ---------------- | ------------- |
| ≤                | $Y_1$​≥0      |
| ≥                | $Y_2$​≤0      |
| =                | $Y_3$​ livre  |

Portanto:

$Y_1$​≥0
$Y_2$​≤0
$Y_3​$ livre

**OBS.: livre significa que a variável não possui uma restrição de sinal.**

### 3. Função objetivo dual

Os termos da função objetivo dual são formados pelos valores do **lado direito das restrições do primal**: 15,5,10

Como o primal é de **maximização**, o dual será de **minimização**:

$$
Min ZD​=15Y_1​+5Y_2​+10Y_3
$$
### 4. Restrições do dual

Como existem **3 variáveis no primal**, teremos **3 restrições no dual**.

#### Restrição associada a $X_1​$

Pegamos os coeficientes de X1 (números que a multiplicam)​ encontradas nas restrições:

1,0,2

O coeficiente de $X_1​$ na função objetivo primal é 6.

Logo:

$Y_1​+2Y_3​≥6​$
#### Restrição associada a $X_2​$

Coeficientes de $X_2​$:

3,2,1

O coeficiente de $X_2​$ na função objetivo é 4.

Portanto:

$3Y_1​+2Y_2​+Y_3​≥4$​
#### Restrição associada a $X_3​$

Coeficientes de X3​:

2,−1,−5

O coeficiente de $X_3​$ na função objetivo é 10.

Assim:

$2Y_1​−Y_2​−5Y_3​≥10$​

### Problema dual completo

$Min ZD​=15Y_1​+5Y_2​+10Y_3$​​

Sujeito a:


$$
\begin{aligned}
Y_1​+2Y_3​≥6​ \\
3Y_1​+2Y_2​+Y_3​≥4​ \\
2Y_1​−Y_2​−5Y_3​≥10
\end{aligned}$$

E as condições de sinal:

$$
\begin{aligned}
Y_1​≥0​ \\
Y_2​≤0​ \\
Y_3​ \ livre​
\end{aligned}
$$

### Resumo da lógica

- **3 restrições no primal → 3 variáveis no dual**.
- **3 variáveis no primal → 3 restrições no dual**.
- Primal **Max → Dual Min**.
- Como $X_1​,X_2​,X_3​≥0$, todas as restrições do dual são do tipo **≥**.
- O tipo de cada restrição do primal determina o sinal da variável correspondente no dual.


