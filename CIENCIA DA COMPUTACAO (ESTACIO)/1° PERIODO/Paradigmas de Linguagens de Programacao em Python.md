
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

# O que é a agregação e composição?

Agregação e composição são formas de associação entre classes (relações "tem-um" ou "has-a") na Programação Orientada a Objetos em Python. A principal diferença é o ciclo de vida: na agregação, objetos partes podem existir sem o todo (ex: professor/escola); na composição, a parte morre com o todo (ex: casa/cômodos).

# Como criar um atributo privado na classe?

Utilize dois underlines antes do nome do atributo:

```python
class Conta:
    def __init__(self, nome, saldo):
        self.__nome = nome
        self.__saldo = saldo
```

É importante lembrar que o python **não tem realmente um mecanismo de privar os atributos**. Se fosse executado o seguinte comando, seria possível acessar o valor do atributo:

```python
conta = Conta('Pedro', 500.0)
print(conta._Conta__saldo)
```

**OBS.: existe também o costume de colocar um único underline antes do atributo, indicando apenas formalmente que tal atributo não deveria ser acessado diretamente, embora nada impeça o acesso dele.**

**OBS.1: é possível também tornar os métodos privados com `__`.**
# Decorators `@property` e `@setter`

Transforma um método em um atributo, permitindo acessar um método sem o uso de parênteses:

```python
class Conta:
    def __init__(self, nome, saldo):
        self.__nome = nome
        self.__saldo = saldo
    @property
    def saldo(self):
        return self.__saldo

conta = Conta('Pedro', 500.0)
print(conta.saldo)
```

Já o `@setter` permite impor uma validação neste atributo. É necessário informar o nome do método com `@property` mais `.setter`. Exemplo:

```python
@saldo.setter
def saldo(self, novo_valor):
	if novo_valor > 0.0:
		self.__saldo = novo_valor
```

É possível acessar o método da seguinte forma:

```python
conta = Conta('Pedro', 500.0)
conta.saldo = -800
print(conta.saldo)
```

# Operators `classmethod` e `@staticmethod`

Permite um método ser acessado sem a instância da classe:

```python
@classmethod
def info(cls):
	return "Informação sobre a classe."
```

O acesso seria feito desta forma:

```python
print(Conta.info())
```

É possível criar um objeto da seguinte forma:

```python
class Conta:
    def __init__(self, nome, saldo):
        self.__nome = nome
        self.__saldo = saldo

    @property
    def saldo(self):
        return self.__saldo

    @saldo.setter
    def saldo(self, novo_valor):
        if novo_valor > 0.0:
            self.__saldo = novo_valor

    @classmethod
    def info(cls, valor):
        return cls("Anonimo", valor)
    
c = Conta.info(800)
print(c._Conta__saldo)
```

Já o `@staticmethod` não recebe nem `self` nem `cls`. Ele é basicamente uma função comum.

```python
@staticmethod
def e_par(num):
	return num % 2 == 0
```

# Como criar uma herança entre uma classe?

Considere:

- Colocar o nome da superclasse entre parênteses e depois do nome da subclasse. Exemplo: `ContaPremium(ContaNormal)`.
- Colocar o `super().__init__` dentro do método construtor da subclasse para chamar o método construtor da subclasse.

```python
class ContaNormal:
    def __init__(self, nome, email):
        self.nome = nome
        self.email = email
    @staticmethod
    def e_par(num):
        return num % 2 == 0

class ContaPremium(ContaNormal):
    def __init__(self, nome, email, saldo):
        super().__init__(nome, email)
        self.saldo = saldo

cp = ContaPremium('Pedro', 'pedro@gmail.com', 1500.0)
print(ContaPremium.e_par(cp.saldo))
```

É possível também fazer herança múltipla, ou seja, uma classe herda de mais de uma classe:

```python
from Conta import Conta
from Poupanca import Poupanca
  
class ContaRemuneradaPoupanca(Conta, Poupanca):
    def __init__(self, taxa_remuneracao, clientes, numero, saldo):
        Conta.__init__(self, clientes, numero, saldo)
        Poupanca.__init__(self, taxa_remuneracao)
```

**OBS.: desta vez, não é chamado o `super()`, mas o próprio nome de cada uma das superclasses.**

# Como criar uma classe abstrata?

Faça com que uma classe herde da classe `ABC` (Abstract Base Classes).

```python
from abc import ABC
class ContaCliente(ABC):
```

Ao criar o método abstrato dentro da classe, coloque a anotação `@abstractmethod`:

```python
from abc import ABC, abstractmethod

class ContaCliente(ABC):
    def __init__(self, numero, IOF, IR, valor_investido, taxa_rendimento):
        self.numero = numero
        self.IOF = IOF
        self.IR = IR
        self.valor_investido = valor_investido
        self.taxa_rendimento = taxa_rendimento

    @abstractmethod
    def calculo_rendimento(self):
        pass
```

Na hora que uma classe comum herdar de uma classe abstrata, é necessário também implementar o método abstrato na classe comum, mesmo que não seja definido o corpo:

```python
from abc import ABC, abstractmethod

class ContaCliente(ABC):
    def __init__(self, numero, IOF, IR, valor_investido, taxa_rendimento):
        self.numero = numero
        self.IOF = IOF
        self.IR = IR
        self.valor_investido = valor_investido
        self.taxa_rendimento = taxa_rendimento

    @abstractmethod
    def calculo_rendimento(self):
        pass
```

# Como criar exceções personalizadas?

Para criar uma exceção personalizada, utilizamos a herança da classe `Exception`:

```python
class ExcecaoCustomizada(Exception):
    pass 
```

Uma vez que uma exceção personalizada tenha sido criada, ela pode ser lançada em situações específicas, usando a instrução raise. Considere o exemplo abaixo, onde um método lança a exceção ExcecaoCustomizada caso o valor passado seja negativo:

```python
def checa_valor(valor):
    if valor < 0:
        raise ExcecaoCustomizada("Valor não pode ser negativo!")
```
# O que é um subprograma em Python?

Nada mais que uma função.

# Bibliotecas

## math

Operações matemáticas

- `sqrt()`: calcula a raiz quadrada.
- `ceil(x)`: Menor inteiro maior ou igual a x.
- `floor(x)`: Maior inteiro menor ou igual a x.

**OBS.: a biblioteca math não permite operações com números complexos.**
## random

Geração de números aleatórios
## smtplib

Envio de e-mails.
## time

Implementação de contadores temporais.

- `time()`: retorna a data e o tempo atual convertidos em segundos.
- `localtime()`: retorna um objeto com os valores da data e hora. Exemplo: `time.struct_time(tm_year=2026, tm_mon=4, tm_mday=9, tm_hour=18, tm_min=12, tm_sec=41, tm_wday=3, tm_yday=99, tm_isdst=0)`
- `ctime()`: recebe como argumento um valor gerado pelo `time()` e converte para uma string com as informações de data e hora. Exemplo: `Thu Apr  9 18:13:21 2026`
## tkinter

Criação de interface gráfica. A importação deve ser feito da seguinte forma: `from tkinter import *`

- `Tk()`: cria um objeto tkinter. Exemplo: `janela = Tk()`
- `texto = Label(master=janela, text="Hello World")`: o parâmetro `master` recebe um objeto tkinter e o texto recebe uma string que informa qual será a mensagem que deve aparecer na janela.
- `title()`: colocar um título na janela.
- `texto.place(x=30, y=100)`: define a posição do texto, seguindo a lógica do plano cartesiano.
- `btn = Button(master=janela, text="Clique", command=imprimirMsg)`: cria um botão na janela. O parâmetro `command` recebe uma função.
- `texto.pack()` ou `btn.pack()`: coloca o elemento centralizado e posicionado o mais perto possível do topo, depois dos elementos posicionados anteriormente.
- `janela.mainloop()`: mantem a janela constantemente aberta até o momento em que o usuário decidir fechar.
- `grid(row=0, column=0, padx=10, pady=5, sticky="e")`: os parâmetros `padx` e `pady` definem o espaçamento ao redor do elemento. Há também o parâmetro `columnspan` que permite o elemento ocupar mais de uma coluna. O `sticky` define o alinhamento dentro da célula:
	- `"n"` → cima (north)
	- `"s"` → baixo (south)
	- `"e"` → direita (east)
	- `"w"` → esquerda (west)
- `Entry()`: cria um campo de entrada. Ele possui um método `get()` para capturar o valor digitado.
- `messagebox.showinfo()`: cria um pop-up, recebendo como o primeiro argumento o título da janela e como segundo argumento uma mensagem.
-  `messagebox.showerror()`: criar um pop-up que devem apresentar mensagens de erro.
- `janela.bind('<Motion>', funcao_qualquer())`: utilizado para executar a função passada como argumento assim que o usuário mexe o mouse em cima da janela principal. Além do `"<Motion>"`, é possível utilizar o `"<Button-1>"` (quando o botão esquerdo mouse é clicado) e o `"<Button-3>"` (quando o botão direito do mouse é clicado)

# Exceções

| Exceção           | Explicação                                                                                      |
| ----------------- | ----------------------------------------------------------------------------------------------- |
| KeyboardInterrupt | Levantado quando o usuário pressiona CTRL+C, a combinação de interrupção.                       |
| OverflowError     | Levantado quando uma expressão de ponto flutuante é avaliada como um valor muito grande.        |
| ZeroDivisionError | Levantado quando se tenta dividir por 0.                                                        |
| IOError           | Levantado quando uma operação de entrada/saída falha por um motivo relacionado a isso.          |
| IndexError        | Levantado quando um índice sequencial está fora do intervalo de índices válidos.                |
| NameError         | Levantado quando se tenta avaliar um identificador (nome) não atribuído.                        |
| TypeError         | Levantado quando uma operação da função é aplicada a um objeto do tipo errado.                  |
| ValueError        | Levantado quando a operação ou função tem um argumento com o tipo correto, mas valor incorreto. |

