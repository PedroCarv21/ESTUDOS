
## 35. Salvando alterações com Git Stash

Os comandos seguintes são usados para criar ou manipular 'rascunhos' do seu projeto, que ficam armazenados em uma espécie de esconderijo.

- `git stash`: salva as modificações feitas no seu arquivo como uma espécie de 'rascunho' e retorna seus arquivos a um estado anterior.
- `git stash push -m 'descricao'`: cria uma nova stash com uma descrição.
- `git stash list`: lista as stash.
- `git stash show -p <numero da stash>`: exibe o que foi modificado na stash.
- `git stash apply <numero da stash>`: recupera o que foi salvo em uma stash.
- `git stash clear`: apaga todas as stash.
- `git stash drop <numero da stash>`: remove um stash específica.

## 36. Utilizando git Tag

As tags são como se fossem etiquetas ou rótulos para um commit especifico, destacando desta forma versões importantes do seu projeto. Estes são os comandos para a manipulação de tags:

- `git tag -a <nome da tag> -m "mensagem"`: cria uma nova tag com nome e uma mensagem vinculada a ela.
- `git tag -d <nome>`: remove a tag.
- `git show <nome da tag>`: mostra o conteúdo de um arquivo modificado com base na tag vinculada àquele commit.
- `git checkout <nome da tag>`: faz com que o HEAD aponte para o commit vinculada a tag informada.

Exemplo de como ficam os commits com tags:

```
24cec0c (HEAD -> chat, tag: v2.0) modificado 2 envio de video
9f901a8 modificado 1 envio imagens
33f9197 adicionado chat-envio
201d387 (tag: v1.0) modificado 2 chat
fd2fdd4 modificado 1 chat
48d295a adicionado chat
```

## 37. Enviando Tags para o GitHub

- `git push origin <nome da tag>`: sobe para o GitHub uma tag específica.
- `git push origin --tags`: sobe todas as tags para o GitHub.

É possível ainda visualizar as tags lá no seu repositório do GitHub:

![[Pasted image 20250822152836.png]]

## 38. Atualizando branchs e tags com Fetch

- `git tag`: lista todas as tags.

### Como trazer outras branches para o seu repositório local

Ao clonar um repositório remoto, apenas a branch `main` será levada para o seu repositório local. Para trazer todas as branches atualizadas, utilize o comando `git fetch -a`. Após esse comando, se você executar `git branch` para listar todas as branches daquele repositório, ainda não será possível visualizá-las. É necessário executar `git checkout <nome da branch>` para então se mover para a branch desejada e visualizá-la.

## 40. Utilizando Rebase

Enquanto o `git merge` é responsável por mesclar os commits de duas branches e agrupá-los na ordem cronológica em que foram criados e, no fim, criar um novo commit que represente esse merge, o `git rebase` irá agrupar os commits de modo linear, ou seja, reaplicando os seus commits no topo de outra branch, resultando num histórico de commits mais limpo e linear. 

Para isso, digite `git branch` mais o nome da branch que deseja mesclar.

Exemplo de commits mesclados com `git merge`:

```
4e4068d (HEAD -> main) Merge branch 'recurso'
a0554b7 (recurso) Recurso 2
a2b3305 C3
a49e3a9 Recurso 1
9a12883 Commit 2
e464da1 Commit 1
```

**OBS.: os commits com nome 'Recurso' são de uma branch e os demais são de outra branch**.

Exemplo de commits mesclados com `git rebase`:

```
598c2cc (HEAD -> recurso) Recurso 4
93620ed Recurso 3
9cc02f9 Recurso 2
50e1740 Recurso 1
83dcbae (main) Commit 4
e7c4582 Commit 3
9a12883 Commit 2
e464da1 Commit 1
```

**OBS.: não é recomendado fazer `git rebase` na branch principal, apenas o `git merge`.**