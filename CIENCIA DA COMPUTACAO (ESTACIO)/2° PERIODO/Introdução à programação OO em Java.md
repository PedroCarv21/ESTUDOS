
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