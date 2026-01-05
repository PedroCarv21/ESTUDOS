
# Descrição

O objetivo é fornecer uma ferramenta capaz de estruturar qualquer projeto em desenvolvimento (independente de qual seja) a partir da divisão de permissões em três papeis:

- Administrador: pode criar, editar e excluir qualquer coisa dentro do projeto.
- Gerente: pode criar, editar e excluir qualquer coisa **apenas dentro do seu time**.
- Membro: pode apenas mudar o status da tarefa que lhe foi designada e criar, editar e excluir seu próprio comentário.
# Camadas
 
## Projeto

### GET/

- Ver informações de todos os projetos que **participa**.
- **Autorização**: TODOS

### GET/nome

- Buscar informações de um projeto específico com base no nome.
- **Autorização**: TODOS

### POST/

- Criar projeto.
- **Autorização**: ADM

### PUT/

- Atualizar informações do projeto.
- **Autorização**: ADM

### DELETE/

- Deletar projeto
- **Autorização**: ADM

**OBS: É SOMENTE UM DELETE LÓGICO**
## Time

### GET/

- Ver informações de todos os times que **participa**.
- **Autorização**: TODOS

### GET/nome

- Buscar informações de um time específico com base no nome.
- **Autorização**: TODOS

### POST/

- Criar time.
- **Autorização**: ADM e MANAGER

### PUT/

- Atualizar informações do time.
- **Autorização**: ADM e MANAGER

### PUT/adicionar_membros

- Adicionar novos membros
- **Autorização**: ADM e MANAGER

### PUT/excluir_membros

- Excluir membros.
- **Autorização**: ADM e MANAGER

**OBS.: QUANDO EXCLUIR OS MEMBROS DO TIME, DEVE EXCLUIR TAMBÉM SUA PARTICIPAÇÃO NAS TAREFAS.**
### DELETE/

- Deletar time
- **Autorização**: ADM e MANAGER
## Tarefa

### GET/

- Ver informações de todos as tarefas que **participa**.
- **Autorização**: TODOS

### GET/nome

- Buscar informações de um tarefa específico com base no nome.
- **Autorização**: TODOS

### POST/

- Criar tarefa.
- **Autorização**: ADM e MANAGER

### PUT/

- Atualizar informações do projeto.
- **Autorização**: ADM e MANAGER

### PUT/adicionar_membros

- Incluir novos membros/gerente na tarefa.
- **Autorização**: ADM e MANAGER

### PUT/excluir_membros

- Excluir membros/gerente na tarefa.
- **Autorização**: ADM e MANAGER
### DELETE/

- Deletar tarefa
- **Autorização**: ADM

**OBS.: É NECESSÁRIO TAMBÉM DELETAR OS COMENTÁRIOS VINCULADOS A TAREFA.**
## Comentário

### GET/

- Ver informações de todos os comentários que **escreveu**.
- **Autorização**: TODOS

### POST/

- Criar comentário.
- **Autorização**: TODOS

### PUT/

- Atualizar informações do comentário.
- **Autorização**: TODOS
### DELETE/

- Deletar comentário
- **Autorização**: TODOS

# Papeis

## ADM

O seu diferencial dentre os demais é:

- Manipular projetos.
- Excluir membros e gerentes.
- Ela não será incluído em nenhum time.
- Ele não ficará responsável por qualquer tarefa.

De resto, ele pode fazer tudo.
## MANAGER

- Manipular membros do seu próprio time.
- 
## MEMBRO

Dentre as suas funcionalidades estão:

- Mudar o status da tarefa.
- Manipular o comentário da tarefa.
- Atualizar suas próprias informações.


| AUTORIZAÇÕES                                | ADM | MANAGER | MEMBER |
| ------------------------------------------- | --- | ------- | ------ |
| Criar, atualizar e deletar projeto          | SIM | NÃO     | NÃO    |
| Criar time                                  | SIM | NÃO     | NÃO    |
| Deletar time                                | SIM | NÃO     | NÃO    |
| Adicionar e excluir tarefas do time         | SIM | SIM     | NÃO    |
| Adicionar e trocar gerente do time          | SIM | NÃO     | NÃO    |
| Adicionar e excluir membros do time         | SIM | SIM     | NÃO    |
| Atualizar nome e status do time             | SIM | SIM     | NÃO    |
| Criar e excluir tarefa                      | SIM | SIM     | NÃO    |
| Atualizar nome da tarefa                    | SIM | SIM     | NÃO    |
| Atualizar status da tarefa                  | SIM | SIM     | SIM    |
| Adicionar, atualizar e excluir comentários  | SIM | SIM     | SIM    |
| Vincular e desvincular membros a uma tarefa | SIM | SIM     | NÃO    |

