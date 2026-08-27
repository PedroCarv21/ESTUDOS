
# O Ambiente Web Cliente X Servidor e as Tecnologias

## Diferença entre design adaptativo x design responsivo

- **Adaptativo:** usa uma única estrutura fluida que encolhe ou estica dinamicamente dependendo do tamanho da tela.
- **Responsivo:** detecta o aparelho e carrega um layout específico e predefinido para aquele dispositivo
## As tecnologias HTML

## O que é a tag `<meta name="viewport">`

Essa tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

É responsável por auxiliar na adaptação do conteúdo da página ao tamanho da tela do dispositivo.

# Linguagem de Marcação de Hypertexto - Html

## Definição de tipos de documento (DTD)

O objetivo do DTD é definir a estrutura e os elementos legais e atributos de um documento XML.

## Para que serve a declaração `DOCTYPE`?

Para que o documento seja renderizado no modo correto e que o navegador aplique as regras corretas na hora de analisar a marcação.

## Tags `<meta>`

Abarca um conjunto de informações chamadas de **metainformações**. Exemplo: descrição da página, palavras-chave etc.

## Diferença entre tag `section` e `article`?

- **`<article>`:** Inclui um bloco de conteúdo que deve ser usado quando se deseja inserir um artigo, como um post de um blog, por exemplo.
- **`<section>`:**  Define uma seção no documento. É normalmente utilizado para agrupar seções. Por exemplo: uma `<section>` poderia conter vários `<articles>`.
## Como são também chamados o símbolo da tag `<>`?

Colchetes angulares.
## O que são tags textuais?

Tags que definem a aparência e organização dos elementos de texto no momento da exibição do conteúdo. Exemplos: `<p>` (parágrafo), `<h1>` até `<h6>` (títulos e cabeçalhos), `<ul>` e `<li>` (listas).
## O que são tags semânticas?

São projetadas para dar significado e fornecer um contexto ao conteúdo.

## O que são tags de formatação?

Modificam o estilo visual do conteúdo. Exemplos:

- **`<strong>`:** deixa em negrito.
- **`<em>`:** deixa o texto em itálico.
- **`<s>`:** traça uma linha no meio do texto.
- **`<sub>`:** coloca o conteúdo abaixo dos outros conteúdos perto dele.
## Criação de lista de definição

- **`<dl>`** (_Description List_): É o container principal que guarda toda a lista de termos e conceitos.

- **`<dt>`** (_Description Term_): Define a palavra, o termo ou o título que vai receber uma explicação.

- **`<dd>`** (_Description Details_): Fornece os detalhes, o texto ou a definição que descreve o termo anterior.

Exemplo:

```html
<dl>
  <dt>HTML</dt>
  <dd>Linguagem de marcação usada para estruturar páginas web.</dd>
  
  <dt>CSS</dt>
  <dd>Linguagem de estilo usada para definir a aparência visual da página.</dd>
</dl>

```
## Criação de tabelas

Serão utilizadas as seguintes tags:

- **`<table>`:** representa o container principal da tabela.
- **`<thead>`:** representa o cabeçalho da tabela.
- **`<th>`:** representa as colunas que compõem o cabeçalho.
- **`<tr>`:** representa as linhas posteriores ao cabeçalho e anteriores ao rodapé.
- **`<td>`:** representa os itens posteriores ao cabeçalho.
- **`<tfoot>`:** representa o rodapé da tabela.

```html
<table>
    <thead>
        <th>Nome</th>
        <th>Email</th>
        <th>Senha</th>
    </thead>
    <tr>
        <td>Pedro</td>
        <td>pedro@gmail.com</td>
        <td>pedro123</td>
    </tr>
    <tr>
        <td>Maria</td>
        <td>maria@gmail.com</td>
        <td>maria123</td>
    </tr>
    <tfoot>
        <td>x</td>
        <td>y</td>
        <td>z</td>
    </tfoot>
</table>
```

**OBS.: coloque o atributo `border="1"` na tag `table` para criar bordas nas linhas e colunas da tabela.**
## Atributos `colspan` e `rowspan`

Os atributos `colspan` e `rowspan` servem para unir ou mesclar células em tabelas HTML O `colspan` une células na horizontal (colunas), enquanto o `rowspan` une células na vertical (linhas). 

Para isso, é necessário em um dos atributos um número que indicará a quantidade de linhas que irá ocupar. Exemplo:

```html
<table>
    <thead>
        <th>Nome</th>
        <th>Email</th>
        <th>Senha</th>
    </thead>
    <tr>
        <td>Pedro</td>
        <td>pedro@gmail.com</td>
        <td>pedro123</td>
    </tr>
    <tr>
        <td>Maria</td>
        <td>maria@gmail.com</td>
        <td>maria123</td>
    </tr>
    <tfoot>
        <td colspan="3">Rodapé</td>
    </tfoot>
```

Resultado:

![[Pasted image 20260820130158.png]]

## Tags para formulário

- `fieldset`: cria um contorno em volta dos campos do formulário.
- `legend`: adiciona um título no topo do `fieldset`.
- `select` e `option`: criam um campo de opções pré-definidas. Exemplo:
  
  ```csharp
	<label for="estado_civil">Estado Civil: </label>
	<select name="" id="estado_civil">
		<option value="">Solteiro</option>
		<option value="">Casado</option>
		<option value="">Divorciado</option>
		<option value="">Viuvo</option>
	</select>
  ```

- `textarea`: cria um campo para que possa incluir textos maiores (em vez de informações curtas). É possível limitar o número de linhas (com o atributo `rows`) e colunas (com o atributo `cols`).
## Atributos das tags presentes em um formulário

- `minlength` e `maxlength` da tag `input`: determina a quantidade de caracteres mínima e máxima.
- `type="reset"` do `submit`: limpa todos os campos do formulário que foram preenchidos. Ele só funciona caso o formulário esteja dentro de uma tag `form`.
- `type="submit"` do `submit`: envia os dados do formulário.
- `type="hidden"` do `input`: torna o campo de entrada oculto.
- `type="radio"` do `input`: cria um botão de opção. Caso queira que a seleção seja única, utilize o atributo `name` com o mesmo valor para todas as opções. Assim, o usuário só poderá escolher uma delas.
- `type="checkbox"` do `input`: cria uma caixa de opção. Neste caso, podem ser escolhidas múltiplas opções.
- `type="date"`: cria um campo para o preenchimento de uma data.

## Quais são os dois tipos de validação no HTML5?

- Verificação se o dado inserido está de acordo com o tipo/padrão. Exemplo é o Regex (expressão regular): refere-se ao uso de padrões de caracteres para validar campos de formulários diretamente no código HTML, utilizando o atributo pattern.
- Verificação se o campo obrigatório foi preenchido através do atributo `required`.

## Como desativar a funcionalidade de validação no formulário?

Adicionando o atributo `novalidate` na tag `form`.


