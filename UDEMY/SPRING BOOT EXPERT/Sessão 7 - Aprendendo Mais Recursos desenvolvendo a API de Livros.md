
## 97. Criando as estruturas básicas da API

### Comando `unique`

É inserido em um determinado campo de uma tabela com o intuito de que os valores daquele campo não sejam duplicados. Exemplo:

```sql
create table livro(  
    id uuid primary key not null,  
    isbn varchar(20) not null unique,  
    titulo varchar(150) not null,  
    data_publicacao date not null,  
    genero varchar(30) not null,  
    preco numeric(18, 2) not null,  
    data_cadastro timestamp,  
    data_atualizacao timestamp,  
    id_usuario uuid,  
    id_autor uuid not null references autor(id),  
    constraint chk_genero check (genero in ('FICCAO', 'FANTASIA', 'MISTERIO', 'ROMANCE', 'BIOGRAFIA', 'CIENCIA'))  
);
```

Neste exemplo, o campo `isbn` não terá valores duplicados.

## 98. Endpoint para cadastro de livro com Bean Validation
### Anotação `@ISBN`

É utilizado em um campo de uma classe para verificar se o código passado é um ISBN válido.

**OBS.: ISBN é um código numérico único que identifica livros, artigos, entre outras publicações.**