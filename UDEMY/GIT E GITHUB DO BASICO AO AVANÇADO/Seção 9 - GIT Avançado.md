
## 35. Salvando alterações com Git Stash

Os comandos seguintes são usados para criar ou manipular 'rascunhos' do seu projeto, que ficam armazenados em uma espécie de esconderijo.

- `git stash`: salva as modificações feitas no seu arquivo como uma espécie de 'rascunho' e retorna seus arquivos a um estado anterior.
- `git stash push -m 'descricao'`: cria uma nova stash com uma descrição.
- `git stash list`: lista as stash.
- `git stash show -p <numero da stash>`: exibe o que foi modificado na stash.
- `git stash apply <numero da stash>`: recupera o que foi salvo em uma stash.
- `git stash clear`: apaga todas as stash.
- `git stash drop <numero da stash>`: remove um stash específica.