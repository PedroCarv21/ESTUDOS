# 2. Padrões e nomenclaturas nos Testes Unitários

## Padrão AAA (Arrage, Action, Assert)

AAA é um padrão de organização dos testes divido em três passos:

- **Arrage:** preparar o ambiente de testes previamente para que possa ser executado as ações sem problemas.
- **Action:** representa a ação que o programador tem interesse em testá-la.
- **Assert:** é a parte onde é verificado se os resultados obtidos condizem com os resultados esperados.

## Nomenclatura usada nos métodos de testes

Pode ser escolhido um desses dois:

- **Padrão AAA:** NomeDoMetodoTestado_CondicaoEsperado_ResultadoObtido
- **Given_When_Then:** DadaSituacao_QuandoDeterminadasCondicoes_EntaoRetornaraIsso

