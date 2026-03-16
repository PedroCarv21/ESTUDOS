
# Criação de um programa 'Olá Mundo' em C

Observe o seguinte código:

```c
#include <stdio.h>

int main(){
	printf("Olá, mundo!\n");
	return 0;
}
```

Estas são os significados de cada parte do código:

- `#include <stdio.h>:` importa as bibliotecas de entrada e saída de dados, necessário para o funcionamento da função `printf()`.
- `int main()`: é a função principal do programa, sendo esta executada primeira.
	- `return 0`: serve para indicar que o programa terminou de forma bem sucedida, ou seja, sem erros ou exceções.

# Variáveis string e char

Uma variável `char` é declarada no C da mesma forma que na linguagem Java:

```c
char letra = 'A';
```

No entanto, no caso de uma string, é necessário você estipular uma quantidade de caracteres que aquela variável provavelmente irá utilizar (não importa se a palavra não ocupar a quantidade máxima de caracteres):

```c
char nome[20] = "Pedro";
```

# Especificadores de formato

Os especificadores de formato na linguagem C são:

- **%d**: Imprime um inteiro.  
     
- **%i**: Equivalente a %d.  
     
- **%f**: Imprime um número de ponto flutuante no formato padrão.  Ex.: 340.00000
     
- **%e**: Imprime um número de ponto flutuante na notação científica.  Ex.: 340.00000+00
     
- **%c**: Imprime um único caractere.  
     
- **%s**: Imprime uma cadeia (string) de caracteres.

# Entrada de dados

A entrada de dados é feita através do comando `scanf`, sendo especificado qual o tipo e qual é a variável que receberá tal valor. Exemplo:

```c
scanf(" %s", &estado1);
```

> [!NOTE]
> As vezes, é bom dar um espaço antes do especificador de formato `" %s"` para que não haja problemas com a entrada de dados.

## Entrada de strings de múltiplas palavras

Quando vamos inserir uma string que é composta de várias palavras (ex.: "São Paulo", "José da Silva"), é necessário utilizar o seguintes comandos:

```c
getchar();
printf("Nome da cidade: ");
fgets(nomeDaCidade2, 50, stdin);
```

O `getchar()` é utilizado para **limpar o buffer (área de memória temporária onde os dados ficam guardados enquanto esperam para ser usados.)**. Suponha que, antes desse campo de entrada acima, haja outro campo de entrada:

```c
printf("Código: ");
scanf(" %s", &codigoDaCarta2);
```

Se a pessoa digitar `25` e aperter Enter (representado pelo `\n`), então o buffer ficará como `25\n`. O `scanf` consumirá o `25`, mas não o `\n`. Ele poderá ser consumido pelo `fgets` caso não haja o `getchar()`

Já a função `fgets()` consegue ler uma linha inteira (incluindo os espaços). Esta função recebe 3 parâmetros:
- A variável onde o valor será armazenado.
- número máx. de caracteres a serem lidos.
- `stdin` representa a entrada padrão (teclado).

# Solução estruturada

É um paradigma de programação que utiliza sequência, seleção e iteração como blocos fundamentais de código para criar algoritmos independentes da área de aplicação e da linguagem de programação utilizada.

Ela possui duas qualidades:

- **Modularidade:** técnica de dividir um sistema de software complexo em partes menores, independentes e gerenciáveis, facilitando a manutenção e reutilização de código Um exemplo são as funções.
- **Abstração:** permite você focar nos aspectos mais importantes de um problema, desconsiderando questões que são irrelevantes naquele momento. Mais uma vez, a função é um exemplo, pois um dos objetivos dela é fazer você focar apenas em *o que* ela pode fazer, e não em *como* ela pode fazer.

# O que é pseudocódigo?

forma genérica e estruturada de representar algoritmos usando linguagem natural (como português) misturada com elementos de programação.

![[Pasted image 20260302193028.png]]

Exemplos de linguagem que utiliza pseudocódigo é **portugol**.

# Conversão de tipos

As conversões podem ocorrer de duas formas:

## Implícita

É aquela conversão de tipos que não é 'forçada' pelo programador. Por exemplo:

```c
#include <stdio.h>

int main() {

  float n1 = 10;
  int n2 = 3;
  float resultado = n1 / n2;
  printf("\n%.2f", resultado);
  return 0;

}
```

## Explícita

É aquela conversão de tipos que é 'forçada' pelo programador através de um **casting**, onde é colocado o tipo desejado entre parênteses. Por exemplo:

```c
#include <stdio.h>
  
int main() {

  int n1 = 10;
  int n2 = 3;
  float resultado = (float) n1 / n2;
  printf("\n%.2f", resultado);
  return 0;

}
```

# Modificadores de tipos de dados

## unsigned

Em tese, esse comando serviria para tornar a quantidade de números inteiros maior, impossibilitando também a quantidade de números negativos. Veja a tabela para uma melhor compreensão:

| Tipo          | Intervalo de valores           |
| ------------- | ------------------------------ |
| int           | -2,147,483,648 a 2,147,483,647 |
| unsigned int  | 0 a 4,294,967,295              |
| char          | -128 a 127                     |
| unsigned char | 0 a 255                        |

> [!NOTE]
> Deve-se lembrar que os caracteres possuem um representante numérico na tabela ASCII.

## Comando long

Esse comando é utilizado para a quantidade de valores permitidas entre os tipos `int` e `double`.

| **Tipo**    | **Intervalo de valores**                               |
| ----------- | ------------------------------------------------------ |
| int         | -2,147,483,648 a 2,147,483,647                         |
| long int    | -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807 |
| double      | ±1.7E-308 a ±1.7E+308                                  |
| long double | ±3.4E-4932 a ±1.1E+4932                                |
No caso dos especificadores de formato para `long int` ou `long double`, utilize o `%ld` ou `%lf`. Caso não funcione, tente utilize o `%lld` ou `%llf` e utilize o `long long int` ou `long long double` como tipo da sua variável.