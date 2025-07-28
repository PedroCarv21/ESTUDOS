
## 16. Entendendo mais sobre Branch

Comandos principais quanto a branches:

- `git branch <nome da branch>`: cria uma nova branch.
- `git branch`: lista as branches existentes.
- `git checkout <nome da branch>`: troca de uma branch para outra.

## 17. Operações básicas com Branch

Outros comandos relacionado a branch:

- `git branch -d <nome da branch>`: remove a branch informada.
- `git checkout -b <nome da branch>`: cria uma nova branch e troca para essa branch.
- `git merge <nome da branch>`: mescla o conteúdo das duas branches. Utilize esse comando quando estiver localizado na branch `main`.

## 18. Trabalhando com branch na prática

### Arquivos criados em branches específicas

Ao commitar um arquivo `untracked` para uma branch específica (e não a `main`), isso fará com que o arquivo se mostre visível na pasta do repositório local apenas quando estiver nesta branch específica.

Por exemplo, o arquivo chat.txt se mostra visível na branch em que ele foi commitado (`chat`) e não na `main`.

![[Pasted image 20250725170156.png]]

![[Pasted image 20250725170256.png]]

## 19. Subindo alterações em uma nova Branch

Ao fazer novos commits em uma branch diferente da `main`, é necessário que, para subir esses commits, você execute o comando `git push -u origin` mais o nome da branch específica. Isso fará com que seja criado uma nova branch com o mesmo nome no repositório remoto. É nesta nova branch onde estarão os commits que acabou de subir.

![[Pasted image 20250728175258.png]]