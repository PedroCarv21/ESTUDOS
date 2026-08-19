# Comandos

## Typeof

Verifica o tipo da variável:

```javascript
let nome = 'Pedro'
let idade = 23;
let salario = 8800.56;

console.log(typeof nome); // string
console.log(typeof idade); // number
console.log(typeof salario); // number
```

## O que significa NaN (Not a Number)?

Quando você tenta realizar uma operação matemática envolvendo valores que não são números. Exemplo:

```javascript
let letra1 = 'a';
let letra2 = 'b';

console.log(letra1 - letra2); // O resultado é NaN
```

No entanto, se o conteúdo das strings for um número, o JavaScript consegue identificar isso e fazer o cálculo.

```javascript
let num1 = '3';
let num2 = '1';

console.log(num1 - num2); // O resultado é 2
```

## Como criar uma lista e consultar seus dados?

```javascript
let lista = [0, 1, 2, 3, 'teste']

for (let x = 0; x <= 4; x++){
    console.log(lista[x]);
}
```

Uma forma mais simples de listar os dados é com o método `map()`:

```js
lista.map((elemento) => {
    console.log(elemento)
});
```
## Método para adicionar elemento na lista

```js
lista.push('hello world');
```

## Método para deletar último elemento da lista

```js
let elementoExcluido = lista.pop();
console.log(elementoExcluido);
console.log(lista);
```

## Método para reverter a ordem dos elementos da lista

```js
lista.reverse();
```

## Método que verifica se o número existe na lista

```js
let lista = [6, 5, 10];
  
console.log(lista.includes(10)); // true
```

## O que acontece quando não é colocado `return` dentro da função?

Aparece um `undefined`.

```js
function imprimirDadosPessoais(nome, idade){
    console.log(`Seu nome é ${nome} e idade é ${idade}.`);
}

/*
O resultado será:
Seu nome é Pedro e idade é 23.
undefined
*/
console.log(imprimirDadosPessoais('Pedro', 23));
```

## O que é um objeto?

Um objeto é uma estrutura que permite armazenar dados em pares chave-valor.   

```js
let pessoa = {

    nome: 'Pedro',
    idade: 23,

    acordar(){
        return "Acordando";
    }
}
  
console.log(pessoa.nome);
console.log(pessoa.idade);
console.log(pessoa.acordar());
```
