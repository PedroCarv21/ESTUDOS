
# 7 - Instalação de ferramentas

## O que é pgAdmin?

Ferramenta utilizada para acessar as bases de dados PostgreSQL.

# 8 - Tabela de clientes

## Diferença entre `char` e `varchar`

- **`char`**: sempre armazenará no disco rígido o valor informado entre parênteses. Por exemplo: `cpf char(11)` sempre armazenará 11 caracteres, não importando se é ou não utilizado 11 caracteres em um dado registro.
- **`varchar`**: só armazena um número de caracteres de acordo com o valor passado. Por exemplo: `nome varchar(50)` é um campo que armazena no máx. 50 caracteres, mas se for passado um valor como `Pedro`, então só serão armazenados 5 caracteres no disco rígido.

## Comentários

Utilize o `--` antes do conteúdo que será transformado em comentário.

## Restrição

A restrição, criada através do `constraint`, impõe uma determinada regra a um campo específico. Um exemplo é o `primary key`, que determina um valor único em um campo específico para cada registro. Essa restrição seria criada desta forma:

```sql
create table clientes(
	id integer not null,
	nome varchar(100) not null,
	email varchar(100) not null,
	
	constraint id_cln primary key (id)
)
```

Isso significa que dois ou mais registros da tabela cliente não poderão ter o mesmo valor no campo 'id'.

# 9 - Inserção de dados

Para fazer a inserção de dados, é necessário informar `insert into <nome do banco> (campo1, campo2) values (1, 'Pedro')`.


# 12 - Consulta simples 1

## Renomeação de colunas

Utilize a palavra-chave `as` para renomear uma coluna:

```sql
select nome, data_nascimento as "Data de Nascimento" from cliente;
```

**OBS.: o nome deve estar entre aspas duplas.**
## Concatenação do valor dos registros

Utilize o `||` para concatenar um texto com um valor de um registro.

```sql
select 'CPF: ' || cpf || 'RG: ' || rg as "CPF e RG" from cliente
```

## Limitando o número de registros

Utilize a palavra-chave `limit` e, em seguida, informe a quantidade de registros desejada.

```sql
select * from cliente limit 3;
```

# 13 - Consultas simples 2

## Filtrando consulta com base na data

É possível buscar registros cujo o valor de alguma coluna seja menor ou maior que uma data específica:

```sql
select * from cliente where data_nascimento > '2000-01-01';
```

Há também como buscar registros cujo o valor referente a alguma coluna esteja entre uma e outra data, através da palavra-chave `between` e `and`.

```sql
select nome, data_nascimento 
from cliente 
where data_nascimento between '1990-01-01' and '2020-12-31';
```

## Buscando registros com valores nulos

Utilize o comando `is null`

```sql
select nome, rg from cliente where rg is null;
```

## Ordenando registros em uma busca

Utilize o comando `order by` e, em seguida, a coluna utilizada como critério para a ordenação.

```sql
select nome, data_nascimento 
from cliente 
order by data_nascimento asc;
```

**OBS.: o `asc` é opcional.**

Caso queira em ordem decrescente, utilize o comando `desc`:

```sql
select nome, data_nascimento 
from cliente 
order by data_nascimento desc;
```

# 17. Comandos update e delete

## Atualização de múltiplos campos

Basta colocar a atualização de cada campo separado por vírgula:

```sql
update cliente set genero = 'F', profissao = 'Professora', numero = '123'
where idcliente = 18;
```

# 20. Criação de mais tabelas

É possível exigir de uma coluna valores únicos para cada um dos registros:

```sql
create table bairro(
	idbairro integer not null,
	nome varchar(30) not null,

	constraint pk_brr_idbairro primary key (idbairro),
	constraint un_brr_nome unique (nome)
);
```

# 21. Chaves estrangeiras 1

## Alterando nome da coluna

Utilize o comando `alter table <nome_tabela> rename <nome_atual_coluna> to <novo_nome_coluna>;`.

## Alterando o tipo de uma coluna

Utilize o comando `alter table <nome_tabela> alter column <nome_coluna> type <novo_tipo>`. Por exemplo:

```sql
alter table cliente alter column idprofissao type integer;
```

## Apagando coluna da tabela

`alter table <nome_tabela> drop column <nome_coluna>`

## Adicionando coluna na tabela

`alter table <nome_tabela> add column <nome_coluna> <tipo>`

## Adicionando uma chave estrangeira

Chave estrangeira é uma coluna ou conjunto de colunas em uma tabela que estabelece um vínculo com a chave primária de outra tabela. Este é o comando:

```sql
alter table <nome_tabela_com_chave_estrangeira>
add constraint <nome_chave_estrangeira> foreign key (<coluna_chave_estrangeira>) references <nome_tabela_com_chave_primaria> (<coluna_chave_primaria>);
```

## Atualizando valores de uma coluna de uma vez só

```sql
update <nome_tabela> set <coluna_que_tera_valores_alterados> = <valor> where <coluna_qualquer> in (<valor1>, <valor2>, <valor3>, etc.);
```

# 28. Tabela de pedidos 2

## Criação de chave primária composta

A chave primária composta é formada por dois ou mais campos que, juntos, seus valores não podem se repetir mais de uma vez. Para criar uma chave primária composta, basta colocar entre parênteses o nome das colunas que farão parte desta chave. Exemplo:

```sql
create table pedido_produto(
	idpedido integer not null,
	idproduto integer not null,
	quantidade integer not null,
	valor_unitario float not null,

	constraint pk_pdp_idpedidoproduto primary key (idpedido, idproduto),
	constraint fk_pdp_idpedido foreign key (idpedido) references pedido (idpedido),
	constraint fk_pdp_idproduto foreign key (idproduto) references produto (idproduto)
);
```

# 31. Solução 2

## Operador de comparação `<>`

É um operador de comparação que significa “diferente de” (not equal). Significa o mesmo que `!=`. Exemplo:

```sql
SELECT *
FROM clientes
WHERE idade <> 18;
```

# 32. Funções agregadas

## `avg`

Calcula a média do valor de alguma coluna. Neste exemplo, será calculado a média de todos os valores presentes na coluna `valor` da tabela `pedido`

```sql
select avg(valor) as media
from pedido;
```

É possível também selecionar quais registros serão considerados para o cálculo da média. Exemplo:

```sql
select avg(valor) from pedido
where idcliente = 9;
```

## `count`

Retorna a quantidade de registros não nulos com base em uma determinada coluna. Exemplo:

```sql
select count(cpf) from cliente;
```

Se quiser incluir valores não nulos na contagem, utilize `count(*)`.
## `min` e `max`

Retorna o valor mínimo e o valor máximo de uma tabela.

```sql
select min(valor) as minimo, max(valor) as maximo
from pedido;
```

## `sum`

Retorna a soma de todos os valores de uma determinada coluna:

```sql
select sum(valor)
from pedido;
```
## Comandos `group by` e `having`

Quando for preciso selecionar uma função agregada e mais uma coluna, é necessário utilizar o `group by <nome_coluna>` para saber qual coluna a consulta se baseará para fazer um agrupamento. Exemplo:

```sql
select idcliente, sum(valor) 
from pedido
group by idcliente;
```

Caso ainda queira filtrar a consulta, em vez de `while`, utilize a palavra-chave `having` da seguinte forma:

```sql
select idcliente, sum(valor) 
from pedido
group by idcliente
having sum(valor) > 500;
```

É possível agrupar linhas que possuem a mesma combinação de duas ou mais colunas. Exemplo:

```sql
select idcliente, idvendedor, valor
from pedido;
```

Suponha que o resultado fosse esse:

| idcliente | idvendedor | valor |
| --------- | ---------- | ----- |
| 1         | 1          | 1300  |
| 1         | 1          | 500   |
Caso precise, por exemplo, somar os valores com base no idcliente e no idvendedor, o comando sql seria esse:

```sql
select idcliente, idvendedor, sum(valor)
from pedido
group by idcliente, idvendedor;
```

E o resultado seria esse:

| idcliente | idvendedor | valor |
| --------- | ---------- | ----- |
| 1         | 1          | 1800  |

# 38. Relacionamentos com joins

## left outer join (left join)

Retorna todos os registros da tabela esquerda e os correspondentes da direita. Exemplo:

Tabela de clientes

| cliente | idproduto |
| ------- | --------- |
| Pedro   | 1         |
| Maria   | null      |
| null    | 2         |

Tabela de produtos:

| idproduto | nome    |
| --------- | ------- |
| 1         | TV      |
| 2         | celular |

Se fosse executado o seguinte comando:

```sql
select c.cliente, p.nome
from clientes c
left outer join
produtos p
on c.idproduto = p.idproduto;
```

**OBS.: o comando `outer` é opcional.**

O resultado da consulta seria:

| cliente | nome    |
| ------- | ------- |
| Pedro   | TV      |
| Maria   | null    |
| null    | celular |

## right outer join (right join)

Retorna todos os registros da tabela direita e os correspondentes da esquerda. Considerando ainda as tabelas de clientes e de produtos e utilizando agora o seguinte comando:

```sql
select c.cliente, p.nome
from clientes c
right outer join
produtos p
on c.idproduto = p.idproduto;
```

O resultado seria:

| cliente | nome    |
| ------- | ------- |
| Pedro   | TV      |
| null    | celular |

## inner join

Já o inner join retorna  apenas os registros que possuem correspondência nas duas tabelas. Se o comando fosse:

```sql
select c.cliente, p.nome
from clientes c
inner join produtos p
on c.idproduto = p.idproduto;
```

O resultado seria:

| cliente | nome    |
| ------- | ------- |
| Pedro   | TV      |
| NULL    | celular |

# 43. Comandos adicionais

## Extraindo partes da data

Separe o valor do dia, mês ou ano a partir da data através do comando `extract()` e dos comandos:
- `day from`
- `month from`
- `year from`

```sql
select data_pedido, extract (day from data_pedido) as dia from pedido;
select data_pedido, extract (month from data_pedido) from pedido;
select data_pedido, extract (year from data_pedido) from pedido;
```

## Extraindo caracteres de uma string

A função `substring` recebe a coluna que contém as strings seguido de um destes dois comandos:

- `from <numero> for <numero>`: determina aonde começa e termina a leitura da string.
- Depois do nome da coluna, informe a posição onde deve começar a leitura da string.

```sql
select nome, substring(nome from 1 for 5) from cliente;
select nome, substring(nome, 2) from cliente;
```

## Funções `upper` e `lower`

Torna os valores de uma determinada coluna maiúsculos ou minúsculos:

```sql
select upper(nome) from cliente;
select lower(nome) from cliente;
```

## Função `coalesce` 

Caso a coluna passada como parâmetro desta função retorne `null`, é possível informar um valor, como segundo parâmetro, que substituirá o valor `null`

**OBS.: o valor substituto deve ser do mesmo tipo que o tipo da coluna.**

```sql
select nome, cpf, coalesce(cpf, 'Não informado') from cliente;
```

## Comandos `case`, `when`, `then`, `else`, `end`

Esses comandos são utilizados para criar uma estrutura condicional: caso o valor da coluna X seja Y, então retorne P.

```sql
select 
	sigla, 
	case sigla
		when 'SC' then 'Santa Catarina'
		when 'SP' then 'Sao Paulo'
	else 'Outros'
	end as estados
from uf;
```

Caso deseje utilizar operadores relacionais, coloque o nome da coluna depois do `when`:

```sql
select 
	nome, 
	case
		when valor > 500 then 'Acima de 500'
		when valor < 500 then 'Abaixo de 500'
	else '500.00'
	end
from produto;
```

# 46. Subconsultas

São consultas dentro de outras consultas
## Exemplo 1

Consultar os registros da tabela pedido cujo o valor é maior que a média.

```sql
select data_pedido, valor
from pedido
where valor > (select avg(valor) from pedido);
```

## Exemplo 2

Selecionar a data e o valor do pedido assim como a quantidade total de produtos por pedido.

```sql
select 
	data_pedido, 
	valor,
	(select sum(quantidade) from pedido_produto pp where pp.idpedido = p.idpedido)
from pedido p;
```
## Exemplo 3

É possível utilizar a subconsulta dentro de comandos `update`. Por exemplo: aumentar em 5% os valores que forem maior que a média dos valores dos pedidos.

```sql
update pedido set valor = valor + ((valor * 5) / 100)
where valor > (select avg(valor) from pedido);
```

# 50. Views

A view nada mais é do que uma consulta armazenada e que pode ser retornada através de um apelido que foi dado a ela. 

Para criar uma view, utilize o comando `create view <apelido> as` e escolha uma determinada consulta. Por exemplo:

```sql
create view cliente_profissao as 
select cln.nome as cliente, prf.nome as profissao, cln.cpf
from cliente cln
left outer join profissao prf
on cln.idprofissao = prf.idprofissao;
```

Caso dê um apelido para as colunas da consulta (`cln.nome as cliente, prf.nome as profissao`), é necessário, na hora em que for consultar a view, informar os apelidos e não o nome original da coluna. Exemplo:

```sql
select cliente from cliente_profissao
```

Caso queira apagar a view, execute o comando `drop view <nome_view>`.

# 54. Autoincremento

## Comando `serial`

É utilizado no lugar do tipo de um campo e serve para gerar um incremento automático. Por exemplo:

```sql
create table exemplo(
	idexemplo serial not null,
	nome varchar(50) not null,

	constraint pk_exemplo_idexemplo primary key (idexemplo)
);
```

Neste caso, não será mais necessário informar manualmente o valor do campo `idexemplo`. Isso criará uma sequência numérica, que ficará disponível no menu esquerdo em `Sequences`.

Para acessar as propriedades da sequência, é necessário: ir no menu esquerdo e procurar por `Sequences` → botão direito → `Properties` → `Definition`.
## Como vincular uma sequência a um campo de uma tabela?

É necessário criar uma sequência, informando o menor valor inicial para essa sequência. Por exemplo, se o maior valor presente na coluna daquela tabela foi 4, então o menor valor inicial da sequência deve ser 5.

```sql
create sequence bairro_id_seq minvalue 5;
```

Agora é preciso definir essa sequência como valor padrão para a coluna da tabela desejada. Isso é feito através do comando `set default nextval('nome_sequencia')`, sendo que a função `nextval()` pega o próximo número disponível de uma sequência.

O comando `default` é uma restrição (constraint) aplicada a colunas de tabelas para definir um valor automático caso nenhum valor seja explicitamente inserido durante uma operação INSERT.

```sql
alter table bairro 
alter idbairro 
set default nextval('bairro_id_seq')
```

Por fim, informe a qual tabela e coluna essa sequência pertence com o comando `owned by`:

```sql
alter sequence bairro_id_seq owned by bairro.idbairro;
```

# 57. Campos default

## Incremento automático da data atual

Utilize o comando `set default current_date` para preencher automaticamente o campo de data. Exemplo:

```sql
alter table pedido
alter column data_pedido
set default current_date;
```

## Incremento automático de valores inteiros

É recomendado que, para campos que indiquem o preço de alguma coisa, haja um preenchimento automático desse campo com o valor zero, caso contrário, poderá ocorrer um erro na hora de calcular, pois haverá com o valor `null`. Exemplo:

```sql
alter table pedido
alter column valor
set default 0;
```

# 60. Índices

Os índices são utilizados para acelerar a consulta de alguma tabela do banco. Essa é a sintaxe:

```sql
create index nome_do_index on nome_tabela (nome_coluna);
```

Exemplo de índice utilizado para consulta na coluna 'nome' da tabela 'cliente':

```sql
create index idx_client_nome on cliente (nome);
```

# 62. Solução

Para apagar um índice, execute o comando `drop index` mais o nome do índice.

# 64. Correção avaliação 1

## Como alterar o limite de caracteres em um campo?

```sql
alter table tabela
alter column coluna type varchar(100);
```

# 68. Correção de avaliação 5

## Comando `distinct`

Essa função é utilizada para que os valores de uma determinada coluna não apareçam repetidos. No seguinte exemplo, cada um dos valores da coluna `livro_emprestado` só aparecerá uma vez.

```sql
select distinct(l.nome) as livro_emprestado from emprestimo_livro el
inner join livro l
on el.idlivro = l.idlivro;
```

# 72. Funções

## Funções `concat`, `round` e `cast`

- `concat`: junta um texto com outro texto/valor. Por exemplo: `concat('R$', valor)`.
- `round`: define a quantidade de casas decimais. Exemplo: `round(valor, 2)`. É necessário que o primeiro argumento seja do tipo `numeric` ou `double precision`.
- `cast`: converte o tipo de um valor para outro. Exemplo: `cast(valor as numeric)`.

É possível utilizar as funções ao mesmo tempo tempo: transformar em decimal, expondo apenas duas casas decimais e que ele tenha 'R$' antes. Exemplo:

```sql
select valor, concat('R$ ', round(cast(valor as numeric), 2)) from pedido;
```

## Criando funções

Este é a estrutura padrão para criação de uma função:

```sql
create function nome_da_funcao(parametro tipo) returns tipo_retornado language plpgsql as
$$
begin
	-- corpo da função
end;
$$;
```

- `language plpgsql` significa que a função usa a linguagem procedural do PostgreSQL chamada **PL/pgSQL**.
- O `$$` é **dollar-quoting**, responsável por delimitar o corpo de uma função.
- Já o `begin` e o `end` servem para delimitar o bloco de código **executável** da função.

É possível também criar funções com variáveis através do comando `declare`. Exemplo:

```sql
create function get_nome_by_id(idc integer) returns varchar(50) language plpgsql as
$$
declare r varchar(50);
begin
	select nome into r from cliente where idcliente = idc;
	return r;
end;
$$;
```

O comando `into` significa que o dado relacionado ao campo `nome` que for encontrado na consulta deverá ser armazenado na variável `r`.

É possível, neste caso, optar por não utilizar uma variável:

```sql
create function get_nome_by_id2(idc integer) returns varchar(50) language plpgsql as
$$
begin
	return (select nome from cliente where idcliente = idc);
end;
$$;
```

Para executar a função, utilize o comando `select`:

```sql
select get_nome_by_id(idcliente) as nome, data_pedido, valor 
from pedido;
```

# 74. Solução

É possível também definir uma função sem nenhum parâmetro, mas é necessário colocar o `()` depois do nome.

```sql
create function maior () returns integer language plpgsql as
$$
declare r integer;
begin
	select idpedido into r from pedido where valor = (select max(valor) from pedido);
	return r;
end;
$$;
```

Neste caso, é preciso executar da seguinte forma:

```sql
select maior();
```

# 75. Stored procedures

## Diferença entre função e procedure

Funções não controlam transações (como `BEGIN`, `COMMIT`, `ROLLBACK`) e devem retornar um valor, enquanto procedimentos podem controlar transações e não retornam valores diretamente.

## Como criar um procedure

```sql
create procedure nome_procedure(parametro tipo) language sql as
$$
	-- corpo do procedure
$$;
```

Para executar o procedure, utilize o comando `call`. Exemplo:

```sql
create procedure insere_bairro(nome_bairro varchar(30)) language sql as
$$
	insert into bairro (nome) values (nome_bairro);
$$;

call insere_bairro ('Teste procedure');
```

O que este código faz é: inserir um novo registro na tabela `bairro`.

# 78. Triggers

Procedimento automatizado que instrui o banco de dados a executar uma função específica sempre que um evento de manipulação de dados (como `INSERT`, `UPDATE` ou `DELETE`) ocorrer em uma tabela ou view.

## Como criar uma função configurada para ser executada por uma trigger

Primeiro, é necessário criar uma função que deva ser executada sempre que um evento ocorrer. Exemplo:

```sql
create function bairro_log() returns trigger language plpgsql as
$$
begin
	insert into bairro_auditoria (idbairro, data_criacao) values (new.idbairro, current_timestamp);
	return new;
end
$$;
```

- `returns trigger` informa que essa função será executada por uma trigger.
- `new` representa a nova linha inserida/alterada em outro local. Portanto, neste caso, `new.idbairro` se refere ao valor do novo registro referente ao campo `idbairro`. **Neste exemplo, `idbairro` não se refere a um campo da tabela `bairro_auditoria`, mas da tabela `bairro`. O vínculo com esta tabela fica mais claro com a criação da trigger.**


**OBS.: o tipo `timestamp` é usado para representar data e hora. O comando `current_timestamp` é usado inserir o valor da data e hora atual.**
## Criando a trigger

Em seguida, é necessário criar a trigger, informando que ela acionará uma função assim que um evento ocorrer. Exemplo:

```sql
create trigger log_bairro_trigger after insert on bairro 
for each row execute procedure bairro_log();
```

O que esse código diz é: crie uma trigger chamada `log_bairro_trigger` que, para cada linha inserida na tabela `bairro`, executará a função `bairro_log`.

# 80. Solução

Quando se tratar de executar uma trigger quando houver a deleção de um registro em uma tabela, use o comando `old` em vez de `new`. Em suma:

- `OLD` → valores antes da operação.
- `NEW` → valores depois da operação.

# 81. Domínios

 É um tipo de dado personalizado que você cria. Ele combina um tipo de dado base (como VARCHAR ou INTEGER) com regras ou restrições específicas (como valores padrão ou limites numéricos).

```sql
create domain nome_domain as tipo;
```


# 84. Usuários e permissões

## Criação de usuários e papeis

Os papeis (roles) são utilizados para determinar quais tipos de ações um usuário poderá executar. Para criar um papel, use o comando `create role nome_role`.

Para definir quais serão as limitações da role, use os comandos `grant role comando_permitido on tabela to nome_role with grant option`. Enquanto o comando `grant` concede permissão para execução de um comando, o comando `with grant option` concede autorização ao usuário relacionado a esse papel para repassar essas permissões a outros usuários.

Uma analogia simples:

- `GRANT` = você recebeu uma chave.
- `WITH GRANT OPTION` = você também recebeu autorização para fazer cópias da chave e entregar para outras pessoas.

Exemplo real:

```sql
grant select, insert, delete, update on bairro, cliente
to gerente with grant option;
```

Muitas tabelas utilizam `sequences`, portanto, é preciso conceder também acesso ao papel:

```sql
grant all on sequence to nome_role with grant option;
```

Você pode também conceder acesso a todos os `sequences`:

```sql
grant all on all sequences in schema public to gerente;
```

Por fim, é preciso criar um usuário e vinculá-lo a um papel:

```sql
create role nome_usuario login password 'senha' in role nome_role;
```