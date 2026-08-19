
# O que é?

É um cálculo matemático para determinar a capacidade de execução e o espaço requerido (memória) na medida que o volume de dados de entrada vai crescendo. Pode-se pensar em uma **notação como uma função.**

As principais notações de Big O são:

- **O(1) ou constante:** algoritmos que mantém o mesmo tempo de resposta, independente da quantidade de dados de entrada. 
- **O(log n) ou logaritmo:** o crescimento da quantidade de operações é inferior ao volume de dados de entrada. Exemplo é o caso da busca binária: se houver uma lista ordenada de 15 números (de 1 até 15) e preciso encontrar o número 3, eu irei capturar o número do meio (8). Caso não encontre de primeira precisaria dividir a lista novamente até encontrar. Porém, na maioria dos casos seria bem mais rápido ir consultando cada um dos números.
- **O(n) ou linear:** algoritmo cuja a quantidade de operações realizadas aumenta conforme o volume de dados de entrada.
- **O(n log n) ou complexidade loglinear:** significa que o algoritmo executa um trabalho **linear** (_n_) e, para cada parte desse trabalho, há um fator **logarítmico** (_log n_), ou vice-versa. Exemplo é o **Merge Sort** divide uma lista repetidamente em partes menores (log n) até que cada parte contenha apenas um elemento. Em seguida, ele intercala essas partes de forma ordenada O(n), formando sublistas cada vez maiores, até reconstruir a lista original completamente ordenada.
- ![[Pasted image 20260709093223.png]]
- **O(n^2) ou quadrática:** quando a operações realizadas aumentam *quadraticamente* (ou elevado a 2) em relação ao volume de dados de entrada. Um exemplo é o o loop aninhado.
- **O(2^n) ou exponencial:** significa que a cada novo dado adicionado, o o número de operações do programa dobra. Um exemplo é uma função de **fibonacci**:
  
  ```java
  int fibonacci(int n) {
    if (n <= 1)
        return n;

    return fibonacci(n - 1) + fibonacci(n - 2);
}
  ```
- **O(n!) ou fatorial:** aparece quando um algoritmo precisa testar todas as possíveis ordens dos elementos. Exemplo: descobrir todas as formas possíveis de colocar 3 pessoas em uma fila. O resultado é 3! = 3.2.1 = 6.
![[Pasted image 20260708193108.png]]

# Como calcular a complexidade de um código?

Os três passos para calcular a complexidade são:

1. Levar em consideração os loops de repetição do código.
2. Verificar a complexidade das funções/métodos do linguagem. Por exemplo: a complexidade do método `size()` é O(1) ou constante.
3. Ignorar as constantes (O(1)) e utilizar o termo de maior grau ou a de maior quantidade de operações realizadas.

Exemplo:

```cpp

int exemplo3(vector<int> v){
	int tamanho = v.size();
	int bla = 0;
	for (int i = 0; i < tamanho; i++){ // O(n)
		for (int j = 0; j < tamanho; j++){ //O (n)
			if (v[i] == v[j]) bla++; // O(1)
		}
	}
	
	// O(n) * O(n) + O(1) = O(n²)
	
	int ble = 0;
	for (int i = 0; i<tamanho; i++){ // O(n)
		if (v[i] == 10){
			ble = 2*ble;
		}
	}
	
	int bli = 0;
	for (int i = 0; i<tamanho; i++){ // O(n)
		if (v[i] == 5){
			ble += 5;
		}
	}
	
	return bla+ble+bli;
}

// O(n²) + O(n) + O(n) = O(n²) + 2.O(n)
```

Analisando cada uma das partes do código você tem:

- `size()`: constante.
- Loops aninhados: cada loop vai percorrer elemento por elemento do array. Então cada loop desse sozinho tem uma complexidade O(n). Como são loops aninhados então a complexidade é O(n) * O(n) ou O(n * 2).

Há então: 
- Uma constante (complexidade O(1))
- Um loop aninhado (O(n * 2))
- Dois loops simples (complexidade de O(n) + O(n)). A razão de haver uma adição e não uma subtração é porque um loop não está encadeado em outro loop, portanto, é preciso realizar uma soma apenas.

O resultado seria então: O(1) + O(n * 2) + O(n) + O(n) ou O(1) + O(n * 2) + 2O(n). Como o 3° passo é ignorar constantes (o O(1) e 2 de 2O(n)) e utilizar o termo de maior grau então o resultado é O(n * 2).

Exemplo 2:

```cpp
bool exemplo4(vector<int> v, vector<int> w){
	int tamanho = v.size();
	int tamanho2 = w.size();
	for (int i = 0; i < tamanho; i++){
		for (int j = 0; j < tamanho2; j++){
			if (v[i] == v[j]){
				return true;
			}
		}
	}
	return false;
}
```

Neste caso em especial, o tamanho do vetor v **independe** do tamanho do vetor w. Portanto, não é correto dizer O(n * 2) ou O(n) * O(n), mas sim O(n) * O(m). Resultado: O(n) * O(m)

## Exercícios

```java
int soma = 0;

for (int i = 0; i < n; i++) { // O(n)
    soma += i;
}
```


```java
for (int i = 0; i < n; i++) { // O(n)
    for (int j = 0; j < n; j++) { // O(n)
        System.out.println(i + " " + j); //O(1)
    }
}

// Resultado = O(n^2)
```


```java
for (int i = 0; i < n; i++) { // O(n)
    for (int j = 1; j < n; j *= 2) { //O(log n)
        System.out.println(i + j); // O(1)
    }
}

// Resultado: O(n log n)
```


```java
for (int i = n; i > 1; i /= 2) { // O(log n)
    System.out.println(i);
}

// Resultado: O(log n)
```


```java
for (int i = 0; i < n; i++) { // O(n)
    for (int j = i; j < n; j++) { //O(n)
        System.out.println(i + j);
    }
}

// Resultado: O(n log n)
```

## 7

```java
for (int i = 1; i < n; i *= 2) { // O(log n)
    for (int j = 1; j < n; j *= 2) { // O(log n)
        System.out.println(i + j);
    }
}

//Resultado: O((log n)²) ou O(log² n)
```


## 8

```java
for (int i = 0; i < n; i++) { // O(n)

    for (int j = 1; j < n; j *= 2) { // O(log n)

        for (int k = 0; k < n; k++) { // O(n)

            System.out.println(i + j + k);

        }
    }

}
/**
O(n) * O(n) * O(log n)
O(n^2) * O(log n)
O(n^2 log n)
**/
```

# Complexidade dos métodos das principais estrutura de dados

## Array (t[])

| Operação                       |   Complexidade |
| ------------------------------ | -------------: |
| Acesso por índice              |       **O(1)** |
| Alterar elemento               |       **O(1)** |
| Busca                          |       **O(n)** |
| Inserção no final (com espaço) |       **O(1)** |
| Inserção no meio               |       **O(n)** |
| Remoção                        |       **O(n)** |
| Método `length()`              |       **O(1)** |
| Arrays.sort()                  | **O(n log n)** |
## ArrayList

| Método              |        Complexidade |
| ------------------- | ------------------: |
| get(index)          |            **O(1)** |
| set(index, value)   |            **O(1)** |
| add(element)        | **O(1)** amortizado |
| add(index, element) |            **O(n)** |
| remove(index)       |            **O(n)** |
| remove(object)      |            **O(n)** |
| contains()          |            **O(n)** |
| indexOf()           |            **O(n)** |
| size()              |            **O(1)** |
| clear()             |            **O(n)** |
| sort()              |            **O(n)** |


## LinkedList

| Método        | Complexidade |
| ------------- | -----------: |
| get(index)    |     **O(n)** |
| set(index)    |     **O(n)** |
| addFirst()    |     **O(1)** |
| addLast()     |     **O(1)** |
| removeFirst() |     **O(1)** |
| removeLast()  |     **O(1)** |
| add(index)    |     **O(n)** |
| remove(index) |     **O(n)** |
| contains()    |     **O(n)** |
| size()        |     **O(1)** |
| sort()        |     **O(n)** |

## HashSet

| Método     | Complexidade média |
| ---------- | -----------------: |
| add()      |           **O(1)** |
| remove()   |           **O(1)** |
| contains() |           **O(1)** |
| size()     |           **O(1)** |
| clear()    |           **O(n)** |
## TreeSet

|Método|Complexidade|
|---|--:|
|add()|**O(log n)**|
|remove()|**O(log n)**|
|contains()|**O(log n)**|
|first()|**O(log n)**|
|last()|**O(log n)**|
## HashMap

|Método|Complexidade média|
|---|--:|
|put()|**O(1)**|
|get()|**O(1)**|
|remove()|**O(1)**|
|containsKey()|**O(1)**|
|containsValue()|**O(n)**|
|size()|**O(1)**|
|clear()|**O(n)**|
## TreeMap

|Método|Complexidade|
|---|--:|
|put()|**O(log n)**|
|get()|**O(log n)**|
|remove()|**O(log n)**|
|containsKey()|**O(log n)**|
|firstKey()|**O(log n)**|
|lastKey()|**O(log n)**|
