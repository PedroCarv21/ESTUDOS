
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


