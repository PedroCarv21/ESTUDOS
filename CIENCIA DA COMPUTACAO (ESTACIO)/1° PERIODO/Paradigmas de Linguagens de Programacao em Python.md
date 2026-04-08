
# Paradigmas imperativos

- **Estruturado:** baseado na divisão do código em blocos lógicos, procedimentos ou funções, visando facilitar a legibilidade e manutenção. Desenvolve programas usando três tipos de estruturas (sequenciais, condicionais e repetição).
- **Orientado a objetos:** baseada na organização de código em "objetos" que modelam entidades do mundo real, unindo dados (atributos) e comportamentos (métodos).
- **Concorrente:** construção de programas de computador que fazem uso da execução simultânea de várias tarefas computacionais interativas. Em vez de um programa executar uma instrução após a outra em sequência, o paradigma concorrente permite que múltiplas partes do programa avancem simultaneamente, compartilhando recursos ou comunicando-se entre si.

# Paradigmas declarativos

- **Funcional:** operam tão somente funções que recebem um conjunto de valores e retornam um valor. O resultado que a função retorna é a solução do problema (foca o processo de resolução de problemas).
- **Lógico:** modelo de programação baseado na lógica formal, no qual o programa é descrito por fatos e regras, e a execução consiste em deduzir respostas para consultas.


# Como funciona o processo de tradução do código-fonte?

![[Pasted image 20260314185439.png]]

- **Compilador**: o compilador analisa o código-fonte e estando tudo OK, o converte para um código Assembly (da máquina hospedeira).  
- **Montador**: o montador traduz o código Assembly para o código de máquina intermediário (Código-objeto), que não é executável pelo computador. O código-objeto pode ser relocável, ou seja, carregado em qualquer posição de memória ou absoluto, carregado em um endereço de memória específico. A opção relocável é mais comum e mais vantajosa.  
- **Carregador**: o carregador é que torna o código-objeto em relocável.  
- **Ligador**: o Ligador liga (ou linka) o código-objeto relocável com as rotinas bibliotecas (outros objetos, rotinas do SO, DLLs etc.), usadas nos códigos-fontes. Essa ligação gera o código executável.

# Quais são os tipos de análise?

- **Sintética:** verificar a estrutura hierárquica e regras gramaticais.
- **Léxica:** Validar o sentido, coerência e significado.
- **Semântica:** Varre caractere por caractere, gerando tokens (palavras-chave, identificadores, símbolos) e classificando-os.

# Quais são as principais características da interpretação?

- Não traduz instruções que nunca são executadas.
- Consome menos memória.
- Execução mais lenta do que a compilação.

# O que é amarração (binding)

Associação entre entidade de programação, tais como:

- Variável amarrada a um valor.
- Operador amarrado a um símbolo.

# Como se chama o tempo em que a amarração ocorre?

Tempo de amarração.

# O que é amarração de tipo?

Vínculo entre a variável e o tipo. Esse vínculo pode ser:

- **Estático:** Ocorrem antes da execução e permanecem inalteradas.
- **Dinâmico:** Ocorrem durante a execução e podem ser alteradas.


# Relação de precedência entre operadores

![[Pasted image 20260326155528.png]]

# O que é a função `eval()`?

Função que recebe uma string como argumento, mas trata como uma expressão matemática que pode ser executada:

```python
print(eval('81 ** 0.5'))
# O resultado é 9.0
```

É possível também passar o `input()` como argumento desta função:

```python
resultado = eval(input("Digite uma expressão matemática: "))
```

# Métodos usados para lista:

- **append()**: adiciona um elemento ou uma lista dentro de outra lista. Exemplo: 

```python
lista = [1, 2, 3]
lista.append([4, 5])
# Resultado: [1, 2, 3, [4, 5]]
```

- **extend()**: extende a lista, seja com um novo elemento ou uma nova lista. Exemplo:

```python
lista = [1, 2, 3]
lista.extend([4, 5])
# Resultado: [1, 2, 3, 4, 5]
```

- **pop()**: informa o índice do elemento que se deseja excluir e retorna o valor excluído.
- **remove()**: informa o valor do elemento que se deseja excluir para excluí-lo.
- **insert()**: adiciona um novo elemento em posicionamento específico na lista, sendo o primeiro parâmetro o índice e o segundo parâmetro o valor que será inserido.
- **sort()**: ordena a lista.
- **del lista[0]**: desta forma, apaga um elemento específico da lista.
- **clear()**: apaga a lista.

# Métodos do dicionário:

- **values()**: retorna só os valores do dicionário.
- **keys()**:  retorna só as chaves do dicionário.
- **items()**: retorna uma lista e cada elemento é uma tupla contendo o par chave valor. Exemplo:

```python
pessoa = {
    "nome": "Pedro",
    "idade": 23,
    "nacionalidade": "Brasileiro"
    }
    
print(pessoa.items())
# dict_items([('nome', 'Pedro'), ('idade', 23), ('nacionalidade', 'Brasileiro')])

for chave, valor in pessoa.items():
	print(f"{chave} = {valor}")
'''
nome = Pedro
idade = 23
nacionalidade = Brasileiro
'''
```

- **clear()**: apaga o dicionário.

# O que é um subprograma em Python?

Nada mais que uma função.