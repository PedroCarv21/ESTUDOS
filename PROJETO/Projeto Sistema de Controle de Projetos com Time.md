
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

# Controllers (sem Spring Security)

## time-controller

### put/times/{id}

#### Requisição

**PathVariable:** id
**RequestParam:** nome
**RequestParam:** status
#### Resposta

```json
{
  "nome": "mobile",
  "status": "ATIVO",
  "dataCriacao": "2026-01-07T18:52:30.976146",
  "dataAtualizacao": "2026-01-08T12:41:36.270379",
  "nomeProjeto": "escola"
}
```
#### Regra de negócio

- Deverá ser passado um novo nome e um status de um time já existente junto com o seu id para o processo de atualização. Os dados atualizados irá aparecer no corpo da resposta.
- Um time só será atualizado se ele não fizer parte de um projeto com o status de **concluído** ou **cancelado**, caso contrário, ocorrerá um `ConflitoException`.
- O campo `nome` não pode receber um valor em branco, caso contrário, será lançado um `MethodArgumentNotValidException`.
- O campo `id` deverá receber o valor id de um time existente, caso contrário, ocorrerá um `NaoEncontradoException`.
### post/times/{id}

#### Requisição

**RequestParam:** nome
**PathVariable:** id
#### Resposta

```json
{
  "nome": "string",
  "status": "ATIVO",
  "dataCriacao": "2026-01-07T18:52:30.976146",
  "dataAtualizacao": "2026-01-08T12:41:36.270379",
  "nomeProjeto": "string"
}
```
#### Regra de negócio

- Será informado o nome de um novo time e o ID de um projeto já existente. O resultado mostrará o nome e o status do novo time e também o projeto ao qual o time pertence.
- Só é possível criar um time em um projeto que ainda não foi **concluído** ou **cancelado**, caso contrário, ocorrerá um `ConflitoException`.
- O campo `nome` não pode receber um valor em branco, caso contrário, será lançado um `MethodArgumentNotValidException`.
- O campo `id` deverá receber o valor id de um projeto já existente, caso contrário, ocorrerá um `NaoEncontradoException`.
### delete/times/{id}

#### Requisição

**RequestParam:** id
#### Resposta

Vazio
#### Regra de negócio

- Este é apenas um delete lógico e, portanto, apenas o status do time é alterado para 'ENCERRADO'.
- O campo `id` deverá receber o valor id de um time existente, caso contrário, ocorrerá um `NaoEncontradoException`.
- Não é possível encerrar um time que já tenha o status 'ENCERRADO'.

### get/times/

#### Requisição

**RequestParam:** nome_projeto
**RequestParam:** nome_time
#### Resposta

```json
[
  {
    "nome": "backend",
    "status": "ATIVO",
    "dataCriacao": "2026-01-07T18:52:30.976146",
    "dataAtualizacao": "2026-01-08T12:41:36.270379",
    "nomeProjeto": "EscolaHoje"
  },
  {
    "nome": "frontend",
    "status": "ATIVO",
    "dataCriacao": "2026-01-07T18:52:44.358741",
    "dataAtualizacao": "2026-01-08T12:41:36.270379",
    "nomeProjeto": "EscolaHoje"
  },
  {
    "nome": "mobile",
    "status": "ATIVO",
    "dataCriacao": "2026-01-07T19:03:04.559413",
    "dataAtualizacao": "2026-01-08T13:23:52.801337",
    "nomeProjeto": "EscolaHoje"
  }
]
```
#### Regras de negócio

- Irá listar todos os times do projeto cujo nome foi informado. Informar o nome do time é opcional.
- Deve digitar um nome existente de um projeto, caso contrário, ocorrerá um `NaoEncontradoException`.
- O campo `nome_projeto` não pode receber um valor em branco, caso contrário, será lançado um `MethodArgumentNotValidException`.
## projeto-controller

### put/projetos/{id}

#### Requisição

**PathVariable:** id
**RequestParam:** nome
**RequestParam:** status
#### Resposta

```json
{
  "nome": "string",
  "dataCriacao": "2026-01-08T18:47:55.977Z",
  "dataAtualizacao": "2026-01-08T18:47:55.977Z",
  "status": "INICIADO"
}
```
#### Regra de negócio

- Caso o novo valor do status seja atualizado para 'CONCLUIDO', os status de todos os times vinculado a este projeto ficarão como 'ENCERRADO'. Caso deseje alterar novamente o status do projeto para 'INICIADO' ou 'EM_ANDAMENTO', o status de todos os times deste projeto ficarão como 'ATIVO'.
- O campo `nome` não pode receber um valor em branco, caso contrário, será lançado um `MethodArgumentNotValidException`.
- O campo `id` deverá receber o valor id de um projeto já existente, caso contrário, ocorrerá um `NaoEncontradoException`.
### delete/projetos/{id}

#### Requisição

**PathVariable:** id
#### Resposta

Vazio
#### Regra de negócio

- Ao 'deletar' o projeto, o status será atualizado para 'CANCELADO' e os status de todos os times vinculados a este projeto ficarão como 'ENCERRADO'.
- O campo `id` deverá receber o valor id de um projeto já existente, caso contrário, ocorrerá um `NaoEncontradoException`.
- Se o projeto já foi 'deletado' uma outra vez, e está sendo feito a tentativa de deletá-lo novamente, ocorrerá uma `ConflitoException`.
### get/projetos/

#### Requisição

**RequestParam:** pagina
**RequestParam:** tamanho_pagina
**RequestParam:** nome
**RequestParam:** status
#### Resposta

```json
{
  "content": [
    {
      "nome": "cassino",
      "dataCriacao": "2026-01-05T21:32:30.093548",
      "dataAtualizacao": "2026-01-05T21:32:30.093548",
      "status": "INICIADO"
    },
    {
      "nome": "futebol",
      "dataCriacao": "2026-01-08T12:43:22.415206",
      "dataAtualizacao": "2026-01-08T12:43:22.415206",
      "status": "INICIADO"
    },
    {
      "nome": "EscolaHoje",
      "dataCriacao": "2026-01-05T21:32:22.901865",
      "dataAtualizacao": "2026-01-08T13:47:26.677934",
      "status": "INICIADO"
    }
  ],
  "empty": false,
  "first": true,
  "last": true,
  "number": 0,
  "numberOfElements": 3,
  "pageable": {
    "offset": 0,
    "pageNumber": 0,
    "pageSize": 3,
    "paged": true,
    "sort": {
      "empty": true,
      "sorted": false,
      "unsorted": true
    },
    "unpaged": false
  },
  "size": 3,
  "sort": {
    "empty": true,
    "sorted": false,
    "unsorted": true
  },
  "totalElements": 3,
  "totalPages": 1
}
```

#### Regra de negócio

- Será realizado uma pesquisa página, de modo que seja informado:
	- A quantidade de elementos por por página (o valor padrão é 3).
	- Em qual página deseja estar (a página padrão é 0).
	- O nome do projeto em especial.
	- O status atual do projeto.
### post/projetos/

#### Requisição

**RequestParam:** nome
#### Resposta

```json
{
  "nome": "Hotel+",
  "dataCriacao": "2026-01-08T16:46:14.4244815",
  "dataAtualizacao": "2026-01-08T16:46:14.4244815",
  "status": "INICIADO"
}
```
#### Regra de negócio

- O campo `nome` não pode receber um valor em branco, caso contrário, será lançado um `MethodArgumentNotValidException`.
