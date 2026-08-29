# 14. Medindo Cobertura com Fine Code Coverage

## O que é Fine Code Coverage?

É uma ferramenta que serve para visualizar de forma clara e visual a cobertura de testes, ou seja, quanto do seu código-fonte foi testado.
## Como instalar?

`Extensions` → `Manage Extensions` → vá na aba `Browse` e pesquise por `fine code coverage`. Será necessário fechar e abrir o microsoft visual studio.
## Como usar?

Depois de rodar os testes, abra o code coverage em `View` → `Other Windows` → `Fine Code Coverage`. Deverá ser aberto uma janela como esta:

![[Pasted image 20260829130554.png]]

É apresentado o percentual de cobertura que cada classe tem. Para saber quais partes da classe ainda não foram cobertas clique em uma delas (ex.: `Demo.Calculadora.ClienteService`) → `Tools` → `FCC Toggle Indicators`. Aparecerá colunas na lateral esquerda, sendo que as partes da classe que foram cobertas estarão com a coluna azul e aquelas que não foram estarão com coluna branca.

Caso queira que a cobertura do código desconsidere uma classe, coloque `[ExcludeFromCodeCoverage]` em cima do nome da classe.