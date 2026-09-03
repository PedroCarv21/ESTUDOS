
# O que é um modelo?

Representação abstrata do sistema a partir de alguma perspectiva. Esse modelo ajuda a todos os membros da equipe entenderem o funcionamento do sistema e a enxergar um problema antes mesmo do desenvolvimento do sistema.

# Quais são as fases mais comuns do processo de desenvolvimento de sistemas?

- **Levantamento de requisitos:** coleta e documentação dos requisitos que atendem as expectativas dos usuários finais e stakeholders.
- **Análise:** buscar entender quais seriam os requisitos funcionais (aquilo que o sistema deve fazer) e não-funcionais (restrições que o sistema deve atender (como de qualidade e segurança)) a partir dos requisitos levantados na etapa anterior. Nesta etapa também são construídos os diagramas que descrevem a estrutura e o funcionamento do sistema.
- **Projeto:** os requisitos são transformados em uma arquitetura mais detalhada, incluindo: componentes, interfaces e algoritmos. Esta etapa envolve também a escolha de tecnologias adequadas.
- **Implementação:** transformação do projeto teórico em código executável.
- **Testes:** verificar e garantir a qualidade do programa. Entre os tipos de testes estão:
	- **Unidade:** para validar unidades individuais de códigos.
	- **Integração:** garantir a harmonia entre diferentes módulos.
	- **Sistema:** avalia o comportamento do software como um todo.
	- **Aceitação:** verificar se o software cumpre as expectativa dos usuários finais.
- **Implantação:** disponibilização do software para uso dos usuários finais.
- **Manutenção:** correção de bugs e atualizações de segurança devem ser realizados ao longo do ciclo de vida do software depois da sua implantação.

# O que é operação, mensagem e estado em POO?

- **Operação:** se refere as ações que um objeto pode realizar.
- **Mensagem:** estímulo que chega a um objeto e solicita que ele realize uma de suas operações. Quando um objeto precisa de um serviço da responsabilidade de outro, ele precisa enviar uma mensagem a ele.
- **Estado:** conjunto de valores de seus atributos em dado momento.

# Quais são as duas fases da análise de sistemas orientado a objetos?

- **Levantamento de requisitos:** serão identificados os requisitos funcionais (o que o sistema deve funcionar) e não funcionais (restrições do sistema) para entender as necessidades e desejos dos envolvidos.
- **Análise de requisitos:** como esses requisitos influenciam o domínio (objetos presentes no sistema (ex.: cliente, veículo, pagamento)) e a aplicação (refere-se a aspectos computacionais de alto nível como a interface do usuário).

# Quais são as duas fases do projeto de sistemas orientado a objetos?

- **Projeto de arquitetura:** distribuição das classes em componentes e distribuir esses componentes em recursos de hardware.
- **Projeto Detalhado:** envolve atividades como modelagem das interações entre objetos, design da interface e do banco de dados, e considerações sobre aspectos computacionais avançados.
# Quais são as visões da UML?

- **Visão lógica de projeto:** apresenta a relação entre os diversos componentes do sistema. Exemplo é o diagrama de classe.
- **Visão de implementação ou desenvolvimento:** envolve o gerenciamento das versões do sistema, ou seja, suas implementações utilizáveis pelos usuários.
- **Visão de implantação ou física:** representa a infraestrutura física no qual o sistema será implantado e executado. Diagrama de implantação. 
- **Visão de processo:** representa os aspectos de execução e comportamento do sistema. Exemplo é o diagrama de sequência. Exemplo são os diagramas de componentes e de pacote.
- **Visão de caso de uso (esta é a reunião de todas as anteriores):** representa a interação do usuário com o sistema, apresentando as funcionalidades que o sistema deve oferecer ao usuário.

# Quais são os processos da UML?

- **Cascata:** Com ou sem retroalimentação, as fases ocorrem sequencialmente, iniciando a próxima quando a anterior é concluída. A desvantagem é que, sem retroalimentação, não há retorno à fase anterior. Por exemplo, se novos requisitos são identificados durante a fase de projeto, eles não podem ser considerados porque a fase de análise já congelou os requisitos identificados. Se a retroalimentação é permitida, esse problema pode ser minimizado, mas não totalmente resolvido. Um grande problema é que o usuário interage com a equipe de desenvolvimento apenas no início e no final do processo, quando o sistema é entregue.
- **Iterativo:** é dividido em subconjuntos de funcionalidades (com mínimo de dependência com os demais conjuntos), e as atividades são realizadas a cada subconjunto. Isso significa que a cada subconjunto haverá a implantação de uma parte do sistema, permitindo que ajustes das partes encerradas ocorram em paralelo com o novo subconjunto de funcionalidades que está sendo construído.
- **Ágil:** Compartilha um conjunto de valores e princípios definidos pelo Manifesto Ágil. O foco está na capacidade de adaptação contínua e no desenvolvimento de código. A modelagem existe, mas é menos abrangente, com ênfase na comunicação entre usuário e equipe de desenvolvimento. Os processos ágeis tendem a ser menos formais.
- **RUP (Rational Unified Proccess):** estrutura para processos iterativos. Será definido uma estrutura para gerenciar projetos complexos, dividindo o ciclo de vida em 4 fases: concepção, elaboração, construção e transição.

# Qual a diferença entre um diagrama estrutural e um digrama comportamental?

- **Estrutura:** estruturas estáticas necessárias ao sistema, como os pacotes e classes, essenciais para o funcionamento do sistema. **Também são chamadas de estruturas estáticas**. Exemplo é o digrama de classe.
- **Comportamental:** representa o comportamento (funcionamento) de parte de um sistema ou processo de negócio relacionado ao sistema. Exemplos são os diagramas de caso de uso e de sequência.

# Quais os principais diagramas?

- **Objetos:** É um diagrama de classes instanciado, ou seja, mostra exemplos de instâncias de classes.
- **Componentes:** Apresenta a estrutura e as conexões entre os componentes de um sistema. Um componente é uma unidade que encapsula um conjunto de funcionalidades relacionadas.
- **Atividades:** mostra o passo a passo de um processo, sistema ou fluxo de trabalho de um jeito simples e claro.
- ![[Pasted image 20260807123918.png]]
- **Sequência:** Mostra como os objetos interagem, evidenciando a linha de tempo (a sequência das interações).
- ![[Pasted image 20260807123947.png]]
- **Estado:** mostra como os eventos que afetam o sistema alteram o estado dos objetos ao longo de seus ciclos de vida.

# Quais são os principais diagramas utilizados

- **No levantamento de requisitos:** caso de uso e atividade.
- **Análise:** caso de uso, atividade, classe e pacote.
- **Projeto:** atividade, classe, colaboração e componentes.
- **Implementação:** atividade, classe, colaboração e componentes.
- **Nos testes:** atividades, caso de uso e componentes.
- **Implantação:** implantação, componente e pacote.

# Uml Para Modelagem do Domínio

## O que são requisitos?

Necessidades que o sistema deve atender.

- **Requisitos de Usuário:** serviços que o sistema deve fornecer para que o usuário atinja o objetivo.
- **Requisitos de Software:** descrições detalhadas dos serviços e restrições operacionais do sistema. A parte de descrição dos serviços é chamada de **requisitos funcionais** e a parte de descrição das restrições é chamada de **requisitos não-funcionais**. Os requisitos não-funcionais são classificados em:
	- **Produto:** usabilidade, eficiência, desempenho.
	- **Organizacionais:**  ambientais, operacionais
	- **Externos:** éticos, legais, contábeis.

## Quais são os tipos de relacionamento em um diagrama de casos de uso?

- Casos de uso com seus atores.
- Casos de uso com outros casos de uso.
- Atores com outras atores.

## Quais são os tipos de relacionamento em um diagrama de caso de uso?

- **Inclusão:** Indica que um caso de uso base **necessita obrigatoriamente** do comportamento de outro caso de uso para concluir sua tarefa. É também utilizado para representar a reutilização de passos de execução em diferentes casos de uso O relacionamento de inclusão é representado por uma seta pontilhada escrito `<<include>>`.
- **Extensão:** indica que um caso de uso base **pode ou não** ter seu comportamento alterado ou ampliado por outro caso de uso. O relacionamento de extensão é representado por um seta pontilha escrito `<<extend>>`.
- **Generalização:** é um caso de genérico que engloba outros casos de uso mais específicos. Por exemplo, um caso de uso 'Cadastrar empregado' poderia ser um caso de uso genérico para outros dois casos de uso: 'Cadastrar vendedor' e 'Cadastrar supervisor'.

## Quais são os tipos de especificações textuais de caso de uso?

- **Formato contínuo:** modelo de especificação de Caso de Uso que descreve a interação entre o ator e o sistema na forma de um texto corrido.
- **Numerado:** os casos de uso são organizados em formato de lista.
- **Tabular:** representado por uma tabela contendo uma coluna para cada ator e uma coluna para o sistema. Exemplo:

|Cliente|Sistema|
|---|---|
|Insere cartão no caixa eletrônico.||
||Solicita a senha.|
|Digita senha.||
||Valida a senha e exibe menu de operações disponíveis.|
|Seleciona a opção consultar o saldo.||
||Exibe o saldo da conta.|
## Quais são os cenários de caso de uso?

- **Cenário principal:** o que deve ser feito normalmente para que o caso de uso alcance seu objetivo.
- **Cenário alternativo:** quando o mesmo objetivo pode ser alcançado de maneiras distintas.
- **Cenário de exceção:** quando algum ocorre e precisa ser corrigido. A forma correta de tratar exceções no modelo de casos de uso é especificar cenários de exceção que, diferentemente dos cenários alternativos, representam situações de anomalias que rompem o fluxo do cenário principal.

## Qual é a estrutura da especificação do caso de uso?

- **Identificador:** código único para cada caso de uso.
- **Nome:** cada caso de uso tem um nome.
- **Objetivo**
- **Primário:** aquele que **inicia** ou que recebe o resultado do caso de uso.
- **Pré-condições:** condições para que o caso de uso tenha início.
- **Secundário:** aqueles que atuam no caso de uso.
- **Cenário principal e cenários alterativos e de exceção**
- **Pós-condições:** estado do sistema após o caso de uso ter sido executado.
- **Regras de negócio:** descrição do que um caso de uso pode fazer referente as regras de negócio.

## Como deve ser a descrição de atributos e métodos em um diagrama de classe?

- **Atributos:** [visibilidade] nome: tipo. Os tipos de visibilidade são:
	- Público (representado pelo +).
	- Protegido (representado pelo #).
	- Privado (representado pelo -).
	- De pacote (representado pelo ~).
- **Métodos:** [visibilidade] nome(parâmetros) : tipo-retorno.

## Tipos de relacionamento entre classes

### Associação

- Representação: linha reta
- Significado: representa a possibilidade da troca de mensagens entre as classes associadas. Exemplo: cliente faz pedido.

Os tipos de associações são:

|                      |             |
| -------------------- | ----------- |
| Apenas 1             | 1..1 (ou 1) |
| Zero ou Muitos       | 0..* (ou *) |
| Um ou Muitos         | 1..*        |
| Zero ou Um           | 0..1        |
| Intervalo Específico | li..ls      |
#### Tipos de associações que podem ser aplicadas aos diagramas de classe

- **Classe associativa:** é usada para guardar informações sobre a associação e é ligada a uma associação e não a outras classes. São comuns em relacionamentos Many-To-Many. É representado por uma linha pontilhada ligada a associação.
- **Auto associações:** ocorre quando objetos da mesma classe se relacionam e possuem papeis diferentes.
![[Pasted image 20260821125800.png]]
- **Associação todo-parte:** indica que um dos objetos está contido (faz parte) no outro. Existem dois tipos de associação:
	- **Agregação:** a parte existe independente da existência do todo. É representado pelo losango branco.
	- **Composição:** a parte não pode existir sem a existência do todo. É representado pelo losango preto.
- **Mecanismo de herança:** é um dos pilares da POO. É representado por uma seta branca.

## Considerações sobre diagrama de objetos

Diferente dos diagramas de classe (que possuem nome, atributos e métodos), os diagrama de objeto terá cada objeto com apenas um nome e atributo (sem métodos). Exemplo de diagrama de objeto. Exemplo:

![[Pasted image 20260821151915.png]]

Os diagramas de objeto, embora não muito utilizados, podem ser úteis para validar certos aspectos de um diagrama de classe. Em suma, eles podem ajudar na análise de uma interação específica entre objetos do sistema.

As duas qualidades que podem ser verificadas são:
- Exatidão: se todas as conexões e objetos estão de acordo com diagrama de classes original.
- Completude: se falta alguma conexão ou objeto, quer no diagrama de objetos ou no diagrama de classes.

## O que é diagrama de pacote?

Descreve os pacotes ou pedaços do sistema divididos em agrupamentos lógicos mostrando as dependências entre eles. Este diagrama é muito utilizado para ilustrar a arquitetura de um sistema mostrando o agrupamento de suas classes.

### Algumas características

- As pacotes podem se relacionar entre si de forma dependente.
- É possível definir a visibilidade de pacotes e dos elementos contidos nele.

### Quais as relações de dependência?

- **Acesso:** indica que um pacote requer assistência das funções de uma classe que está em outro pacote.
- **Importação:** indica que uma funcionalidade foi importada de um pacote para outro.

Ambas as relações são representadas por uma linha pontilhada com uma seta apontando para o pacote dependente.
### Exemplo de diagrama de pacote

![[Pasted image 20260821161529.png]]

### Visibilidades nos pacotes

- Público (+)
- Protegido (#)
- Privado (-)
# Utilizando Uml Para Projetar o Software

## O que é o diagrama de interação?

É um tipo de diagrama comportamental que mostra como objetos ou partes de um sistema trocam mensagens e dados ao longo do tempo. Além disso:

- Os objetos possuem uma linha de vida definida.
- As mensagens são transformadas em métodos.
- Um diagrama de interação é baseado em um diagrama de interação específico.
- As principais características são:
	- **Atores**: aqueles que irão interagir com o sistema.
	- **Classes limites ou fronteiras (boundary class)**:  Objetos que interagem com atores do sistema (por exemplo, um **usuário** ou **um serviço externo** ). Janelas, telas e menus são exemplos de limites que interagem com usuários.
	- **Entidade (Entity object):** Objetos que representam dados do sistema, geralmente provenientes do modelo de domínio.
	- **Controle (Control object):** são objetos que atuam como intermediários entre limites e entidades. Eles servem como a cola entre os elementos de limite e os elementos de entidade, implementando a lógica necessária para gerenciar os diversos elementos e suas interações.

![[Pasted image 20260826115054.png]]

## Dois tipos de diagrama de interação

### Comunicação

Muito mais focado na relação entre os componentes do sistema. É também nesse diagrama em que as mensagens são enumeradas para descrever a sequência.
### Sequência

Diferente do diagrama de comunicação, o diagrama de sequência apresenta a sucessão de mensagens ocorrendo a partir do topo do diagrama até chegar no ponto mais baixo do diagrama.
#### Características dos diagramas de sequência

- Linha horizontal: atores objetos e classes.
- Vertical: linha de tempo e tempo de vida do objeto.
- Perfis específicos: fronteira, controle e entidade.
- Arquitetura MVC.

#### Tipos de mensagem

- **Síncrona:** espera uma resposta.
- **Assíncrona:** não espera resposta.
- **De retorno:** indica o retorno de um objeto. 
- **De criação:** indica a criação de um objeto.

![[Pasted image 20260826122701.png]]

#### Condição de guarda e iteração

A condição de guarda é uma expressão booleana (verdadeiro ou falso) colocada entre colchetes `[...]` ao lado ou acima de uma mensagem ou fragmento. Como funciona: a mensagem só é enviada ou executada se a condição dentro dos colchetes resultar em verdadeiro.

Já a condição de iteração é a repetição de uma mensagem ou conjunto de mensagens, semelhante a um laço (`for`, `while`) na programação. Como funciona: É indicada por um asterisco `*` na frente da mensagem (iteração simples).
#### Autochamada

Quando um método de um objeto X chama outro método do mesmo objeto X.
#### Tipos de interação

- **Ref:** referência para outro diagrama de sequência.
- **Opt:** representa um if-else.
- **Loop:** representa o loop de repetição.
- **Alt:** permitem que um trecho da interação seja alternativo.

## Qual a diferença entre diagrama de classe conceitual e de projeto?

O primeiro foca na análise enquanto que o segundo foca na implementação.

## Como devem ser utilizados os tipos em um diagrama de classes?

Os tipos devem ser utilizados de acordo com a plataforma de desenvolvimento (linguagem de programação).

## Como é declarado um atributo em um diagrama de classe?

```
[/][visibilidade] [nome] : [tipo] = [valor_inicial]
```

A barra / significa que o atributo é derivado, ou seja, calculado. Por exemplo, a partir da data de nascimento será calculado um valor para o atributo idade.

As visibilidades são representadas por símbolos:

- Pública (+).
- Privada (-).
- Protegida (#).
- Pacote (~).

O valor inicial é opcional.
## Como é declarado um método em um diagrama de classe?

```
[visibilidade] [nome([parâmtros])] : [tipo-retorno]
```

E o parâmetro será criado desta forma:

```
[direção] [nome-parâmetro] : [tipo-parâmetro]
```

Há três tipos de direção:

- **IN**: o parâmetro envia informação para dentro do método. método apenas lê o valor. Ele não modifica o dado original fora do escopo do método.
- **OUT**: o parâmetro serve para retornar uma informação para quem chamou o método. O método ignora qualquer valor inicial do parâmetro, calcula um novo dado e o preenche.
- **INOUT**: o parâmetro faz as duas funções ao mesmo tempo. O método lê o valor inicial do parâmetro, processa, modifica esse valor e devolve o dado alterado para a variável original.

## Quais são os diferentes tipos de associação entre as classes?

- **Unárias, reflexivas ou recursivas (autoassociação)**: quando a classe se associa com ela mesma.
- ![[Pasted image 20260902112019.png]]
- **Binária**: é uma ligação estrutural que conecta exatamente duas classes (ou instâncias) em um diagrama de classes.
- ![[Pasted image 20260902112357.png]]
- **Ternárias ou N-árias**: é um relacionamento que conecta **três classes** simultaneamente em uma única conexão lógica.
- ![[Pasted image 20260902113800.png]]
- **Agregação**: é um tipo de relacionamento fraco do tipo "todo-parte", onde um objeto contém outro, mas ambos podem existir de forma independente.
- ![[Pasted image 20260902113309.png]]
- **Composição**: só faz sentido a parte existir se o todo também existe.
- ![[Pasted image 20260902114433.png]]
- **Classe associativa:** utilizada para modelar informações e comportamentos que pertencem especificamente ao **relacionamento** entre duas outras classes.
- ![[Pasted image 20260902114955.png]]
- **Herança (ou generalização):** representado por uma seta branca.
- ![[Pasted image 20260902115130.png]]
- **Associação de dependência**: mostra que a relação é fraca, indireta ou ocorre apenas em momentos específicos. Isso acontece quando uma classe recebe a outra como parâmetro em um método ou cria uma instância dela internamente.
- ![[Pasted image 20260902120447.png]]
- **Navegabilidade**: define a direção em que os objetos conseguem "enxergar" ou acessar os dados e métodos de outra classe associada. Os tipos de navegabilidade são:
	 -  **Unidirecional:** Ocorre em uma única direção. É representada por uma linha com uma **seta aberta** na ponta da classe destino (ex: `Cliente` ➔ `Pedido`). Apenas a classe de origem conhece a classe de destino.
	 - **Bidirecional:** Ocorre em ambas as direções. É representada por uma linha simples **sem setas**. Tanto a classe `A` conhece a `B`, quanto a classe `B` conhece a `A`.
## Qual a diferença entre classe persistente e transiente?

Classe persistente é capaz de guardar seu estado e classe transiente é destruída ao final da sessão.