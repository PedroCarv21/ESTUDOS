
# 91. Operação project

## O que é algebra relacional?

Linguagem de requisição que utiliza de operadores matemáticos para realizar ações no banco de dados. Para realizar operações desse tipo, utilize o https://relax.mad.uom.gr/help.htm.

Para escolher o banco, clique em `UIBK - R, S, T` e selecione um dos bancos no canto esquerdo ou carregue um novo banco de dados em `Create new Dataset`.

![[Pasted image 20260527215129.png]]

## Project

Utiliza o símbolo `π` para realizar consultas no banco de dados. É necessário informar o `π` seguido do nome das colunas desejadas e, por fim, o nome da tabela entre parênteses. Exemplo:

```
π acode, aname, duration_in_minutes (activity)
```

### Coméntário

Coloque um `--` antes do comando.
# 92. Operação select

Utiliza-se o `σ` para filtrar as consultas. Coloque esse símbolo, a condição e o nome da tabela entre parênteses.

```
σ year = 2001(participate)
```

É possível também utilizar o `∧` (E) ou o `∨` (OU) no filtro:

```
σ year = 2001 ∨ year = 2003 (participate)
```

