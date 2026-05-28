
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


# 87. Transações

A transação é um processo que garante o sucesso na execução de todas as requisições em conjunto; caso alguma das requisições falhe, todo o resto das requisições será desfeito, garantindo a integridade dos dados. O PgAdmin utiliza a transação durante **qualquer instrução SQL por padrão.** Esses são os comandos utilizados durante a transação:

- `begin`: inicia uma transação. Coloque antes da sequência de comandos.
- `rollback`: desfaz as alterações causadas pela transação.  Coloque depois da sequência de comandos.
- `commit`: em vez de `rollback`, pode-se utilizar esse comando para salvar as alterações causadas pela transação. Coloque depois da sequência de comandos.

# 88. Backup e restore

- **backup**: botão direito no banco de dados que deseja fazer o backup → `Backup...` → Em `Filename`, clique no 📁para escolher o local do seu backup → clique em `Backup`.
- **restore**: botão direito no `Databases` → `Create` → `Database...` → botão direito no banco de dados que acabou de criar → `Refresh...` → Em `Filename`, clique no 📁para encontrar o seu backup → `Restore`
