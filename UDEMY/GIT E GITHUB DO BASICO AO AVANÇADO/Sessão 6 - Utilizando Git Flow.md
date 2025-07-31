
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