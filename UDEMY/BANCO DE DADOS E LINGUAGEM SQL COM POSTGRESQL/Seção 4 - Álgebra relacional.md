
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

# 93. Project + select, união e intersecção

Coloque primeiro a operação project e depois select. Exemplo:

```
π name, country σ age > 20 ∧ gender = 'female' (tourist)
```

## Intersecção e união

É possível também utilizar os símbolos `∩` e `∪` para intersecção e união. Exemplo:

```
π tcode (stay) ∩ π tcode (tourist)
```
# 94. Joins

Utilize o símbolo de left outter join (`⟕`) ou natural (inner) join (`⨝`). A estrutura deve ser essa:

```
π tabela1.nome, tabela2.nome (tabela1 tabela1.t1code = tabela2.t1code tabela2)
```

Exemplo de duas tabelas (hotel e tourist) fazendo join com a tabela stay:

```
π hotel.name, tourist.name, stay.year, stay.days, stay.cost (hotel ⟕ hotel.hcode = stay.hcode stay ⟕ stay.tcode =  tourist.tcode tourist)
```
## Apelido para a tabela

Utilize o `ρ`, depois o apelido e, por fim, o nome da tabela.

```
π h.name, t.name, s.year, s.days, s.cost (ρ h hotel ⟕ h.hcode = s.hcode ρ s stay ⟕ s.tcode =  t.tcode ρ t tourist)
```
# 95. Agrupamentos

Utilize o γ para realizar o agrupamento. A estrutura deve ser assim:

```
γ coluna1 ; sum(coluna2)->apelido (tabela1)
```

**OBS.: assim como o sql, a algebra relacional aceita as funções para agrupamento (`sum`, `avg`, etc...).**

Exemplo simples:

```
γ tcode ; sum(cost)->total (participate)
```

Exemplo de agrupamento com join:

```
γ hotel.hcode, hotel.name ; sum(cost)->soma (stay ⟕ stay.hcode = hotel.hcode hotel)
```