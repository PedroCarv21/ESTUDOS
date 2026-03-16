
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