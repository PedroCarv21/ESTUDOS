
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