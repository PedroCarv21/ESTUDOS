
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

## 29. Commits - Verificar diferenças

### Comandos para a comparação de código

- `git diff`: compara as alterações recentes, ainda não colocadas na área stage, com a última versão do arquivo (sendo que a criação deste arquivo já foi commitada).
- `git diff <nome_arquivo>` compara as alterações recentes com a última versão de um arquivo específico.
- `git diff <codigo do commit> <codigo do commit>`: compara as alterações feitas entre dois commits com base no código específico de cada um.

## 30. Commits - Checkout

- `git checkout <codigo do commit>`: retorna para o commit informado, restaurando a versão salva do arquivo durante aquele commit. Isso fará com que o `HEAD` aponte para o código do commit informado, e não mais para `main`. Isso é muito para saber em qual das versões, por exemplo, um sistema começou a apresentar defeitos.

**OBS.: Caso tenha executado este comando enquanto o arquivo em questão estava aberto, feche-o e abra novamente para visualizar a restauração do arquivo.**

- `git checkout <branch>`: dentro do contexto apresentado, este comando retornará para o commit mais recente da branch informada.