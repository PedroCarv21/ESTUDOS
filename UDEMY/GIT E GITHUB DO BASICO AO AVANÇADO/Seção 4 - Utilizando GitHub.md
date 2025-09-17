
## 11. Configurando chave SSH

### O que é uma chave SSH?

É uma chave criptografada utilizada para fazer autenticação de upload ou download de arquivos em repositórios do GitHub. É representado por um par de chaves:

- **id_rsa (privada)**
- **id_rsa.pub (pública)**

A chave pública é copiada para o servidor e toda vez que alguém tentar subir ou baixar um arquivo em um repositório do GitHub, será analisado a compatibilidade da chave pública com a chave privada.
## 12. Clonando projeto com o GIT

### Criação de um novo repositório remoto

- **Repository name**: será o nome do repositório e não deve ser um nome já utilizado em outro repositório seu.
- **Opção Public**: permite que o repositório fique visível para qualquer um. É recomendado usar essa opção no caso de projetos usados em portfólio.
- **Opção Private**: o acesso deste tipo repositório é restrito aos colabores do projeto.
- **README file**: arquivo utilizado para descrever as principais informações do projeto.
- **.gitignore**: documento que informa quais arquivos naquele projeto devem ser ignorados na hora de subir as atualizações.

![[Pasted image 20250717172341.png]]


### O que significa clonar um projeto do GitHub?

Significa trazer um repositório remoto do GitHub para sua máquina local (praticamente um download). Para isso, é necessário:

- Clicar no botão `Code` e copiar o link SSH.
- ![[Pasted image 20250717175545.png]]
- Abrir o Git Bash e digitar `git clone` mais o link SSH que foi copiado. O clone do projeto será criado no diretório atual do Git Bash. Esse clone será uma pasta com o nome do projeto e, dentro dele, estarão os arquivos e diretórios que compõem aquele projeto.
- **OBS.: se você digitar `git clone <link SSH> .` (com este ponto no final), isso fará com que  sejam 'baixados' os arquivos daquele projeto no diretório atual do Git Bash, sem uma pasta com o nome do projeto.**

## 13. Subindo alterações para o GitHub

### Repositório remoto 'origin'

O nome 'origin' é um nome padrão dado ao repositório remoto quando você clona o projeto. Caso não tenham sido feitas quaisquer alterações, ao executar `git status` será mostrado a seguinte mensagem: `Your branch is up to date with 'origin/main'.`

Isso significa que as atualizações do seu repositório local estão iguais às atualizações do seu repositório remoto (nenhum repositório tem mais ou menos atualizações do que o outro).

Agora, depois  de fazer um novo commit e executar `git status`, será apresentado a seguinte mensagem: `Your branch is ahead of 'origin/main' by 1 commit.`

Isso significa que o repositório local possui um commit a mais do que o seu repositório remoto. Para que o novo commit seja empurrado (push) para o seu repositório remoto, e assim ambos tenham a mesma quantidade de commit, digite `git push`.

Depois de executar esse comando, execute `git status` novamente e veja a mesma mensagem que apareceu antes de fazer o commit: `Your branch is up to date with 'origin/main'.`

### Modificações em arquivos já commitados

Ao modificar um arquivo já commitado anteriormente será mostrado em vermelho a mensagem `modified:` mais o nome do arquivo alterado.

### Comando `git add .`

Em vez de salvar, um por um, os arquivos que foram modificados ou criados, é possível salvar todos de uma vez só através do comando `git add .`.
## 14. Baixando alterações com Git pull

### Como criar um arquivo no repositório remoto?

Clique em `Add file` -> `Create new file`:

![[Pasted image 20250721172451.png]]

Informe agora o nome do arquivo (ex.: chat-joao) -> o conteúdo do arquivo (ex.: recurso de chat) -> clique em `Commit changes...` -> informe o nome do commit em `Commit message` -> escolha a opção `Commit directly to the main branch` -> `Commit changes`.

![[Pasted image 20250721173207.png]]

Em casos assim, onde são feitas alterações no repositório remoto, porém não no local, é necessário executar o comando `git pull` no Git Bash. Esse comando irá trazer os commits presentes somente no seu repositório remoto para o repositório local.

## 15. Sincronizando projeto com o GitHub

Os comandos a seguir serão utilizados quando for criado um repositório local primeiro e, posteriormente, precisar subir ele no GitHub.
### Como renomear a branch principal?

Comando `git branch -M` mais o nome da branch. Este `-M` refere-se ao tipo de branch (a principal).

### Como vincular o repositório local com o repositório remoto (origin) ?

Comando `git remote add origin <url do repositório remoto>`.

### Comando `git push -u origin main`

Em caso de projetos clonados ou projetos que já possuem mais de um commit, é preciso apenas executar o comando `git push`. No entanto, em casos de projetos locais que precisam subir o primeiro commit, é necessário o comando `git push -u origin main` indicando para qual branch esse commit será enviado.