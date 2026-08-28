
# Introdução à Programação oo em Java

## Tipos de relações entre objetos

- **Associação:** é a relação mais fraca e se refere a objetos que consomem serviços ou funcionalidades de outros. Ela pode ocorrer mesmo quando nenhuma classe possui a outra e cada objeto instanciado tem sua existência independente do outro. Essa relação pode ocorrer com cardinalidade “um para um”, “um para vários”, “vários para um” e “vários para vários”.
- **Agregação:** ocorre entre dois ou mais objetos, com cada um tendo seu próprio ciclo de vida, mas com um objeto (pai) contendo os demais (filhos). Precisamos compreender que, nesse caso, os objetos filhos podem sobreviver à destruição do objeto pai.
- **Composição:** ocorre quando há uma relação de dependência entre o(s) filho(s) e o objeto pai. Caso o pai deixe de existir, necessariamente o filho será destruído.

## O que é referência?

É o endereço na memória do computador que aponta para um objeto. Em vez de guardar o objeto inteiro em uma variável, o programa guarda um "atalho" ou "ponteiro".

## Mecanismos de visibilidade

- **Default:** visibilidade restrita ao pacote do Java.
- **Private**
- **Public**
- **Protected:** restrita ao pacote e a todas as subclasses.

## Método `Collectors.groupingBy()`

Este método agrupa elementos de um fluxo de dados com base em uma chave ou atributo específico.

Por exemplo, agrupar os nomes dos funcionários com base no departamento:

```java
public class Funcionario {  
    String nome;  
    String departamento;  
  
    Funcionario(String nome, String departamento) {  
        this.nome = nome;  
        this.departamento = departamento;  
    }  
  
    public String getDepartamento() { return departamento; }  
    public String getNome() { return nome; }  
  
    @Override  
    public String toString() { return nome; }  
  
}
```

```java
import java.util.ArrayList;  
import java.util.Arrays;  
import java.util.List;  
import java.util.Map;  
import java.util.function.Function;  
import java.util.stream.Collectors;

public class Principal {  
    public static void main(String[] args) {  
        List<Funcionario> funcionarios = Arrays.asList(  
                new Funcionario("Ana", "TI"),  
                new Funcionario("Bruno", "RH"),  
                new Funcionario("Carlos", "TI"),  
                new Funcionario("Daniela", "RH")  
        );  
  
        Map<String, List<Funcionario>> porDepartamento = funcionarios.stream()  
                .collect(Collectors.groupingBy(Funcionario::getDepartamento));  
  
        System.out.println(porDepartamento);  
    }
}
```

O resultado será:

```
{TI=[Ana, Carlos], RH=[Bruno, Daniela]}
```

## Queue

Uma “Queue” pode ser usada para criar uma fila (FIFO), mas também pode implementar uma lista de prioridades, na qual os elementos são ordenados e consumidos segundo a prioridade e não na ordem de chegada. **Essa coleção admite a criação de outros tipos de filas com outras regras de ordenação.**

Exemplo:

```java
Queue<String> fila = new LinkedList<>();

// Adicionando elementos (no final da fila)
fila.add("Ana");
fila.add("Bruno");
fila.add("Carlos");

// Espiando o primeiro da fila (sem remover)
System.out.println("Próximo da fila: " + fila.peek());

// Removendo o primeiro elemento
System.out.println("Atendido: " + fila.poll());

// Fila restante
System.out.println("Fila atual: " + fila);
```

## Deque

Implementa a estrutura de dados conhecida como Deque (double ended queue). **Pode ser usada como uma fila (FIFO) ou uma pilha (LIFO).** Admite a inserção e a retirada em ambas as extremidades.

Exemplo:

```java
Deque<String> deque = new ArrayDeque<>();

// Adicionando elementos em ambas as pontas
deque.addLast("Elemento do Meio");  // Adiciona no fim
deque.addFirst("Primeiro Elemento"); // Adiciona no início
deque.addLast("Último Elemento");    // Adiciona no fim

System.out.println("Deque: " + deque); 
// Saída: [Primeiro Elemento, Elemento do Meio, Último Elemento]

// Removendo de ambas as pontas
System.out.println("Removido do início: " + deque.removeFirst()); // Primeiro Elemento
System.out.println("Removido do fim: " + deque.removeLast());    // Último Elemento

System.out.println("Deque final: " + deque);
```

## Papel da JDK, JRE e JVM

- **JVM:** executa os programas traduzindo o código.
- **JRE:** fornece o ambiente de execução com a JVM e bibliotecas.
- **JDK:** kit completo de desenvolvimento que inclui o JRE mais ferramentas de compilação.

# Herança em Java

## Por que Java não permite herança múltipla?

Por causa de uma falha de ambiguidade chamada de **diamante da morte**. 

Esse problema ser exemplificado assim: suponha que haja uma superclasse A e duas subclasses B e C, sendo que ambas implementam os mesmos métodos da superclasse A. Agora, imagine que uma classe D venha herdar tanto da subclasse B quanto da subclasse C. Quando a classe D for instanciada e chamar um método, o método de qual classe ela estará se referindo? B ou C. 

Exemplo em uma imagem:

![[Pasted image 20260828121139.png]]

## O que é aninhamento de classes?

O aninhamento de classes é a prática de declarar uma classe inteiramente dentro do escopo de outra classe ou interface. Exemplo:

```java
class Externa {  
   void getPosClasse () {
       System.out.println( "Externa" );
   }
    class Intermediaria {  
        void getPosClasse () {
            System.out.println( "Intermediaria" );
        }
        class Interna {  
            void getPosClasse () {
                System.out.println( "Interna" );
            }
        }
    }
}
public class Principal {
    public static void main ( String args [ ] ) {
        Externa.Intermediaria.Interna in = new Externa().new Intermediaria().new Interna();
        in.getPosClasse();
    }    
} 
```


> [!NOTE] Modificador de acesso em classes externas e internas
> Uma classe interna declarada como **protegida** pode ser acessada por uma classe em outro pacote que estenda a classe externa declarada publicamente.


> [!NOTE] Modificador de acesso aplicáveis
> Todos os modificadores de acesso são aplicáveis à classe mais externa do aninhamento.

## O que é o princípio da substituição?

Ele pode ser encontrado com diversos enunciados, sempre afirmando a substitutibilidade de um objeto da classe base pela classe derivada, sem prejuízo para o funcionamento do software. Podemos enunciá-lo da seguinte forma: seja um programa de computador P e os tipos B e D, tal que D deriva de B. Se D for subtipo de B, então qualquer que seja o objeto b do tipo B ele pode ser substituído por um objeto d do tipo D sem prejuízo para P.

## Qual a diferença entre subclasse e subtipo?

Uma subclasse é estabelecida quando uma classe é derivada de outra, mas um subtipo tem uma restrição adicional. Para que uma subclasse seja um subtipo da superclasse, todas as propriedades da superclasse devem ser válidas na subclasse. No caso dos subtipos, um tipo B é subtipo de um tipo A se um objeto do tipo B puder substituir perfeitamente um objeto do tipo A sem quebrar o sistema.

## Qual a diferença entre classe membro e classe aninhada?

Classe membro é aquela declarada dentro de outra classe. Por exemplo, uma classe Pessoa tem como um dos seus atributos um objeto do tipo Endereço. Neste caso, há uma **agregação**, ou seja, uma situação onde as classes são independentes; seria perfeitamente possível criar um objeto Endereço sem instanciar uma classe Pessoa.

No caso da classe aninhada, sua existência depende da classe que a engloba.

## Quais são os principais métodos do Collection?

| Método                         | Comportamento                                                              |
| ------------------------------ | -------------------------------------------------------------------------- |
| add(Object e)                  | Insere um elemento na coleção.                                             |
| addAll(Collection c)           | Adiciona os elementos de uma coleção em outra.                             |
| clear()                        | Limpa ou remove os elementos de uma coleção.                               |
| contains(Object c)             | Verifica se um dado elemento está presente na coleção.                     |
| containsAll(Collection c)      | Verifica se todos os elementos de uma coleção estão presentes em outra.    |
| equals(Object e)               | Verifica se dois objetos são iguais.                                       |
| hashCode()                     | Retorna o hash de uma coleção.                                             |
| isEmpty()                      | Retorna verdadeiro se a coleção estiver vazia.                             |
| Iterator()                     | Retorna um iterador.                                                       |
| remove(Object e)               | Remove um determinado elemento da coleção.                                 |
| removeAll(Collection c)        | Remove todos os elementos da coleção.                                      |
| retainAll(Collection c)        | Remove todos os elementos de uma coleção exceto os que correspondem a “c”. |
| size()                         | Retorna o número de elementos da coleção.                                  |
| toArray()                      | Retorna os elementos de uma coleção em um vetor.                           |
| Objetct [ ] toArray (Object e) | Retorna um vetor que contém todos os elementos da coleção que o invoca.    |
