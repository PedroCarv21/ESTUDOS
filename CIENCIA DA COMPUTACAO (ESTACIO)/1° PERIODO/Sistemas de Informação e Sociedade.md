
# Exemplos de como as empresas utilizam sistemas de informação

- **Automatização de processos repetitivos.**
- **Análise de dados.**
- **Comunicação.**

# O que é o Diamante de Leavitt?

É a estrutura dos sistemas de informação dentro das empresas, sendo formado por quatro elementos:

![[Pasted image 20260313184727.png]]

- **Tarefa:** atividades necessárias para a produção de um bem ou serviço.
- **Pessoa:** Representa o capital humano, incluindo habilidades e conhecimentos.
- **Estrutura:** Envolve a hierarquia, autoridade e o fluxo de trabalho organizado.
- **Tecnologia:** compreende o hardware, software e equipamentos de telecomunicações utilizados para processar e armazenar informações.

# O que são mainframes?

Computadores de altíssimo desempenho voltados para processar grandes volumes de dados e transações críticas simultâneas com máxima segurança.

# O que é batch?

Batch (ou processamento em lote) é um modo de executar grandes quantidades de processamento automaticamente, sem interação humana, normalmente processando muitos registros de uma vez.

Em vez de executar uma operação registro por registro com um usuário interagindo, o sistema:

- recebe um conjunto de dados.
- executa um programa sobre todos os dados.
- gera resultados ou arquivos de saída.

# O que é arquitetura monolítica?

Neste modelo, todos os módulos, regras de negócio e interface do usuário são desenvolvidos e implantados juntos como um único serviço. 

**Funcionamento:** A interface, lógica de negócios e acesso a dados rodam no mesmo processo e geralmente na mesma máquina. Essa arquitetura **usa armazenamento em batch**.

# Qual a diferença entre arquitetura cliente-servidor e monolítica?

- **Cliente-Servidor** foca na **distribuição de responsabilidades** (quem pede x quem processa), geralmente em máquinas diferentes.
- **Monolítica** foca na **unificação do código**, onde tudo roda como uma única unidade em um só local.


# Quais são os 3 componentes de uma arquitetura de aplicações?

- **Interface (GUI)**: sempre fica no lado do cliente.
- **Lógica:** pode ficar no lado do cliente (se for um 'cliente gordo' e um 'servidor magro' ) ou no lado do servidor (se for um 'cliente magro' e um 'servidor gordo' ).
- **Dados:** sempre fica no lado do servidor.

![[Pasted image 20260313222925.png]]

# Qual a diferença entre World-Wide-Web e Internet?

**Internet**
- É a **infraestrutura de rede mundial** que conecta computadores e servidores.
- Permite vários serviços: e-mail, FTP, jogos online, streaming, etc.

**World Wide Web (WWW)**
- É **um dos serviços que funciona sobre a internet**.
- Consiste em **páginas e sites acessados por navegadores** usando links (HTTP/HTTPS).

**Resumo:**
- **Internet** = a **rede global de computadores**
- **World Wide Web** = **sistema de páginas e sites que usa a internet**

# O que são as 5 forças de porter?

São um modelo de análise da competitividade entre empresas de um mesmo segmento de mercado.

As 5 forças são:

- **1° Rivalidade entre os concorrentes:** disputa entre as empresas para atrair o público de um mesmo **mercado-alvo.**
- **2° Ameaça de produtos substitutos:** produtos substitutos são aqueles que atendem às mesmas necessidades ou realizam as mesmas funções que outras mercadorias, podendo ser utilizados como alternativas a elas.
- **3° Ameaça de entrada de novos concorrentes:**  nível de **dificuldade para novos concorrentes** entrarem no seu mercado.
- **4° Poder de negociação dos clientes:**  Avalia a capacidade dos clientes de pressionar por preços mais baixos ou maior qualidade
- **5° Poder de negociação dos fornecedores:** quanto maior for o poder de negociação de um fornecedor, mais fácil é para ele elevar os preços.

# Quais são os tipos de sistemas da informação?

- **Sistema de apoio executivo (ESS):** Esse sistema é usado por **diretores e executivos**, ajudando na **tomada de decisões estratégicas de longo prazo**. Nível: Estratégico (topo da pirâmide)
- **Sistemas de apoio à decisão (DSS):** Esses sistemas ajudam gestores a tomar **decisões mais complexas**, através da análise de informações e simulações. Nível: Gerencial/analítico
- **Sistemas de informação gerencial (MIS):** a principal pergunta que esse tipo de sistema deve responder é: tudo está funcionando corretamente? Sua função é **resumir** e **relatar** operações comerciais essenciais usando dados fornecidos por sistemas de processamento de transações. Nível: Gerencial (gerentes de nível médio)
- **Sistema de processamento de transações (TPS):** Esse sistema registra e processa as **operações do dia a dia da empresa**. Nível: Operacional (base da pirâmide)

![[Pasted image 20260314164615.png|578]]


# Em quais situações é mais comum uma situação estruturada e uma situação não estruturada?

Decisões estruturadas são mais comuns em níveis mais baixos da organização, enquanto problemas não estruturados são mais comuns em níveis de negócios mais altos. Quanto mais estruturada for a decisão, mais fácil será automatizar.

Exemplos de decisões por nível gerencial:

- **Topo:** decidir se quer ou não entrar no mercado.
- **Intermediária:** desenhar um plano de marketing.
- **Operacional:** determinar as horas extras.

# O que são controles de sistema de informação?

São procedimentos que garantem que os sistemas de informação funcionem de modo seguro.

Exemplos: controle de acesso, controle de gerenciamento de mudança (garantindo que mudanças no sistema de informação sejam planejadas, testadas e implementadas adequadamente) e controle de buckup e recuperação, garantindo que os dados da organização sejam devidamente processados e possam ser recuperados em caso de emergência.

# O que são controles gerais e de aplicativos?

- **Gerais:** se aplicam às atividades do sistema de informação em toda a organização. Exemplo: medidas administrativas que restringem o acesso dos funcionários apenas aos processos diretamente relevantes para suas funções
- **Aplicativos:** são específicos para um determinado aplicativo. Exemplo: validação de dados de entrada e registro de acessos ao sistema.

# O que é backbone?

Backbone, ou "espinha dorsal", é a infraestrutura central de rede de alta capacidade que interliga diferentes redes menores, provedores de internet e data centers, transportando grandes volumes de dados.

# Por onde a maior parte dos dados trafegam?

Eles trafegam por meio de cabos submarinos. **Esses são exemplos de backbones.**

# Quais são os tipos de infraestrutura que visam simplificar o data center unificando computação, armazenamento e rede?

- **Convergente (CI):** junta servidores, storage e rede em um único sistema pré-configurado. Mesmo estando tudo no mesmo “pacote” (conjunto de equipamentos que já vêm juntos, integrados e prontos para uso), os componentes ainda são independentes:
	- Você tem um servidor (processamento).
	- Um storage dedicado (armazenamento).
	- Equipamentos de rede.

Em resumo: cada um desses é um hardware próprio, com função específica.
- **Hiperconvergente (HCI):** tudo é integrado via software (computação, armazenamento e rede). Usa servidores comuns e transforma tudo em um sistema único.

Estas são as características de ambas:

![[Pasted image 20260320192519.png]]

# Quais são as melhores práticas para gerenciamento de infraestrutura?

- Monitoramento contínuo.
- Backup
- Utilização de serviços em nuvem.
- Cultura de segurança.

# O que é Planejamento de recursos empresariais (ERP)?

É um software de gestão que integra todas as áreas de uma empresa — finanças, RH, estoque, vendas e produção — em um único banco de dados, centralizando informações para otimizar processos e facilitar a tomada de decisão, em vez de as informações que antes eram fragmentadas em vários sistemas diferentes.

É possível ter tanto ERPs on-premise quanto on-cloud.

Exemplo: um ERP identificou que uma matéria-prima foi encaminhada ao setor de produção e, por conta disso, retirou esse item do estoque e atualizou o setor de compras.

![[Pasted image 20260321111123.png]]

## Vantagens

- **Centralização de dados.**
- **Aumento da produtividade.**
- **Redução de custos.**

## Desvantagens

- **Dependência do fornecedor do ERP.**
- **Customizar o ERP de acordo com o padrão organizacional da empresa.**
- **Cada departamento se torna dependente um dos outros.**

# O que é a gestão de relacionamento com o cliente ou Client Relationship Management (CRM)?

Sistema para gerenciar todos os relacionamentos comerciais e interações com clientes existentes e potenciais dentro de uma empresa. 

O CRM utiliza as informações dos clientes para conhecê-los melhor e oferecer a eles no momento certo aquilo que precisam.
## Vantagens

- **Maior controle de vendas e prospecções.**
- **Melhora o relacionamento com os clientes e a equipe.**
- **Maior gestão do tempo.**

## Funcionalidades

- **Gestão de dados dos clientes.**
- **Captura de dados via e-mail.**
- **Automatização de tarefas repetitivas.**

## Tipos de CRM

- **Operacional:** foca nas tarefas do dia a dia dos vendedores e no atendimento aos clientes.
- **Colaborativo:** os dados analíticos são acessados de **forma integrada**, o que melhora a gestão do negócio.
- **Analítico:** traz os dados para você analisar a performance dos vendedores.
- **Estratégico:** inclui todas as funções anteriores.

# O que é Gestão da cadeia de suprimentos ou Supply Chain Management (SCM)?

Gerenciamento de todo o fluxo de produção de um bem ou serviço ‒ desde os componentes brutos, matérias-primas, até a entrega do produto acabado, final, ao consumidor. Isso permite tomar decisões mais estratégicas como: corte de custos, otimização de processos, etc.
## Processo de gestão

![[Pasted image 20260321130558.png]]

- **Planejamento:** define demandas, recursos e estratégias para atender aos requisitos do mercado.
- **Aquisição:** envolve a compra de materiais e serviços.
- **Produção:** trata-se da transformação dos materiais em produtos acabados.
- **Logística:** abrange tanto o armazenamento quanto o transporte dos produtos.
- **Gestão de retornos:** envolve a devolução dos produtos.

## Pilares do SCM

- **Produto:** inclui compra de matéria-prima, fabricação, armazenamento e entrega.
- **Finanças:** envolve pagamentos, cobranças e toda atividade relacionada ao fluxo de caixa.
- **Informações:** troca de informações entre as pessoas envolvidas.

## Benefícios

- **Mais fácil fazer levantamento de dados com uma cadeia integrada.**
- **Planejamento logístico é mais simples.**
- **Facilita o gerenciamento de estoque.**


# O que é Sistema de gestão do conhecimento ou knowledge management system (KMS)?

 É uma plataforma de software projetada para capturar, organizar e compartilhar conhecimento dentro de uma organização. Ele centraliza informações, como documentos, facilitando o acesso rápido e tomada de decisão.

# O que é Business Intelligence (BI)?

Combina análise de negócios, mineração de dados, visualização de dados e práticas recomendadas para ajudar as organizações a tomar decisões baseadas em dados. 

## Quais são as quatro etapas?

- **Coletar e processar dados de várias fontes.**
- **Descobrir tendências e inconsistências.**
- **Visualizar para apresentar descobertas.**
- **Agir com base nos insights em tempo real.**


# Quem liberou os indígenas da escravidão?

Marques de Pombal em 1757.

# Quando começa a colonização portuguesa?

A colonização propriamente dita começa a partir de **1534**, quando o **território brasileiro é dividido em capitanias hereditárias doadas a donatários** que poderiam explorar e proteger o espaço, além de iniciar o plantio da cana-de-açúcar.

# Qual grupo descobriu o ouro e o diamante no Brasil?

Bandeirantes no século XVII.

# Em quais regiões foram descobertas as primeiras minas?

Regiões dos atuais estados de Minas Gerais, Goiás e Mato Grosso. 
# Em qual ano foi a chegada da família real no Brasil?

1808.
# Quais outros povos europeus tentaram invadir o Brasil?

Franceses e holandeses.

# Quais as teorias do século XIX foram utilizados por pensadores brasileiros para descrever o atraso social do Brasil em relação a outros países?

- **Positivismo**: propõe a ideia de uma ciência sem teologia ou metafísica, baseada apenas no mundo físico/material.
- **Darwinismo social**: sugere que existiriam comportamentos e características biológicas que determinariam que uma pessoa é superior a outra e aptas ao desenvolvimento social.
- **Evolucionismo social**: acreditavam que as sociedades tiveram início em um estado primitivo e gradualmente tornaram-se mais civilizadas com o passar do tempo.

# O que é um coloralismo?

O colorismo é um processo que separa indivíduos com base no tom de sua pele.

# O que foi o movimento antropofágico?

Buscava promover pensamentos para “engolir” uma cultura estrangeira e, a partir dela, promover uma nova cultura com a cara do país, excluindo o eurocentrismo.

# A literatura indianista brasileira teve dois nomes importantes. Quais?

José de Alencar e Gonçalves Dias.

# O que afirma os artigos 231 e 232?

O reconhecimento dos índios quanto a sua organização social, costumes, crenças e tradições, e os direitos originários sobre as terras que tradicionalmente ocupam.

# O que diz a Lei n° 10.639/2003?

Estabelece as diretrizes e bases da educação nacional, para incluir no currículo oficial da Rede de Ensino a obrigatoriedade da temática "História e Cultura Afro-Brasileira", e dá outras providências.

# Qual lei tornou o racismo crime?

Lei nº 7.716/1989.

# Quais os três principais aspectos da biodiversidade?

Riqueza de espécies, diversidade genética e de ecossistemas.

# Qual a importância ambiental da biodiversidade?

Essencial para a manutenção do correto funcionamento dos processos ambientais. A extinção de uma única espécie pode levar à degradação de todo o ambiente.

# Qual a importância econômica da biodiversidade?

Está associada aos produtos e serviços que dela são retirados e utilizados pela espécie humana, de forma **direta** (espécies utilizadas diretamente pela população humana), **indireta**  (espécies que, de forma indireta, beneficiam os humanos, como a abelha com a polinização) ou **potencial** (não possuem uma utilidade atual para o ser humano, mas podem ter sua utilidade descoberta no futuro).

# O que torna o Brasil um país megadiverso?

Distintos biomas, diferentes zonas climáticas e enorme costa marinha.

# O que são os hotspots?

Regiões com alta incidência de espécies endêmicas ameaçadas de extinção.

# Como o Conselho Nacional do Meio Ambiente (CONAMA) define impacto ambiental?

Toda alteração causada pela ação humana que provoque alterações nos ambientes naturais. Há dois tipos:
- **Positivo:** buscam corrigir um dano ambiental já existente (ex.: reflorestamento).
- **Negativo:** provocam a degradação de um ambiente natural.

# Quais são uma das classificações do impacto ambiental?

- **Direto:** causa e consequência se relacionam de forma direta. Ex: jogar lixo no rio impacta na qualidade da água.
- **Indireto:** causa e consequência não se relacionam de forma direta. Ex: jogar lixo no rio pode provocar, de forma indireta, a diminuição da quantidade de peixes.

# O que é efeito de borda? 

Conjunto de alterações físicas (luz, vento, umidade) e biológicas (espécies, interações) que ocorrem nas margens de um fragmento florestal quando ele é isolado por atividades humanas.

# O que é o efeito estufa?

O efeito estufa é um fenômeno natural essencial que retém o calor do sol na atmosfera, mantendo a Terra aquecida. Gases como, metano e vapor d'água agem como um "cobertor". A queima de combustíveis fósseis e desmatamento aumentam essa concentração, intensificando o efeito, causando aquecimento global e mudanças climáticas.

# O que é acidificação da água?

Ocorre pela absorção de gás carbônico pela água. Esses gases são oriundos da atividade antrópica e causam uma alteração do pH dos mares e oceanos. O resultado é alteração na ciclagem dos nutrientes.

# Qual o principal mecanismo de prevenção de impactos ambientais no Brasil?

Mecanismos de licenciamento ambiental.

# O que é sustentabilidade?

É a capacidade de suprir as necessidades do presente sem comprometer a capacidade das gerações futuras de satisfazerem as suas próprias necessidades. 

# Quais são os 3 pilares da sustentabilidade?

- **Social (ou sociopolítica):** busca-se que todas as pessoas tenham recursos para uma vida saudável e de qualidade.
- **Econômica (ou ecoeficiência):** busca pelo desenvolvimento econômico que causem menos impactos ao meio ambiente
- **Ambiental (ou ecológica):** manutenção da biodiversidade e dos processos ambientais.

# Quando foi utilizado a palavra sustentabilidade pela primeira vez?

Relatório Brundtland - 1987
# O que é Agenda 21?

A agenda 21 foi o primeiro programa internacional que buscava o desenvolvimento sustentável em âmbito global.

# Quais são alguns dos objetivos da Agenda 21 no Brasil?

Objetivo 1. Produção e consumo sustentáveis contra a cultura do desperdício.
Objetivo 7. Promover a saúde e evitar a doença, democratizando o SUS.
Objetivo 11. Desenvolvimento sustentável do Brasil rural.

# O que é a Agenda 2030?

Esse programa possui 17 objetivos principais relacionados ao desenvolvimento sustentável em âmbito global e substituiu a Agenda 21.

# Quando a Declaração Universal dos Direitos Humanos foi adotada pela ONU?

1948.

# O que inspirou a ONU a criar essa declaração?

As duas guerras mundiais.
# Características dos direitos humanos

- **Universalidade:** estar disponíveis para todos os membros da família humana igualmente, sem restrições para ninguém.
- **Interdependência:** a existência de um direito está condicionada à existência de todos os demais. Nenhum direito é mais importante do que os outros.
- **Indivisibilidade:** Não pode haver uma divisão dos direitos humanos em categorias. É preciso entendê-los e respeitá-los como um todo.
# Quais direitos são reconhecidos pela ONU como inalienáveis?

Justiça, paz e liberdade.
# O que foi a crise do absolutismo?

Foi o descrédito na tese de que um governante soberano com todos os direitos concentrados em suas mãos. Isso ocorreu nos séculos XVII e XVIII.

# Quais foram os dois principais documentos que materializaram a noção de direitos básicos para todos?

- **Declaração de Independência (Estados Unidos)**: 
	- **Causa**: insatisfação dos colonos americanos com os abusos da Inglaterra, principalmente no final da **Guerra dos Setes Anos**, obrigados a **pagar dívidas inglesas** e a obedecer a **ordens autoritárias** da metrópole.
	- **Dizeres da carta**: anuncia que todos os homens são **criados iguais por Deus** e que recebem Dele direitos que não lhes deveriam ser retirados: a vida, a liberdade e a busca da felicidade. Essa carta foi feita em 1776 e se tornou oficial em 1787.
- **Declaração dos Direitos do Homem e do Cidadão (Revolução Francesa)**:
	- **Causa**: insatisfação do povo com o governante Luís XVI, que **aumentou os impostos** cobrados da população, mas manteve as **classes privilegiadas isentas** de contribuição.
	- **Dizeres:** defendeu que a ignorância ou o menosprezo aos direitos dos homens eram a razão da difícil situação em que o povo se encontrava e que, para mudar a situação, era necessário defender de forma solene os direitos considerados naturais e inalienáveis. Ela foi criada em 1789.
# O que é o Estado de Direito?

Sistema jurídico-político onde todos, incluindo governantes e instituições, estão submetidos às leis, garantindo direitos fundamentais e evitando o arbítrio. Ele surgiu através dos **filósofos iluministas** e esse período ficou conhecido como **era dos direitos**.

# Quais foram as 3 filosofias que influenciaram os direitos humanos?

- **Jusnaturalismo:** o direito é visto como algo **intrínseco e natural** ao ser humano, funcionando antes mesmo de ser legalizado pelas constituições ou pelo Estado.
- **Positivismo:** os direitos não são elementos naturais em uma sociedade. Eles seriam o resultado de discussões e entendimentos do Estado, que decide pela oficialização e legalização de certas normas.
- **Moralismo:** defende que os direitos são normas que não precisam ser oficializadas em leis e constituições para terem validade. Sua importância está diretamente relacionada às necessidades e valores da sociedade em que estão inseridos.

# Quais foram opiniões de Hannah Arendt?

Propôs que ocorreu uma ruptura nos direitos humanos não apenas devido aos regimes totalitários e também devido às **políticas imperialistas** praticadas.

Para Arendt, o grupo dos apátridas foi o que teve a situação mais angustiante, pois, além de terem perdido seus direitos, eles não eram reconhecidos como iguais perante a lei, já que a lei nem existia mais para eles.

Segundo Arendt, seria necessário garantir que todos os homens e mulheres, sem condições ou exceções, obtenham proteção jurídica na mesma medida que todos os demais. O indivíduo deveria ser reconhecido como **cidadão do mundo** ou, como foi dito na declaração da ONU, membro da família humana, sem distinção entre nativo e estrangeiro.

# Quais são os críticos do universalismo?

Surge a preocupação de que existe um grupo que presume entender sozinho as necessidades globais e pode decidir unilateralmente o que é necessário para garantir uma vida digna, sem consultar aqueles que serão afetados por esses direitos. Isso sugere que um grupo ou cultura possa tutelar o mundo em detrimento de outros.

# O que defende Sousa Santos?

Um dos **principais defensores do multiculturalismo**, que é natural que todas as culturas vejam seus próprios princípios como os mais corretos, algo que deveria ser respeitado pelos outros ou não seriam cultivados.

# Quando foi que o Brasil adotou a ideia da ONU de que todos os seres humanos nascem livres e iguais?

Constituição de 1988.
# Quais os fundamentos da Republica Federativa do Brasil segundo Carta Magna?

Soberania, Cidadania e Dignidade da pessoa humana (**condições mínimas necessárias** para que alguém viva uma vida justa).

# Quais continentes não tem comitês regionais da ONU?

Ásia e da Oceania

# O que é a Constituição Cidadã?

Foi redigida para superar as restrições aos direitos durante o regime militar, restaurar a democracia e promover a redução da desigualdade social e o combate à corrupção.

# Quais são alguns dos tratados internacionais da ONU que o Brasil possui compromisso?

1. Pacto Internacional dos Direitos Econômicos, Sociais e Culturais  
     
2. Pacto Internacional dos Direitos Civis e Políticos  
     
3. Convenção sobre Eliminação de Todas as Formas de Discriminação Racial

# Como foi a construção dos direitos humanos em cada geração?

- **Primeira:** Representada pelas declarações americana e francesa, o foco principal era a conquista da liberdade individual em oposição aos Estados absolutistas.
- **Segunda:** reafirmou a liberdade da primeira geração e buscou a igualdade, promovendo a ideia de uma família humana.
- **Terceira:** A partir dos anos 1960, concentrou-se nos direitos coletivos. Enfatizou-se a proteção do meio ambiente (ex.: Floresta Amazônica), o direito à paz e o compartilhamento equitativo de conhecimento, tecnologia e cultura.