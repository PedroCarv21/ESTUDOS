
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

# Quais são as características essenciais da computação em nuvem?

- **Autoatendimento sob demanda:** o usuário tem acesso a plataforma para configurar recursos como servidores e redes de armazenamento, de forma automática e sem depender do provedor de serviço em núvem.
- **Amplo acesso à rede:** os recursos computacionais devem estar acessíveis a internet.
- **Agrupamento de recursos:** os recursos de computação do provedor são agrupados para atender a vários consumidores usando um modelo multilocatário, ou seja, os recursos computacionais são compartilhados entre diversos usuários, os quais não precisam ter conhecimento acerca da localização dos recursos que estão utilizando.
- **Elasticidade dinâmica:** a capacidade dos recursos podem ser aumentadas ou diminuídas de acordo com a demanada.
- **Serviço mensurável:** a capacidade de medir exatamente quais recursos estão sendo usados, monitorar e controlar esses serviços para podermos posteriormente apresentar esses dados ao cliente ou ao usuário final.

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