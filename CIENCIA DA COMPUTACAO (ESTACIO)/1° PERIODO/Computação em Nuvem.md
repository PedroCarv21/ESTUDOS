
# Quais são os tipos de implementação da computação em nuvem?

- **Pública:** é acessível em toda internet. As vantagens são: 
	- A divisão da infraestrutura entre vários clientes acaba diluindo o custo de aquisição.
	- São simples a contratação dos serviços e a implementação na empresa.
	Já as desvantagens são: 
	- Menor segurança.
	- Você não é o proprietário do hardware nem dos serviços, não poderá gerenciá-los como deseja
- **Privada:** restrita apenas aos funcionários ou parceiros de negócio, sendo propriedade de uma empresa. Ela é a melhor opção para empresas que precisam manter seus dados seguros e permite a construção de uma infraestrutura mais alinhada com a vontade do dono. Já as desvantagens são: custo inicial e a necessidade de uma equipe de TI própria.
- **Híbrida:** é composta por uma nuvem pública e uma privada, possibilitando a transmissão de dados entre elas. Alguns serviços são hospedados na nuvem privada, enquanto outros na nuvem pública.
- **Comunitária:** são compartilhadas por diversas empresas que possuem interesses comuns, como os requisitos de segurança, políticas, entre outros. Nesse modelo, a nuvem comunitária pode ser administrada tanto pela própria organização ou por terceiros.
- **Distribuida:** se caracteriza pela possibilidade de ser acionada em diferentes localidades, mas possui servidores conectados a uma única rede.

# Quais são os principais serviços oferecidos pela computação em nuvem?

- **Infraestrutura como serviço (IaaS):** fornece recursos brutos de computação (servidores, rede, armazenamento) onde você gerencia o SO e aplicativos. O provedor de serviço é responsável por manter a infraestrutura do datacenter que hospedará as máquinas virtuais dos usuários. Exemplo: máquina virtual da Azure da Microsoft.
- **Plataforma como serviço (PaaS):** a responsabilidade do usuário diminui e aumenta a do provedor. O provedor é responsável por entregar todos os recursos de hardware e software necessários para que o usuário possa construir seus aplicativos. O código e os dados gerados pela aplicação são responsabilidade do usuário. Exemplo: Google App Engine.
- **Software como serviço (SaaS):** refere-se ao software que é executado e gerenciado na nuvem, sendo assim executado em um banco de dados remoto.é aquele com o qual o usuário tem menor responsabilidade, bastando apenas se conectar aos aplicativos disponibilizados e utilizar. Ao contrário, o provedor de serviços é o que tem maior responsabilidade. Ele é responsável por gerenciar toda a pilha de aplicativos, desde o hardware, passando pelos sistemas operacionais, até o aplicativo. Exemplo: Office 365.

# Quais são as tecnologias habilitadoras da computação em nuvem?

- **Virtualização:** permite criar versões virtuais de recursos físicos — como servidores, sistemas operacionais, armazenamento e redes — para que possam ser usados de forma mais eficiente e flexível na nuvem. Assim, a virtualização permite que **várias máquinas virtuais (VMs)** funcionem no mesmo hardware físico, cada uma operando como se fosse um computador independente.
- **Conteinirização:** virtualiza apenas a aplicação e suas dependências, sendo que esta virtualização está em nível de sistema operacional. Ou seja, a conteinirização é mais leve, pois integra apenas a configuração da sua aplicação e não da máquina inteira. Exemplo: Docker.
- **Computação sem servidores:** situação em que o gerenciamento do servidor se torna um trabalho do provedor da nuvem. Sendo assim, você só se preocupa com o código, e não mais com a infraestrutura do servidor. Entre os pontos positivos estão:
	- **Baixo custo:** só vai pagar aquilo que realmente está utilizando.
	- **Redução de código:** não são necessárias configurações adicionais para aproveitar a escalabilidade da arquitetura.

# Quais são as vantagens e desvantagens da computação em nuvem?

- **Vantagens:** só paga pelo que consumiu do serviço, aumento da infraestrutura conforme o aumento do seu negócio de forma mais eficiente do que seria com a compra de novos servidores.
- **Desvantagens:** necessidade de acesso a internet, exposição de dados da empresa e diminuição da segurança.

# Quais são as características essenciais da computação em nuvem segundo o NIST (National Institute of Standards and Technology)?

- **Autoatendimento sob demanda (on-demand self-service):** o usuário tem acesso a plataforma para configurar recursos como servidores e redes de armazenamento, de forma automática e sem depender do provedor de serviço em núvem.
- **Amplo acesso à rede (broad network access):** os recursos computacionais devem estar acessíveis a internet.
- **Agrupamento de recursos (resource pooling):** os recursos de computação do provedor são agrupados para atender a vários consumidores usando um modelo multilocatário, ou seja, os recursos computacionais são compartilhados entre diversos usuários, os quais não precisam ter conhecimento acerca da localização dos recursos que estão utilizando.
- **Elasticidade dinâmica (rapid elasticity):** a capacidade dos recursos podem ser aumentadas ou diminuídas de acordo com a demanada.
- **Serviço mensurável (measured service):** a capacidade de medir exatamente quais recursos estão sendo usados, monitorar e controlar esses serviços para podermos posteriormente apresentar esses dados ao cliente ou ao usuário final.

# Qual a diferença entre a infraestrutura on-premise e em nuvem?

Ambas as arquiteturas armazenam e integram os dados e os serviços de uma empresa. No entanto, as diferenças se encontram em:

- **Tipo de servidor:** no on-premise, o servidor é físico, pois existe um servidor principal instalado na empresa na qual os computadores estão conectados. Já na nuvem, dados e os serviços estão na nuvem, ou seja, estão guardados em um provedor de nuvem, uma empresa especializada com poder computacional disponível para alugar.
- **Forma de acesso:** no on-premise, o acesso aos dados só é possível se o computador estiver devidamente e interligado ao servidor principal. Já em nuvem, o acesso é realizado pela plataforma disponibilizada pelo provedor de nuvem; o acesso é sempre remoto e por meio de uma conexão com a internet.
- **Flexibilidade de armazenamento:** no on-premise, no caso de uma necessidade de crescimento, será necessário adquirir softwares e hardwares. Já em nuvem, ao se contratar os recursos do provedor de nuvem, é possível aumentar ou diminuir o espaço consumido. Assim, a flexibilidade se torna mais rápida e mais barata.

# O que é virtualização?

A virtualização é a tecnologia que permite que diversas aplicações e sistemas operacionais sejam processados em uma mesma máquina. Isso possibilitou o datacenter das empresas trabalhar com inúmeras plataformas de sistemas operacionais, sem a necessidade do aumento no número de servidores físicos. Ou seja, a virtualização permite um alto nível de flexibilidade e portabilidade.

# O que é hypervisor?

É o software responsável por criar, gerenciar e executar máquinas virtuais (VMs) em um computador físico, atuando como uma camada intermediária entre o hardware físico e os sistemas operacionais das máquinas virtuais. Há dois tipos de hypervisores:

- **Tipo 1 (bare metal ou stand alone):** roda diretamente no hardware, sem sistema operacional intermediário. Exemplo: Microsoft Hyper-V.
- **Tipo 2(hosted):** roda sobre um sistema operacional existente (exemplo é o VirtualBox):

```
Hardware
   ↓
Sistema Operacional (Windows / Linux)
   ↓
Hypervisor
   ↓
Máquinas Virtuais
```

Há também os conceitos de:

- **Virtualização total:** o hypervisor simula completamente o hardware real (CPU, memória, disco, placa de rede etc.), fazendo com que o sistema operacional acredite que está rodando em um computador físico.
- **Paravirtualização:** Na paravirtualização, o sistema operacional convidado sabe que está rodando em um ambiente virtualizado. Por causa disso, ele se comunica diretamente com o hypervisor através de chamadas especiais (hypercalls) em vez de tentar acessar o hardware virtualizado.

![[Pasted image 20260305192459.png]]

# O que é um container?

É uma técnica de virtualização que permite **empacotar uma aplicação junto com todas as suas dependências** (bibliotecas, configurações, runtime etc.) dentro de um **container**, para que ela rode **de forma isolada e consistente em qualquer ambiente**. 

Diferente das máquinas virtuais, que inclui **sistema operacional + aplicação**, o container inclui apenas **aplicação + dependências**, compartilhando o SO.

Os **cloud containers** nada mais são do que containers que rodam em servidores na nuvem.

# O que é Provedor de serviços de aplicação (ASP)?

Formato de terceirização que fornece software e aplicações por meio da internet para usuários finais, pequenas e médias empresas ou até grandes organizações. 

Em vez de as organizações arcarem com os encargos financeiros, os requisitos de hardware e os conhecimentos técnicos necessários para possuir o software, eles alugam esses aplicativos de terceiros.

# O que é Grid e utility computing?

- **Grid (computação em grade):** tipo de sistema paralelo e distribuído que permite o compartilhamento, seleção e agregação de recursos geograficamente distribuídos dinamicamente e em tempo de execução dependendo da sua disponibilidade, capacidade, performance, custo e requerimentos dos usuários.
	- **Diferença entre cluster e grid:** cluster são vários computadores próximos (conectados na mesma rede local) funcionando como um único supercomputador. Já o grid são computadores espalhados em diferentes lugares colaborando para resolver um problema.
- **Utility (computação de utilidade pública):** modelo classificado como computação sob demanda, pois o usuário pode contratar software, hardware e serviços conforme sua necessidade de utilização e em função de fatores como picos, quedas e conforme o período de uso.

# Quais são as camadas da infraestrutura em nuvem?

- **Servidor:** inclui servidores virtuais, servidores físicos ou um híbrido dos dois.
- **Armazenamento:** inclui sistemas de arquivo, banco de dados e outros tipos de armazenamento.
- **Rede:** inclui serviços de conectividade, segurança e gerenciamento de aplicativos.

# O que é middleware?

**Middleware** é um **software intermediário** que fica **entre duas partes de um sistema** — normalmente entre o **cliente (frontend)** e o **servidor ou lógica principal (backend)** — para **processar, modificar ou controlar as requisições e respostas**.

Em outras palavras: ele funciona como **uma camada no meio do caminho** que pode executar tarefas antes ou depois de uma ação principal.

```
Usuário → Middleware → Servidor
        ←           ←
```

# Quais são os dois modelos de datacenters?

- **PDC (PRIVATE DATACENTER):** infraestrutura física, localizada dentro da própria empresa (on-premises) ou gerenciada exclusivamente para ela, garantindo controle total.
- **IDC (INTERNET DATACENTER):** centro de dados de terceiros, acessível pela internet, focado em escalabilidade e recursos compartilhados.

# Quais são os outros tipos de classificações para os datacenters?

- **Mega:** estruturas gigantes com centenas de milhares de servidores. São usados por grandes empresas de tecnologia.
- **Micro:** é uma versão compacta de um datacenter tradicional. São usados por pequenas empresas.
- **Nano:** é ainda menor que um micro, podendo ter apenas alguns servidores. São usados em Redes IoT.
- **Baseado em container:** Esse modelo usa containers físicos (tipo contêiner de transporte) como módulos de datacenter. Cada container inclui: servidores, rede, energia, refrigeração. Ou seja: um datacenter completo dentro de um container.

# Quais são os componentes principais do back-end?

Aplicação, serviços, cloud runtime (execução na nuvem), armazenamento, infraestrutura, gerenciamento e segurança.

# Quais são as camadas da arquitetura em nuvem?

- **Infraestrutura:** é através dela que os provedores de infraestrutura disponibilizam os serviços de rede e armazenamento da nuvem. Fazem parte desta camada: servidores, sistema de armazenamento, datacenters e roteadores.
- **Plataforma:** provê serviços para que as aplicações possam desenvolvidas, testadas e implementadas no ambiente da nuvem.
- **Aplicação:** oferece diversas aplicações como serviço para os usuários.

# Quais são os tipos de serviço em nuvem?

- **Serviços de armazenamento na nuvem:** Permitem aos usuários armazenar e acessar arquivos, independentemente da localização física.
- **Serviços de computação na nuvem:** Permitem computação em escalas variadas, desde servidores virtuais até clusters de computadores.
- **Serviços de infraestrutura na nuvem:** Permitem aos usuários acessar servidores e serviços de rede, como VPNs e firewalls.
- **Serviços de plataforma na nuvem:** Permitem aos usuários criar, implantar e gerenciar aplicativos através de um ambiente baseado na nuvem.
- **Serviços de análise na nuvem:** Permitem aos usuários processar, analisar e gerenciar grandes quantidades de dados.
- **Serviços de desenvolvimento na nuvem:** Permitem aos usuários criar aplicativos baseados na nuvem por meio de uma interface de programação de aplicativos (API).

# O que é datalake?

Vasto reservatório onde dados de todas as formas e tamanhos são armazenados em seu estado bruto (significa guardar as informações exatamente como foram coletadas, sem qualquer tipo de processamento, filtragem, organização ou transformação).
# O que é edge computing?

Abordagem de computação de borda que permite que os dados sejam processados e **armazenados localmente**, em vez de forma remota. Isso diminui o tempo de latência (atraso entre o envio de um dado e a sua recepção) e aumenta a confiabilidade da conexão.

O processamento dos dados é feito de forma local e separa aqueles que podem ser processados ali mesmo, diminuindo o tráfego de dados e a necessidade de enviá-los. Apenas uma parte dos dados é enviada para a nuvem, por isso o nome computação de borda.

# Quais são as 7 estratégias de migração para a nuvem, também conhecidas como 7Rs?

- **Rehost (Re-hospedar):** também conhecida como lift and shift, onsiste em mover aplicações, infraestrutura e dados para um ambiente de nuvem, mantendo intactas as suas configurações.
- **Replatform (Replataforma):** relacionado ao caso de sistemas legados, onde muitas organizações possuem sistemas estruturados demais para migrar para plataformas de nuvem IaaS ,esta estratégia permite que se façam algumas alterações de configuração para melhor se adequar ao ambiente de nuvem, sem alterar a arquitetura principal.
- **Repurchase (Recompra):** conhecida como uma estratégia de marketing em que uma empresa incentiva seus clientes a comprar novamente seus produtos ou serviços. Ela envolve oferecer descontos, ofertas especiais, programas de fidelidade e outras formas de recompensar os clientes por sua lealdade.
- **Refactoring/Re-architecting (Refatorar/Rearquitetar):** Consiste em desenvolver os sistemas do zero para torná-los nativos da nuvem. Essa estratégia permite aproveitar todo o potencial das tecnologias.
- **Retire (Aposentar):** está relacionada à desativação ou ao desligamento dos serviços (workloads) que não são mais necessários. Sua desativação permite que a organização se concentre em áreas que oferecem mais valor comercial, economizando recursos.
- **Retain (Reter):** também conhecida como revisit, é a estratégia de refatorar algumas áreas críticas de seus ativos digitais antes de migrar para a nuvem.
- **Relocate (Realocação):** Assim como na re-hospedagem, o software em execução nas máquinas virtuais migradas permanece inconsciente de que algo mudou. Nesse caso, no entanto, as ferramentas e os processos operacionais existentes também podem ser mantidos, mesmo que dependentes de produtos de terceiros.

# O que é o balanceamento de carga?

Processo que ajuda a distribuir o tráfego de uma aplicação entre vários servidores para garantir que todas as solicitações sejam servidas de forma eficiente.

# Dentro do contexto de segurança da computação em nuvem, quem fica responsável por trazer a segurança?

Depende, conforme se vê na imagem abaixo a graduação de responsabilidade, do provedor até o cliente, varia de acordo com o serviço.


![[Pasted image 20260325131820.png]]

![[Pasted image 20260325132823.png]]

# Quais são as 5 atividades do gerenciamento de riscos?

- **Identificar:** detectar os CVES (Common Vulnerabilities and Exposures, um sistema padronizado para identificar e catalogar vulnerabilidades de segurança conhecidas em softwares e hardwares).
- **Avaliar o risco:** estabelecer critérios de correção.
- **Remediar/mitigar:** corrigir o problema o possível para fechar as portas para futuras ameaças.
- **Relatar:** documentar as falhas encontradas e as soluções utilizadas para esse problema.
- **verificar:** fazer uma nova varredura para garantir que as medidas que foram tomadas realmente funcionaram.

# Quais são os tipos de erros em serviços de nuvem?

- **Erros de configuração (como de controle de acesso).**
- **Sistemas desatualizados.**
- **Falhas nas APIs que dão acesso as nuvems.**

# Quais são algumas das regras para àqueles que manipulam dados pessoais?

- **Minimização dos dados:** coletar somente os dados do cliente que realmente serão utilizados.
- **Limitação de armazenamento:** não reter os dados por mais tempo do que o necessário.
- **Direito de acesso:** o ente que abriga os dados deve **solicitar** essas informações aos clientes.

# O que são banco de dados gerenciado (DBaaS)?

Serviços baseados na nuvem em que o provedor (como AWS, Google Cloud ou Oracle) cuida da infraestrutura, manutenção, segurança, backups e escalonamento do banco de dados.

# Quais são os 4 tipos de armazenadores?

- **Arquivos**: organiza os dados como uma hierarquia de pastas.
- **Bloco:** separa os dados em volumes com o mesmo tamanho.
- **Objetos:** gerenciam dados como unidades discretas, combinando os dados reais (arquivos, imagens) com metadados ricos e um identificador único.
- **Containers**

# O que são funções sem serviço (abordagem serverless)?

Indica que o cliente do serviço de nuvem não é responsável pela infraestrutura de computação subjacente, isto é, manutenção do sistema operacional, escala, gerenciamento de tempo de execução, e assim por diante.

# O que é rede como serviço (NaaS)?

 Funciona oferecendo aos organizações serviços de rede para que não precisem investir na compra, instalação e manutenção de hardware de rede. Em seguida, o cliente paga uma assinatura mensal para acessar os recursos de rede do provedor.

A classe de serviço em nuvem associado a rede são:

- **Domain Name System (DNS);**
- **Virtual Private Network (VPN);**
- **Proteção Distributed Denial of Service (DDoS protection).**
# O que é o Serviço de Monitoramento e Auditoria?

O monitoramento refere-se às atividades de registro feitas nos serviços do ambiente de nuvem. Eventos de login do usuário (sucesso e falha) e ações tomadas (quem fez o quê e quando, e qual foi o resultado final com sucesso ou falha) são os exemplos principais.

# O que é Cloud Security Alliance (CSA)?

organização dedicada a fomentar conscientização sobre as melhores práticas de segurança em ambientes de computação em nuvem.

A CSA selecionou 14 domínios, sendo o domínio nada mais do que uma área crítica da computação em nuvem que tem relação com a segurança.

O **domínio 1** descreve e dine computação em nuvem e propõe uma terminologia base e detalha estruturas lógicas e arquiteturais par ambientes em nuvem.

Outros exemplos de domínio são o de **governança**, que é a capacidade de uma organização governar e gerir o risco corporativo introduzido a partir da adoção da computação em nuvem e também o **operacional** .
# Quais são as técnicas-chave para a criação de nuvem?

- **Abstração** é o que torna os recursos físicos invisíveis e consumíveis como software.
- **Orquestração** é o que coordena e automatiza esses recursos para funcionarem juntos.

# Quais conceitos compõem a multilocação?

- **Segregação:** que "permite que o provedor de nuvem divida os recursos para os diferentes grupos".
- **Isolamento:** que "garante que um grupo não possa ver ou modificar os ativos uns dos outros".

# Qual a diferença entre Capex e Opex?

**Capex** (Capital Expenditure) refere-se a investimentos em bens duráveis e ativos fixos (máquinas, imóveis) que geram benefícios de longo prazo. **Opex** (Operational Expenditure) são despesas operacionais recorrentes e de curto prazo para manter a empresa funcionando no dia a dia (aluguel, salários, manutenção).

# O que são as zonas de disponibilidade da Azure?

São datacenters fisicamente separados e independentes dentro de uma região do Azure, projetados para proteger aplicações e dados contra falhas de infraestrutura. 

# O que é a conta de armazenamento do Azure?

é responsável por agrupar quatro tipos de dados  — container, arquivos, filas e tabelas — em um único lugar. Mais informações sobre cada um deles:

- **Container:** armazenam qualquer tipo de dado, geralmente não estruturado (imagens, vídeos).
- **Compartilhamento de arquivos:** armazenamento de arquivos estruturados.
- **Filas:** armazenamento de mensagens (ou mensageria).
- **Tabelas:** armazenar tabelas em formato nome-valor.

# O que é o Azure Active Directory?

O Azure Active Directory (Azure AD), agora oficialmente chamado de Microsoft Entra ID, é o serviço de gerenciamento de identidades e acessos baseado na nuvem da Microsoft. A identidade é representação digital de um objeto que precisa acessar um recurso. Imagine a identidade como um crachá digital inteligente que carrega informações sobre "quem" ou "o quê" está tentando entrar no sistema.
# Quais são os serviços de armazenamento no Azure?

- **Blobs do Azure:** espaço de armazenamento para dados considerados não estruturados, como arquivos de texto, vídeos, imagens e dados binários, dados que crescem de uma forma escalonável.
- **Arquivos do Azure:** compartilhamento de arquivos bem familiar (que conhecemos nos sistemas Windows), que pode ser utilizado em implementações locais e em nuvem.
- **Filas do Azure:** tipo de armazenamento de mensagens para um sistema de mensagens entre componentes do aplicativo
- **Azure Disks:** tipo de armazenamento usado para os discos de máquina virtual.

# Quais são algumas das características do Azure Active Directory?

- **Autenticação:** verificar a identidade para acessar aplicativos e recursos. Também inclui fornecer funcionalidades, como redefinição de senha por autoatendimento, autenticação multifatorial, etc.
- **Logon único:** Permite lembrar apenas de um nome de usuário e uma senha para acessar vários aplicativos.
- **Gerenciamento de aplicativo:** Permite gerenciar seus aplicativos de nuvem e locais usando o Azure AD.
- **Gerenciamento de dispositivo:** Permite suporte ao registro de dispositivos.

# O que é o orçamento do Azure?

Auxilia no gerenciamaneto de custos no Azure. Por exemplo, é possível configurar o Azure para que ele envie um e-mail informando que os custos atingiram 80% do custo permitido.

# O que são as cotas no Azure?

Limite a quantidade de recursos por assinatura (contêineres lógicos que agrupam recursos de nuvem (como VMs, bancos de dados)).

# O que são bloqueios no Azure?

Impossibilita certas ações em relação aos recursos ou grupo de recursos.

# O que é o azure monitor?

Ele serve para maximizar a disponibilidade e o desempenho de seus aplicativos e serviços. Ele ajuda você a entender como seus aplicativos estão se comportando e permite que você responda a eventos do sistema manual e programaticamente.

# O que é o Azure Policy?

Ela permite que você defina políticas individuais e grupos de políticas relacionadas, conhecidas como iniciativas. Também avalia seus recursos e realça aqueles que não estão em conformidade com as políticas criadas por você e pode impedir a criação de recursos sem conformidade.
# O que é o azure advisor (ou assistente azure)?

Ele oferece recomendações práticas para ajudar você a otimizar seus recursos do Azure em termos de confiabilidade, segurança, excelência operacional, desempenho e custo

# O que é a calculadora de preços do Azure?

Ajuda a estimar os custos dos recursos disponíveis na plataforma.

# O que é o status do Azure?

É uma exibição global da integridade de todos os serviços do Azure em todas as regiões. Ela é uma referência rápida para incidentes com impacto amplo.
# O que é a integridade do serviço da Azure?

Fornece as regiões e serviços do Azure de forma mais detalhada, focando nos serviços e regiões que estão sendo utilizados no momento, ajudando na tomada de decisão.
# O que é o Resource health?

É um serviço gratuito que monitora a saúde individual de cada recurso do Azure (VMs, bancos de dados, web apps), fornecendo relatórios em tempo real e históricos sobre disponibilidade.

# O que são as marcas (tags)?

Elas permitem associar metadados a um recurso para ajudar a controlar o gerenciamento de recursos, os custos e a otimização, a segurança etc.

# O que é o portal 'Migrações para Azure'?

É um portal onde é possível **alocar todos os projetos de migração para a nuvem**. É possível definir se o projeto será um conjunto de servidor, banco de dados e aplicativos, banco de dados somente, aplicativos web somente, entre outras opções.

**O Azure Active Directory é um recurso que não pode ser migrado**, pois está vinculado a conta do Azure e não está dentro de um grupo de recursos.

# Como é organizado a infraestrutura da AWS?

A infraestrutura global da AWS é dividida em regiões, que representam localizações geográficas onde ficam hospedados seus datacenters. Dentro de cada região existem subdivisões conhecidas como **zonas de disponibilidade (AZs), que consistem em um ou mais datacenters**.. A escolha de qual região será utilizada é do usuário que provisiona os recursos de TI, que deve avaliar critérios como **latência, preço, disponibilidade e possíveis regulações de conformidade nesse ambiente**. 

Para garantir a resiliência de ambientes na nuvem AWS, **é sempre recomendado o uso de pelo menos duas AZ**. Dessa forma, havendo falha em uma AZ, o ambiente continuará em pleno funcionamento em outra AZ da região.

# O que é o Amazon Elastic Compute Cloud?

É um serviço que provê capacidade computacional segura e redimensionável na nuvem, em formato de máquinas virtuais.

**No Amazon EC2, a responsabilidade da instalação do sistema operacional não é do usuário, pois a AWS fornece imagens prontas, conhecidas como Amazon Machine Images (AMI).**

# O que é Amazon Machine Image (AMI)?

É um modelo (template) pré-configurado que contém o sistema operacional, softwares e configurações necessários para lançar uma instância virtual (servidor) no Amazon EC2.
# O que é AMI ID?

AMIs possuem um identificador único (AMI ID), com prefixo “ami-” seguido de um hash com números e letras, que representa todo o conjunto de características, como o sistema, a versão, a arquitetura e a região.
# Quais são os 3 tipos de computação da AWS?

- **Máquinas Virtuais (VMs)**: **virtualização de um servidor físico**, que possui disco, placa de rede, e permite instalar e personalizar o ambiente de forma similar. **Na AWS, as máquinas virtuais são chamadas de Amazon Elastic Compute Cloud (EC2).**
- **Containers:** um padrão de empacotamento de código e dependências projetado para ser executado de forma confiável em qualquer plataforma. Na AWS é possível executar containers no **Amazon Elastic Container Service (Amazon ECS)** ou no **Amazon Elastic Kubernetes Service (Amazon EKS)**. Os containers oferecem **maior velocidade** de provisionamento e consistência de funcionamento independente do ambiente.
- **Computação sem servidor (Serverless Computing):** o foco passa a ser no código das suas aplicações, sem precisar gastar tempo mantendo e atualizando infraestrutura, servidores ou sistema operacional. Nesse modelo, você pagará apenas pelo tempo que sua aplicação executar. Na AWS, o principal serviço de computação sem servidor é o AWS Lambda.

# Quando é mais recomendado o EC2?

para aplicações que necessitam de armazenamento local e que possuem forte dependência do sistema operacional e têm características de monolito.

# Quando é mais recomendado ECS/EKS?

Para equipes que dominam docker ou kubernetes, que já utilizam uma arquitetura de microsserviços e armazenamento de rede ou de objetos.

# Quando é mais recomendado o Lambda?

Quando o time técnico tem um perfil desenvolvedor e não quer gerir detalhes de infraestrutura ou de rede e as aplicações processam tarefas rapidamente.

# O que é uma instância

É um servidor virtual na nuvem, utilizado para executar aplicações, sites e processar dados de forma escalável e segura. Elas fazem parte do serviço Amazon EC2 (Elastic Compute Cloud), permitindo escolher capacidades específicas de CPU, memória, armazenamento e rede.

# Tipos de instância EC2:

- **De uso geral:** provê um **equilíbrio entre memória, processamento e rede**, e pode ser utilizado para uma ampla gama de workloads (conjunto de códigos, aplicativos, bancos de dados e recursos computacionais (memória, rede) necessários para executar uma tarefa ou serviço). Ex.: t4g, t3, t3a, m6i, m6g, m6a, m5, m5a, m5n, m4.
- **Otimizado para computação:** ideal para workloads de **uso intensivo de CPU**, beneficiando-se de processadores de alta performance. Ex.: c6g, c6i, c6a.
- **Otimizado para memória:** ideal para workloads que precisam processar grandes conjuntos de dados em memória. Ex.: r6a, r6g, r6i.

# O que é o par de chave (key pair) da EC2?

**É usado para autenticação segura ao acessar uma instância EC2**. Esse par de chaves é composto por uma chave pública e uma chave privada. A chave pública é associada à instância EC2 e a chave privada é mantida pelo usuário.

**Para instâncias do Windows, a chave privada é necessária para descriptografar a senha do administrador e em instâncias Linux, para conectar remotamente, usando o SSH.**

# O que é o Security Group (SG)?

É um firewall virtual para suas máquinas EC2, controlando o tráfego de entrada e saída. 

| Serviço                  | EC2                                                                             | ECS                                                                                                                           | Lambda                                                          |
| ------------------------ | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Tipo de Computação       | Instância;   <br>Infraestrutura como serviço (IaaS)                             | Container;   <br>Container como serviço (CaaS)                                                                                | Função;   <br>Função como serviço (FaaS)                        |
| Caso de uso              | De uso geral; controle completo sobre o servidor                                | Executar containers docker; Tarefas/execuções de +15 minutos                                                                  | Pequenas aplicações que executam tarefas em menos de 15 minutos |
| Escalabilidade           | Uso de políticas de auto scaling groups para aumento e diminuição de instâncias | Escalabilidade nativa baseado em métricas do cluster                                                                          | Escalabilidade automática                                       |
| Tempo limite de execução | Sem limite                                                                      | Sem limite                                                                                                                    | 300 segundos (15 minutos)                                       |
| Preço                    | Varia pelo tipo, tempo de execução e opção de compra.                           | ECS no EC2: mesmos custos do EC2;   <br>ECS no Fargate: quantidade vCPU e memória usada, tempo de execução e opção de compra. | Números de requisições e tempo de execução.                     |

# O que é um Amazon Elastic Block Storage (EBS)?

O Amazon Elastic Block Storage é um serviço que fornece volumes de armazenamento em blocos, e que pode ser usado com instâncias EC2. Se você desligar ou apagar uma instância do Amazon EC2, todos os dados no volume do EBS anexo permanecerão disponíveis, permitindo reanexar a uma instância.

# O que é snapshot do EBS?

É um backup incremental. Isso significa que o primeiro backup de um volume copia todos os dados. Nos backups subsequentes, somente os blocos de dados que foram alterados desde o snapshot mais recente serão salvos.

# Em quais cenários se usa o EBS?

- **Sistemas operacionais**
- **Banco de dados**
- **Aplicativos corporativos**

# O que é Amazon Simple Storage Service (Amazon S3)?

Ao contrário do Amazon Elastic Block Store (Amazon EBS), o Amazon Simple Storage Service (Amazon S3) é uma solução de armazenamento independente, que não está vinculada à computação e permite que você recupere seus dados de qualquer lugar na web.

# O gp3 é o tipo de EBS mais recomendado para qual dos seguintes casos de uso?

Volumes de boot, aplicativos de baixa latência, desenvolvimento e testes.
# O que são os buckets do Amazon S3?

Nesse serviço, você **armazena seus objetos em contêineres chamados de buckets (baldes)**. Não é possível fazer upload de nenhum objeto, nem mesmo uma única foto, para o Amazon S3 **sem criar um bucket primeiro.**

Ao criar um bucket você especifica, no mínimo, **dois detalhes: o nome desse bucket e a região da AWS na qual deseja que ele resida.**

Aqui está o conteúdo resumido em formato de perguntas e respostas:

# O que acontece se eu não especificar a classe de armazenamento no S3?

Se você não especificar, o objeto é armazenado automaticamente na classe padrão do Amazon S3, chamada **S3 Standard**.

# Para que servem as classes de armazenamento do S3?

Elas permitem ajustar o tipo de armazenamento conforme o padrão de acesso aos dados, ajudando a equilibrar **custo e desempenho**.

# O que é a classe S3 Standard?

É a classe padrão, ideal para dados acessados com frequência. Oferece:

- Alta disponibilidade
    
- Baixa latência
    
- Alto desempenho  
    Indicada para aplicações web, apps móveis, jogos e análise de dados.

# O que é a classe S3 Standard-IA?

É voltada para dados acessados com menos frequência, mas que ainda precisam de acesso rápido.  
Vantagens:

- Custo menor de armazenamento
    
- Alta performance  
    Indicada para backups e recuperação de desastres.

# O que é a classe Glacier Instant Retrieval?

É uma classe de baixo custo para dados raramente acessados, mas que precisam ser recuperados rapidamente (em milissegundos).  
Indicada para:

- Arquivos médicos
    
- Mídias
    
- Conteúdo gerado por usuários

# O que são Glacier Flexible Retrieval e Glacier Deep Archive?

São classes voltadas para arquivamento de longo prazo, com custo ainda menor, porém com tempos de recuperação mais lentos (não detalhados no texto).

# Para que o Amazon S3 é mais utilizado?

**1. Backup e armazenamento**  
Alta durabilidade, ideal para guardar cópias de segurança.

**2. Hospedagem de mídia**  
Permite armazenar arquivos grandes (até 5 TB por objeto), como vídeos, fotos e músicas.

**3. Data lakes**  
Escalabilidade praticamente ilimitada, ideal para grandes volumes de dados.

**4. Sites estáticos**  
Pode hospedar sites simples com HTML, CSS e JavaScript.

# O que é o O Amazon Elastic File System (Amazon EFS)?

É um sistema de arquivos escalável, usado com os serviços de nuvem AWS e recursos locais. À medida que você adiciona e remove arquivos, o Amazon EFS expande e retrai automaticamente, de forma que pode dimensionar sob demanda para petabytes sem interromper os aplicativos.

# Por que é necessário controlar o acesso entre recursos na AWS?

Porque existem milhões de clientes e recursos (como instâncias do Amazon EC2). Sem controle, todos poderiam se comunicar livremente, o que comprometeria a segurança.

# O que é o Amazon VPC?

O Amazon Virtual Private Cloud (VPC) é um serviço que permite criar uma rede virtual isolada dentro da AWS para seus recursos.

# Qual é a principal função de uma VPC?

Permitir que você execute recursos (como servidores) em uma rede definida por você, com controle total sobre:

- Acesso
- Comunicação
- Estrutura da rede

# O que são sub-redes (subnets)?

Sub-redes são divisões dentro de uma VPC onde você pode organizar seus recursos, como instâncias do Amazon EC2.

# Quais fatores precisam ser definidos ao criar uma VPC?

1. Nome da VPC
Identificação da sua rede.

2. Região
A VPC é criada em uma região específica da AWS e pode abranger várias zonas de disponibilidade.

3. Intervalo de IP (CIDR)
Define o tamanho da rede e a quantidade de IPs disponíveis.
Cada VPC pode ter até quatro blocos CIDR /16.

# O que a AWS faz após a criação da VPC?

A AWS provisiona automaticamente:

- A rede virtual
- Os endereços IP dentro do intervalo definido

# Uma VPC pode abranger várias zonas de disponibilidade?

Sim. Embora esteja dentro de uma única região, a VPC pode se estender por múltiplas zonas de disponibilidade, aumentando a disponibilidade e resiliência. **Para ter alta disponibilidade em uma VPC, é recomendável usar ao menos duas AZs.**

# O que são sub-redes em uma VPC?

Sub-redes são divisões menores dentro de uma VPC, semelhantes a VLANs em redes tradicionais. Elas ajudam a organizar e controlar o tráfego de rede dentro do Amazon Virtual Private Cloud.

# Qual é o objetivo das sub-redes na AWS?

Elas são usadas para:

- Melhorar a organização da rede
- Garantir alta disponibilidade
- Controlar a conectividade dos recursos

# O que é necessário definir ao criar uma sub-rede?

1. A VPC
Em qual VPC a sub-rede será criada.

2. Zona de disponibilidade
A sub-rede pertence a uma única zona específica.

3. Bloco CIDR
Um intervalo de IP que deve estar dentro do CIDR da VPC.

# Onde uma instância do EC2 é criada?

Uma instância do Amazon EC2 é sempre iniciada dentro de uma sub-rede, e portanto em uma zona de disponibilidade específica.

# Quais são os tipos de sub-redes?

Sub-redes públicas

- Possuem acesso direto à internet
- Utilizam um gateway de internet

Sub-redes privadas

- Não possuem acesso direto à internet
- Acessam a internet indiretamente via NAT (gateway NAT ou instância NAT)

# Qual é a principal diferença entre sub-redes públicas e privadas?

- Públicas: acesso direto à internet
- Privadas: acesso indireto ou restrito, aumentando a segurança


# O que são IPs reservados em uma sub-rede da AWS?

São endereços IP que a AWS reserva automaticamente em cada sub-rede para funções internas, como:

- Roteamento
- DNS
- Gerenciamento de rede

# Quantos IPs a AWS reserva por sub-rede?

A AWS reserva 5 endereços IP em cada sub-rede dentro de uma Amazon Virtual Private Cloud.

# Esses IPs podem ser usados por instâncias?

Não. Eles são exclusivos para uso interno da AWS e não podem ser atribuídos a recursos como instâncias do Amazon EC2.

# Como funciona o cálculo de IPs em uma VPC?

Exemplo:

VPC: 10.0.0.0/22 → total de 1024 IPs
Dividida em 4 sub-redes /24 → cada uma com 256 IPs

# Quantos IPs realmente podem ser usados em cada sub-rede?

De 256 IPs por sub-rede:

5 são reservados pela AWS
251 ficam disponíveis para uso

# Pode dar um exemplo de sub-rede?

Sim. Uma sub-rede poderia ser:

10.0.0.0/24
# Qual é a importância de entender os IPs reservados?

Ajuda no planejamento da rede, evitando surpresas ao perceber que nem todos os IPs estão disponíveis para uso.

# Quais são os 5 endereços IP reservados pela AWS?

|Endereço IP|Propósito|
|---|---|
|10.0.0.0|Endereço de rede|
|10.0.0.1|Roteador da VPC|
|10.0.0.2|Servidor DNS|
|10.0.0.3|De uso futuro|
|10.0.0.255|Endereço de broadcast

# O que é um Gateway NAT?

É um serviço de Network Address Translation (NAT) que permite que instâncias em sub-redes privadas se conectem a redes externas, sem permitir conexões de entrada iniciadas de fora.

# Qual é a principal função de um Gateway NAT?

Permitir que recursos em sub-redes privadas:

- Acessem a internet ou outras redes
- Permaneçam protegidos contra acessos externos diretos
# Instâncias em sub-redes privadas podem receber conexões externas usando NAT?

Não. O Gateway NAT permite apenas conexões de saída, bloqueando conexões de entrada não solicitadas.

# Quais são os tipos de Gateway NAT?

## Público

É o tipo padrão. Características:

- Criado em uma sub-rede pública
- Permite que instâncias privadas acessem a internet
- Requer um IP elástico (EIP)
- O tráfego é roteado para um gateway de internet

Também pode ser usado para conectar com:

- Outras VPCs
- Redes locais (on-premise)
## Privado

Características:

- Usado para comunicação entre redes privadas
- Não permite acesso direto à internet
- Não utiliza IP elástico
- Indicado para conexões com:
- Outras VPCs
- Redes locais (via VPN ou conexão dedicada)

# Um Gateway NAT privado pode acessar a internet?

Não. Mesmo que exista um gateway de internet na Amazon Virtual Private Cloud, o tráfego vindo de um NAT privado será descartado.

# Onde o Gateway NAT é utilizado na prática?

Principalmente em arquiteturas onde:

- O backend fica em sub-redes privadas
- Precisa acessar APIs externas, atualizações ou serviços na internet
- Mas deve continuar protegido contra acessos diretos


# O que acontece quando você cria uma VPC na AWS?

Ao criar uma Amazon Virtual Private Cloud, a AWS automaticamente cria uma tabela de rotas principal.

# O que é uma tabela de rotas?

É um conjunto de regras que define para onde o tráfego de rede deve ser enviado dentro da VPC.

# O que são rotas?

Rotas são regras dentro da tabela de rotas que determinam o caminho que o tráfego deve seguir.

# Qual é o comportamento padrão da tabela de rotas principal?

Por padrão, ela permite que todas as sub-redes dentro da VPC se comuniquem entre si.

# Quais são os principais elementos de uma tabela de rotas?

## Destino (Destination)

É o intervalo de IP para onde o tráfego será enviado
Exemplo: o bloco CIDR da própria VPC

## Alvo (Target)

É o caminho pelo qual o tráfego será roteado
Exemplo: a própria rede local da VPC
# Como entender “destino” e “alvo” de forma simples?

- Destino: para onde o tráfego quer ir
- Alvo: por onde ele vai chegar lá
# Qual a importância da tabela de rotas?

Ela controla o fluxo de comunicação dentro da rede e também pode ser usada para:

- Permitir acesso à internet
- Conectar com outras VPCs
- Integrar com redes locais

 Quais os tipos de site/página web o Amazon S3 possui capacidade para fazer hospedagem e executar como um servidor web?

# O que é a área de Compute Engine do Google Cloud?

É a página onde são criadas e armazenadas as máquinas virtuais. 

# O que é a área de suporte?

É através dessa área que é possível consultar documentação, conferir guias de arquitetura, ver perguntas frequentes e iniciar um tutorial.

# O que são as regiões e as zonas do Google Cloud?

As **regiões são os locais onde ficam os datacenters** responsáveis por prover serviço computacional. Serve como uma estratégia de recuperação de desastres (**disaster recovery**), em caso de uma indisponibilidade de uma região inteira.

Dentro de cada região, existe uma divisão chamada de **“zonas”, o que representa uma divisão de servidores, denominados “a”, “b” e “c”.** Projetadas para tolerância a falhas: se uma zona falha, as outras na mesma região não são afetadas.

A comunicação entre as regiões ocorre através de um **rede privada com cabos submarinos**.

# O que é a VPC do Google Cloud?

É uma rede privada hospedada em Google Cloud em que **os usuários podem disponibilizar suas aplicações, armazenar dados e hospedar sites.** Por meio dela é possível **configurar políticas de firewall, IPs (internet protocol), portas e protocolos.**

A VPC do Google Cloud é global, logo, podemos ser atendidos em qualquer região disponível.

# O que são as subnets?

Uma subnet é uma divisão da VPC que define um intervalo de IPs (ex: 10.0.0.0/24) disponíveis para os recursos internos (VMs, serviços etc.).

# O que é série ou geração?

Cada série é formado por um conjunto de máquinas virtuais predefinidas, que possuem um conjunto de recursos para a VM. Se nenhum deles atender sua necessidade, é possível criar uma máquina personalizada.
# Quais são os tipos de máquinas virtuais?

| Tipo de uso | Econômico                                                                                                                    | Equilibrado                                                                              | Escalonamento horizontal otimizado                                      | Otimização de memória                                                                  |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Família     | E2                                                                                                                           | N2, N2D, N1                                                                              | Tau T2D, Tau T2A                                                        | M3, M2, M1                                                                             |
| Objetivo    | Computação básica a um custo menor                                                                                           | Desempenho e preços equilibrados                                                         | Melhor desempenho para cargas que precisam de escalabilidade horizontal | Cargas de trabalho com memória ultraelevada                                            |
| Exemplos    | - Aplicação web<br>- Front-end<br>- Banco de dados pequenos<br>- Ambientes para desenvolvimento<br>- API<br>- Microsserviços | - Streaming de mídia<br>- Banco de dados médios e grandes<br>- Aplicações web<br>- Cache | - Aplicativos Java em grande escala<br>- Microsserviços em containers   | - Banco de dados de análises em memória<br>- Bancos de dados como Microsoft SQL Server |

# Quais são uma das vantagens da máquinas virtuais?

- Facilidade de gerenciamento: é possível facilmente deletá-la e recriá-la de maneira muito simples.
- flexibilidade em customizações: podemos instalar a versão que melhor nos atender de um software e customizar as bibliotecas.

# Como é feito o gerenciamento de responsabilidades de uma VM?

**Mista**. Toda a infraestrutura física é provida e gerenciada pelo Google, mas o gerenciamento de utilização dos recursos, instalação e atualizações de softwares é de responsabilidade única do usuário.

# O que é aplicativo nativo da nuvem (cloud native application)?

Software que utiliza recursos como serviço e que é desacoplado, ou seja, seus componentes não dependem de outros componentes externos, é independente.

## Quais são as duas arquiteturas comuns para o aplciativo nativo da nuvem?

- **Stateful:** consiste em uma aplicação que, além da lógica, armazena os dados em si.
- **Stateless:** dados armazenados em um componente externo, ficando apenas responsável pela lógica e processamento.

# O que é Cloud Run?

Um PaaS que entrega uma infraestrutura sem servidor para as aplicações e suporta as principais linguagens de programação.

# O que é a ISO 27001?

Norma da Organização Internacional de Normatização que descreve os requisitos de um sistema de gestão de segurança e especifica um conjunto de práticas recomendadas.

# Exemplo de segurança aplicada ao Google?

Apenas funcionários autorizados possuem acesso aos datacenters, e esses funcionários representam menos de 1% do total de funcionários do Google.

# O que é o Google App Engine?

É um serviço de PaaS (Plataforma como Serviço) totalmente gerenciado. Ele permite desenvolver e hospedar aplicações web e APIs sem gerenciar a infraestrutura subjacente.

# O que é IAM (identity and access management)?

Processo para controle do acesso às informações, recursos e ações do ambiente, sendo possível gerir todos os usuários e seu nível de acesso.

Exemplo: se um usuário tem acesso de desenvolvedor, estará autorizado a somente visualizar ou talvez editar configurações relacionadas à sua alçada, não podendo visualizar, utilizar ou configurar nada de infraestrutura

# O que é o Cloud Armor?

Tecnologia que utiliza inteligência artificial e aprendizado de máquinas para mitigar ataques contra aplicações e servidores dos clientes.

# O que é o reCAPT?

Tecnologia do Google que permite distinguir entre um acesso humano ou automatizado por meio do uso de identificações visuais ou auditivas.

# O que é a lista de bloqueios (blocklist) e lista de permitidos (allowlist)?

Estratégia de segurança da informação cujo o objetivo é ter uma lista de bloqueios ou permissões de acessos ao sistema, e isso pode ser baseado em IPs ou regiões. É muito útil para podermos negar o acesso de IPs externos da nossa rede, por exemplo, a uma aplicação.

# O que é DevOps?

DevOps é uma cultura e um conjunto de práticas que une as equipes de **Desenvolvimento** (Dev) e **Operações** (Ops) de tecnologia, com a finalidade de criar, testar e colocar o software no ar mais rápido e com menos erros.

# O que são os LOGS?

Uma forma de monitoramento que registra eventos relevantes no sistema ou infraestrutura. Com o uso dos LOGS, é possível identificar erros, acessos e alterações realizadas.

# Qual é a ferramenta de monitoramento do Google Cloud?

**Cloud Monitoring** para monitoramento de aplicações e infraestrutura de maneira mais minuciosa.

# Quais são as etapas de construção de uma infraestrutura para um projeto que utilizará VMs?

Criar uma VPC, selecionar uma região, criar as subnets, vincular a VM a essa subnet.

# O que é cloud native architecture?

É uma arquitetura cujo objetivo é se adequar às tecnologias como serviço oferecidas pelo provedor de nuvem.

# O que é o Cloud SQL?

Um banco de dados SQL reacional, completamente gerenciado e com alta disponibilidade, escalável e em nuvem.

# O que é mensageria assíncrona?

É um sistema responsável por gerenciar a troca de mensagens entre serviços, no entanto, não é necessário que ambos serviços estejam simultaneamente disponíveis para que isso aconteça. Em suma, a troca de informações não exige resposta imediata.

A ferramenta oferecida pelo Google Cloud para comunicação assíncrona é o Pub/Sub.