
## 6. O que é um Branch (Ramificação)

É uma linha de desenvolvimento específica do projeto, onde são trabalhadas novas versões de determinados recursos. 

Por exemplo: suponha que esteja sendo criado um site de compras que é atualizado conforme o necessário. Cada círculo presente na imagem representa uma versão do projeto. Aquelas versões na área azul chamada **master** (que é a branch principal do projeto) é onde estão sendo desenvolvidas certos recursos do site.

Agora imagine que um grupo de pessoas fique responsável por desenvolver um novo recurso do site (como o carrinho de compras), porém trabalhando neste recurso de forma separada, sem afetar a versão principal do projeto (que está na branch master). Para isso, será necessário criar uma nova branch (como a new_feature, presente na imagem).

Desta forma, o desenvolvimento do projeto fica organizado e sem conflitos.

![[Pasted image 20250624145629.png]]

## 7. Comandos básicos para o terminal

- `cd` (Change Directory): muda o local do diretório atual. Digite no Git Bash o comando `cd` mais o nome do caminho. Exemplo: `cd nova_pasta1`. É possível também arrastar a pasta para onde deseja se mover até o terminal. Isso fará com que todo o caminho daquela pasta seja escrito no terminal. 
- `ls` (list): lista o que está dentro do diretório atual. Se deseja listar arquivos ocultos também, digite `ls -al`.
- `clear` (limpar): apaga o conteúdo trazido pelos comandos anteriores.


## 8. Criando seu primeiro repositório GIT

### git init

Comando utilizado para transformar um diretório em um repositório local gerenciado pelo Git. Ao executar o comando, será criado uma pasta oculta chamada **.git** com alguns arquivos necessários.
### git status

Comando utilizado para expor o status do seu repositório local.

Se esse comando for executado em um repositório local vazio, será mostrado a seguinte mensagem:

```
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Isso significa que você, no momento, se encontra na branch **main**, que não há commits (mudanças salvas) ainda e que não há nada para commitar (salvar) por enquanto.

No entanto, caso seja criado um novo arquivo dentro do repositório local, e executado o comando `git status` logo em seguida, irá aparecer a seguinte mensagem:

```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        codigo.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Agora o Git informa que há um arquivo untracked, ou seja, não rastreado, no seu repositório. Isso significa que foi criado um novo arquivo e que ele não é gerenciado pelo Git, logo, é possível perder completamente o arquivo.

Há também o aviso de que este arquivo ainda não foi adicionado para ser commitado.

## .9 Utilizando comandos Add & Commit

### git add

Para então adicionar este arquivo de modo que ele seja posteriormente commitado, digite `git add` mais o nome do arquivo específico. Em seguida, execute o comando o `git status`; irá aparecer a seguinte mensagem:

```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   codigo.txt
```

Isso significa que o arquivo precisa ser agora commitado.
### git commit -m ""

Este comando salva (commita) os arquivos que haviam sido adicionados anteriormente. Entre as aspas, coloque uma mensagem que informe quais mudanças foram realizadas.