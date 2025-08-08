
## 20. Introdução à Pull Request e Code Review (PR)

### O que é Pull Request?

Uma solicitação para que as alterações realizadas em uma branch específica sejam traziadas (pull) para a branch `main`.

Em alguns casos, esta solicitação será enviada para um **Code Review**, onde alguém ficará responsável por analisar o código enviado e verificar se pode ou não ser aceito.

## 21. Utilizando Pull Request na prática (PR)

- Clique no botão de `Pull requests`.

![[Pasted image 20250730161847.png]]

- Clique no botão `New pull request`.

![[Pasted image 20250730162033.png]]

- Defina qual branch (neste caso a `main`) fará o `pull` de qual da branch (neste caso a branch `chat`) e clique em `Create pull request`.

![[Pasted image 20250730162622.png]]

- Adicione um título, uma descrição e também o tipo de `pull request` que está sendo feita (uma correção de bug, documentação, um aprimoramento, etc.) em `Labels`. Clique em `Create pull request`.

![[Pasted image 20250730164237.png]]

- Para aqueles que são code reviewers, é possível ver os commits da branch em que será feito o `pull` (neste caso a branch `chat`) ao clicar em `Commits`.

![[Pasted image 20250730171901.png]]

- Caso deseje relatar algum erro, clique em um dos commits e depois no sinal de + na linha do código que deve ser corrigida.

![[Pasted image 20250730172231.png]]

![[Pasted image 20250730172326.png]]

- Informe algum comentário e clique em `Start a review`. Esse comentário irá retornar para a pessoa que realizou os commits.
- Depois que todas as correções forem resolvidas, é só clicar em `Merge pull request` na aba `Conversation`.

![[Pasted image 20250730172640.png]]

- Clique em `Confirm merge`.

![[Pasted image 20250730172849.png]]

Por fim, irá aparecer a mensagem `Pull request successfully merged and closed`:

![[Pasted image 20250730173117.png]]

## 22. Fluxo de trabalho - Protegendo uma Branch

**OBS.: A proteção da branch de maneira gratuita é possível apenas em repositórios públicos.**

- Vá até a página do seu repositório e clique em `Settings`:

![[Pasted image 20250731151610.png]]

- Clique em `Branches`:

![[Pasted image 20250731151850.png]]

- Clique em `Add classic branch protection rule`:

![[Pasted image 20250731151931.png]]

- Informe o nome da branch que deverá se protegida em `Branch name pattern` -> selecione a opção `Require a pull request before merging`, que define um número específico de aprovações para que haja um merge. É também possível marcar a opção `Require review from Code Owners`, onde também será necessário uma revisão aprovada do código.

![[Pasted image 20250731152205.png]]

- Por fim, clique em `Create` no final da página.

![[Pasted image 20250731152224.png]]

- Caso tenha criado em uma conta privada, será exigido de você o `Upgrade` (nada mais que um pagamento) para habilitar estas regras na branch escolhida.

![[Pasted image 20250731153553.png]]

### Como adicionar novos colaboradores

- Vá até a página do seu repositório e clique em `Settings`:

![[Pasted image 20250731151610.png]]

- Clique em `Collaborators`:

![[Pasted image 20250731154421.png]]

- Clique em `Add People`:

![[Pasted image 20250731154532.png]]

- Busque e selecione pelo nome de algum perfil e confirme no botão `Add ...`:

![[Pasted image 20250731154747.png]]

## 24. Fluxo de trabalho - Code Review (Revisão de código)

### Escolhendo Code Reviewer

No momento em que for criar um `pull request`, é possível escolher quem será o code reviewer daquele(s) commit(s) ao clicar no link `Reviewers` e selecionar alguma das opções disponíveis (como aparece em destaque na foto).

![[Pasted image 20250804115059.png]]

### Análise do `pull request` **por parte do code reviewer**

- Acesse o repositório do projeto e clique em `Pull requests`

![[Pasted image 20250804120703.png]]

- Clique na `pull request` -> clique em `Commits` -> clique em um dos commits.

![[Pasted image 20250804120815.png]]

![[Pasted image 20250804120850.png]]

![[Pasted image 20250804120934.png]]

- Clique no sinal de + que aparece ao lado da linha que deseja fazer um comentário -> ao fazer o comentário, clique em `Add single comment`.

![[Pasted image 20250804121319.png]]

### Opções de review

- Clique em `Review changes`, faça se  e escolha uma das 3 opções:
	- `Comment`: será enviado apenas o comentário.
	- `Approve`: o `pull request` será aprovado e, portanto, feito um merge.
	- `Request changes`: o pull request não será aprovado, mas, em vez disso, será enviado uma solicitação de mudança junto com os comentário feito em `Review changes`.
- Por fim, clique em `Submit review`.

![[Pasted image 20250804121815.png]]

Será enviada então esta mensagem para o colaborador que realizou a `pull request`:

![[Pasted image 20250804122353.png]]

Caso o colaborador tenha realizado as alterações necessárias e enviado um novo commit, este novo commit irá aparecer na mesma `pull request` que a anterior:

![[Pasted image 20250804123339.png]]

### Visualização dos pull requests já encerrados

Clique na opção `Closed` na sessão `Pull requests` do seu repositório:

![[Pasted image 20250804124329.png]]

## 25. Usando Fork

### O que é fork?

É um recurso do GitHub que permite você copiar e trazer um repositório público de outra conta para o seu perfil, permitindo que você faça alterações nesta cópia de forma independente, sem alterar o repositório original.
### Como fazer um fork?

- Vá até um repositório público de outra conta e clique em `Fork`:

![[Pasted image 20250805120051.png]]

- Escolha se você quer copiar apenas a branch principal (neste caso o `master`) ou todas as branches em `Copy the master branch only`. Por fim, clique em `Create fork`.

![[Pasted image 20250805120329.png]]

Depois que você fez um `git clone` deste fork e subiu um novo commit, é possível agora fazer um `pull request`:

![[Pasted image 20250805123556.png]]

## 26. Trabalhando com arquivos - reverter, mover, excluir e log

### Remoção de um arquivo

Ao remover um arquivo do seu repositório local, irá aparecer uma mensagem semelhante ao executar `git status`:

```
Your branch is ahead of 'origin/ajuste' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    novo.txt
```

Em vez de executar `git add .`, execute `git rm ` mais o nome do arquivo deletado. Agora irá aparecer uma mensagem semelhante informando para que você comite essa mudança (a remoção de um arquivo):

```
Your branch is ahead of 'origin/ajuste' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    novo.txt
```

Agora é só fazer o commit e, por fim, o `git push`.
### Trocar um arquivo de diretório

Digite `git mv <nome_arquivo> <nome_pasta>/<nome_arquivo>`. Por exemplo, se você deseja mudar o arquivo configuracao.txt para a pasta usuario então digite `git mv configuracao.txt usuario/configuracao.txt`

**OBS.: é possível também renomear o arquivo com `git mv`. Por exemplo: `git mv configuracao.txt configuracao2.txt`**

Ao executar `git status`, irá aparecer uma mensagem semelhante a esta:

```
Your branch is ahead of 'origin/ajuste' by 2 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    configuracao.txt -> usuario/configuracao.txt
```

Mesmo que o arquivo não tenha sido renomeando, ainda assim irá aparecer `renamed`.

Por fim, não é preciso executar o `git add .`, mas apenas o `git commit -m` e o `git push`.

### Restaurar arquivos

Digite `git checkout <nome_arquivo>` para restaurar o conteúdo daquele arquivo para a última versão em que foi commitado.

### Histórico de commits

Digite `git log` para visualizar o histórico de commits. Caso tenha sido feito muitos commits, irá aparecer `:` no final do Git Bash, indicando que há uma continuação de commits que podem ser vistos. Para visualizá-los, pressione a seta pra baixo e, para sair, digite `q`.

## 27. Configurando informações de usuário no Git

### Configuração do nome e e-mail

As seguintes configurações irão ser registradas no momento em que for realizado um novo commit:

- `git config --global user.name "seu nome"`
- `git config --global user.email "seu e-mail"`

**OBS.: embora não haja nesta aula uma instrução sobre como verificar estas alterações, digite `git config --list` para isso.**

**OBS.2: o e-mail deve ser o mesmo usado na plataforma do GitHub.**

### Comandos de ajuda

- `git help`: lista os principais comandos do Git e oferece uma breve explicação sobre cada um deles.
- `git help <comando específico>`: isso fará com que seja aberto uma nova página no seu navegador com as informações detalhadas do comando escolhido.

## 28. Commits - Utilizando Log e Show

### Histórico de commits

Além do comando `git log`, há outras formas de buscar pelo histórico de commits:

- `git log --oneline`: exibe o histórico de commits, porém de forma resumida (apenas com o código e a mensagem do commit).
- `git log <nome_arquivo>`: exibe apenas os commits relacionados ao arquivo informado.
- `git log --oneline <nome_arquivo>`: exibe apenas os commits relacionados ao arquivo informado, porém de forma resumida.

### Apresentação das alterações

- `git show <codigo_commit>`: apresenta as alterações que foram feitas naquele commit.

### Referência HEAD do Git e o origin

O HEAD aponta para o commit mas recente de uma branch. Por exemplo:

```
37213f6 (HEAD -> ajuste) alterado novo v2
61a4559 adicionado novo v1
3dee844 Alterei o chat removendo o v3
0be0063 Alterado chat v3
180e9af configurado movido
d020ee8 removido arquivo novo
6b2bfa5 adicionado arquivo novo
8609ce7 (origin/ajuste) adicionado chat alterado
```

Este código afirma que o último commit da branch 'ajuste' foi o 'alterado novo v2'. No entanto, o mesmo código afirma que o último commit que foi 'empurrado' para a branch 'ajuste' do repositório remoto 'origin' foi o 'adicionado chat alterado'. Isso é sabido por causa do '(origin/ajuste)'.