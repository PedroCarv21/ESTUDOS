
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