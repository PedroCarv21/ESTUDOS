
# Como criar uma relação entre duas entidades por meio de chave commposta?

## Criando uma classe com a chave primária

Suponha que deseje criar a relação entre duas entidades Pedido e Produto:

```
Pedido
------
id
cliente

Produto
--------
id
nome

PedidoProduto
-------------
pedido_id
produto_id
quantidade
preco
```

Para isso é necessário criar primeiro uma classe que contenha a chave composta. Exemplo:

```java
@Embeddable
public class PedidoProdutoId implements Serializable {

    private Long pedidoId;
    private Long produtoId;

    public PedidoProdutoId() {}

    public PedidoProdutoId(Long pedidoId, Long produtoId) {
        this.pedidoId = pedidoId;
        this.produtoId = produtoId;
    }

    // getters e setters

    // equals e hashCode
}
```

A anotação `@Embeddable` serve para indicar que os atributos dessa classe servirão de chave composta para outra entidade.

O JPA obriga a implementar o `Serializable` e também a criação de métodos `equals()` e `hashCode()`.

Agora é preciso criar as entidades Pedido e Produto:

```java
@Entity
public class Pedido {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String cliente;

    @OneToMany(mappedBy = "pedido")
    private List<PedidoProduto> produtos = new ArrayList<>();

}
```

```java
@Entity
public class Produto {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nome;

    @OneToMany(mappedBy = "produto")
    private List<PedidoProduto> pedidos = new ArrayList<>();

}
```

Por fim, é preciso criar a entidade que irá conter dentro de si as chaves compostas:

```java
@Entity
public class PedidoProduto {

    @EmbeddedId
    private PedidoProdutoId id;

    @ManyToOne
    @MapsId("pedidoId")
    @JoinColumn(name = "pedido_id")
    private Pedido pedido;

    @ManyToOne
    @MapsId("produtoId")
    @JoinColumn(name = "produto_id")
    private Produto produto;

    private Integer quantidade;

    private BigDecimal preco;
}
```

A anotação `@EmbeddedId` indica que o id desta entidade não é apenas um único atributo, mas sim um objeto. Desta forma, o Hibernate entende que as chaves compostas de PedidoProduto são os atributos de PedidoProdutoId (pedidoId e produtoId).

Já o `@MapsId` serve justamente para capturar o valor do id do objeto produto ou pedido e armazená-lo nos campos do objeto PedidoProdutoId.