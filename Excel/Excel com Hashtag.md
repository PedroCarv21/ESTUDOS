# Validação de dados

Estabelece uma quantidade limitada de valores que irão preencher uma determinada coluna. Por exemplo: determinar que a coluna sexo será ou masculino ou feminino.

Para isso, selecione a coluna desejada → clique na guia de **Dados** → vá até o grupo **Ferramentas de dados** e procure por **Validação de dados**. Será aberto esta janela:

![[Pasted image 20260728155431.png]]

No campo de **Permitir**, escolha a opção **Lista** → vá até a aba **Alerta de erro** e defina um Título e a mensagem de erro caso alguém escolha um valor incorreto → Clique em **Ok**.

![[Pasted image 20260728155609.png]]

Agora haverá uma seta ao lado da cédula para escolher uma das opções:

![[Pasted image 20260728155908.png]]

# Como gerar valores aleatórios

Digite `=ALEATÓRIOENTRE()` e coloque dois valores separados por ponto e vírgula. Exemplo: `=ALEATÓRIOENTRE(0;100)`. Para preencher o restante das linhas, dê um duplo clique na borda inferior direita.

# Pincel para copiar e colar formatação 

Selecione a(s) cédula(s) com a formatação desejada → vá na guia **Página Inicial** e clique no **Pincel de Formatação** → Clique na(s) cédula(s) que irão receber a formatação.

# Fixar a linha superior

Vá até a guia de **Exibir** → Clique em **Congelar Painéis** → **Congelar Linha Superior**.

# Formatação Adicional

## Colorir um percentual da cédula de acordo com o valor da cédula

Guia **Página Inicial** → **Formatação Condicional** → **Barra de Dados** → escolha uma cor. O resultado será este.

![[Pasted image 20260728182910.png]]

## Colorir cédulas específicas de acordo com conteúdo

Guia **Página Inicial** → **Formatação Condicional** → **Regras de Realce das Células** → **Texto que Contém...** → informe o conteúdo da cédula que será destacado e com qual cor.

![[Pasted image 20260728183800.png]]

O resultado:

![[Pasted image 20260728183827.png]]

Se outro registro tiver o cargo alterado para 'Diretor', esse registro terá o cargo destacado em vermelho automaticamente.
# Filtros

Selecione a parte superior da tabela → Vá até a guia **Dados** → **Filtro**. A partir disso, você pode escolher uma das colunas e clicar na seta que aparece no canto inferior direito e filtrar de acordo com os valores de cada coluna. Por exemplo: filtrar a coluna Salário, ordenando os valores do maior para o menor.

![[Pasted image 20260728174833.png]]


# Funções

- `=SOMA()` → soma todos os valores das cédulas selecionadas dentro da função. Exemplo: `=SOMA(C2:C7)`. O `:` indica de um valor até outro, ou seja, da cédula C2 até C7.
- `=MULT()` → multiplica todos os valores das cédulas selecionadas dentro da função.
- `=MÉDIA()` → calcula a média de todos os valores das cédulas selecionadas dentro da função.
- `=MÁXIMO()` → informa o valor máximo dentro os números selecionados.
- `=MÍNIMO()` → informa o valor mínimo dentro os números selecionados.
- `=MAIOR()` → define um conjunto de valores e estabelece qual dos maiores valores deseja-se buscar. Por exemplo: buscar o segundo maior valor entre o conjunto de números que vai de C1 até C6. Portanto, a fórmula deve ser: `=MAIOR(C1:C6;2)`.
- `MENOR()` → define um conjunto de valores e estabelece qual dos menores valores deseja-se buscar.
- `CONT.VALORES()` → conta a quantidade de todos os valores selecionados.
- `CONT.NÚM()` → conta apenas a quantidade de números selecionados.
- Auto soma (Σ) → selecione as cédulas que serão somadas → vá até a **Página Inicial** → grupo **Edição** → escolha a opção **Soma**.
- Média → selecione as cédulas que serão somadas → vá até a **Página Inicial** → grupo **Edição** → escolha a opção **Média**.
- Contar Números → selecione as cédulas que serão somadas → vá até a **Página Inicial** → grupo **Edição** → escolha a opção **Contar Números**.
# Como criar tabelas dinâmicas

- Selecione todas cédulas preenchidas do Excel com **Ctrl+T**. Neste foi utilizado uma tabela já pronta com as seguintes colunas: Nome do Produto, Data da Venda, Nome, DDD, Telefone, Tipo de Pagamento e Preço Total.
- Vá na guia **Inserir** e clique em **Tabelas Dinâmicas Recomendadas**.
- Selecione a opção **Nova Planilha** e clique em **Ok**.

O resultado deve abrir uma nova planilha (ou guia) como esta:

![[Pasted image 20260728101353.png]]

É possível arrastar as colunas da tabela inicial para as seguintes áreas: **Filtros, Colunas, Linhas e Valores**. Exemplo: se eu arrastar a coluna 'Tipo de Pagamento' (que possui apenas os valores 'Boleto Bancário' e 'Cartão de Crédito') para a área 'Coluna' e a coluna 'Nome do Produto' para a área de 'Linhas' e também para a área de 'Valores'. O resultado deve ser esse:

![[Pasted image 20260728102218.png]]

O resultado é a quantidade de vendas de cada produto divido pelos tipos de pagamento.
## Percentual

É possível também descobrir o percentual de cada produto em relação a quantidade total de produtos. Para isso, será necessário colocar a coluna 'Nome do Produto' tanto na área de 'Linhas' quanto na área de 'Valores'.

![[Pasted image 20260728103213.png]]

Selecione todos os valores → clique com botão direito → Opção 'Mostrar Valores Como' → '% do Total Geral'.

![[Pasted image 20260728103503.png]]

É possível diminuir o número de casas decimais: Selecione os dados de percentual → guia 'Página Inicial' → grupo 'Número' → 'Diminuir Casas Decimais'.

## Extraindo mês e ano de datas

- Mês: digite `=texto(` → selecione uma cédula correspondente a data → digite `; "MMM")`. Exemplo:

![[Pasted image 20260728114801.png]]

- Ano: é o mesmo processo que o mês, porém, em vez de "MMM", digite "AAAA".

Caso queira preencher todas as outras linhas posteriores com o valor do mês ou do ano, dê um duplo clique na borda inferior direita da cédula.
## Filtro

Arraste uma coluna para a área de Filtros e será assim possível determinar quais serão os dados visualizados na tabela de acordo com a seleção dos valores presentes na coluna colocada em Filtros. Exemplo da coluna 'Tipo de Pagamento' na área de Filtros:

![[Pasted image 20260728123813.png]]

Eu visualizar os dados da tabela tanto com base na opção 'Boleto Bancário' ou 'Cartão de Crédito' como também visualizar todos os dados presentes nessas duas opções.

## Outras opções de filtro

Selecione a tabela dinâmica → clique na guia 'Análise de Tabela Dinâmica' → 'Inserir Segmentação de Dados' → Selecione uma das colunas como filtro. Por exemplo: coluna ano para filtro:

![[Pasted image 20260728124355.png]]

## Gráfico

Depois de criar o filtro, você deve selecionar a tabela dinâmica → Inserir → vá ao grupo 'Gráficos' e clique em 'Inserir Gráficos de Colunas ou de Barras' e escolha um dos gráficos.

![[Pasted image 20260728125524.png]]

Na medida em que você muda o filtro, muda-se o gráfico de forma dinâmica.