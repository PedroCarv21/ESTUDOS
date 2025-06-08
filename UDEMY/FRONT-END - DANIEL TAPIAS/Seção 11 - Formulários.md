
## 122. Introdução
### Tag form

Irá conter todos as outras tags relacionadas a um formulário como: campo de entrada, checkbox, botão de enviar, entre outros.

Os principais atributos são:

- **action**: irá conter o link do documento que receberá os dados informados no formulário.
- **method**: define o método de envio. Os principais são:
	- **get**: os dados enviados ficarão visíveis na URL. Portanto utilize este método apenas quando se tratar dados em quantidade ínfima e que não sejam sigilosos.
	- **post**: os dados enviados não ficarão visíveis na URL.


Exemplo de código com a tag `form`:

```html
<form action="" method="get">

</form>
```
### Tag input

Esta tag é utilizada para criar diversos tipos de componentes presentes em um formulário como: campo de entrada, botão de enviar, checkbox, entre outras. Isto depende de qual será o valor passado para o atributo **type**. Os principais valores mostrados até agora são:

- **text**: cria um campo de entrada para receber texto. É o mais genérico de todos.
- **submit**: cria um botão de envio. Para que o botão receba algum título indiciando sua ação, use o atributo **value**.

Exemplo de código:

```html
<form action="" method="get">
  <input type="text"/>
  <input type="submit" value="OK"/>
</form>
```

### Enviando dados para o Google

Acompanhe os seguintes passos:

- Coloque o link https://www.google.com/search no atributo action da tag form.
- Passe o valor get no atributo method.
- Passe o valor "q" para o atributo **name** em uma tag input que represente um campo de entrada. O valor "q" está de acordo com o mecanismo de busca, portanto, este valor pode variar.

Exemplo:

```html
<form action="https://www.google.com/search" method="get">

  <input type="text" name="q"/>

  <input type="submit" value="OK"/>

</form>
```

### Tag label

A tag label permitirá criar um rótulo para um campo de entrada. Através do atributo **for** da tag label e do atributo id da tag input, será possível vicular ambos os elementos com base em um valor comum. Isso significa que toda vez que a tag label for clicada, o campo de entrada será selecionado. Exemplo:

```html
<label for="texto">Texto: </label>
<input id="texto" type="text" name="q"/>
```


## 123. Semântica em forms

### Tags fieldset e legend

A tag **fieldset** é utilizada para agrupar um conjunto de elementos por meio de uma linha envolta aos elementos. A tag **legend** irá dizer do que se trata aquele conjunto de elementos. Exemplo:

```html
 <form action="">

  <fieldset>

	<legend>Login</legend>

	<label for="email">Email: </label>

	<input id="email" type="text"><br><br>

	<label for="senha">Senha: </label>

	<input id="senha" type="password"><br><br>

	<input type="button" value="Enviar">

  </fieldset>

</form>
```

O resultado é este:

![[Pasted image 20250415153708.png]]

## 123. Semântica em forms - mão na massa

### Campo de entrada para senhas

Coloque o valor 'password' para o atributo type no elemento input. Isso fará com que os caracteres digitados no campo sejam substituídos por asteriscos de modo ocultar o que alguém está escrevendo.

### Campo obrigatório e selecionado

Para que um campo do formulário seja obrigatório, coloque o atributo booleano **required** e para que o campo já esteja selecionado ao carregar a página, adicione o atributo booleano **autofocus**


## 127. Botões lado a lado

### Tipo reset

Este tipo é especificado em um elemento input e gera um botão com a funcionalidade de apagar tudo aquilo que havia sido nos campos de entrada. Exemplo:

```html
<input type="reset" value="Apagar" class="btn btn_limpar">
```

## 128. Tipos de entrada de dados - parte 1

Estes são os principais valores passados para o atributo type do elemento input.
### Tipo email

Responsável por validar se o valor recebido em um campo de entrada deste tipo é ou não um e-mail válido. Exemplo:

```html
<form>

      <fieldset>

        <legend>Cadastro</legend>

        <input type="email" required>

        <input type="submit" value="enviar">

      </fieldset>

</form>
```

Ao clicar no botão de enviar, o campo de entrada e-mail irá expor uma mensagem de erro caso o valor esteja incorreto.

Se não houver o atributo booleano required então será possível enviar este campo de entrada como vazio.

**OBS.: dependendo de cada celular, ao usar este tipo de atributo é possível gerar algumas mudanças no teclado do dispositivo:**

![[Pasted image 20250429105314.png]]

### Tipo number

Recebe apenas valores numéricos e, por meio dos atributos **min** e **max**, é possível estabelecer um limite para o valor mínimo e o valor máximo.

```html
<input type="number" min="10" max="20" required>
```
### Tipo date

Cria um campo para inserção de datas, sendo também possível estabelecer uma data mínima e máxima através dos atributos min e max.

```html
<input type="date" min="2025-02-01" max="2025-04-29">
```

**OBS.: é necessário informar nos atributos min e max a data no formato americano, ou seja, ano-mês-dia.**
### Tipo radio

Cria um botão que permite o usuário escolher uma única opção. Para que isso seja realizado adequadamente, é necessário informar o mesmo valor no atributo name. No exemplo a seguir, o valor para name é 'sexo', ou seja, o usuário só poderá escolher uma das duas opções: masculino ou feminino. Exemplo:

```html
<input type="radio" name="sexo" id="masculino">

<label for="masculino">Masculino</label>

<input type="radio" name="sexo" id="feminino">

<label for="feminino">Feminino</label>
```

## 129. Tipos de entrada de dados - parte 2

### Tipo checkbox

Diferente do tipo `radio`, onde só é possível selecionar apenas uma única opção, o tipo `checkbox` permite a seleção de mais uma opção.

```html
<h2>Você tem experiências nas tecnologias: </h2>

<label>HTML/CSS: <input type="checkbox" name="tecnologia" value="html_css"></label>

<label>GIT/GITHUB: <input type="checkbox" name="tecnologia" value="git_github"></label><br>

<label>JAVA: <input type="checkbox" name="tecnologia" value="java"></label>

<label>SPRING BOOT: <input type="checkbox" name="tecnologia" value="spring_boot"></label>
```

### O uso do atributo name e value

O atributo `name` serve como uma espécie de identificador do elemento enquanto o atributo `value` informa qual o valor foi escolhido.

## 130. Tipos de entrada de dados - parte 3

Outra forma de criar opções que possam selecionadas por um usuário é através das tags:

- `select`: é o container que possui as opções contidas dentro dele e também é usado para definir certas configurações. Um exemplo é o atributo booleano `multiple` que permite selecionar mais de uma opção. Outro atributo é o `size` que define a quantidade de opções visíveis.
- `option`: é a tag que representará uma opção dentro de `select`. Caso o elemento `select` possua um atributo booleano `required` então só serão aceitas as opções selecionadas que possuírem algum valor no atributo `value`.
- `optgroup`: cria uma categoria para determinadas opções contidas dentro desta tag. No exemplo abaixo, as tag `option` com os valores Estagiario e Junior estão dentro da categoria Iniciante.

```html
<h2>Nível de senioridade:</h2>

        <select multiple size="7">

          <option value="">Nível</option>

          <optgroup label="Iniciante">

            <option value="Estagiario">Estagiario</option>

            <option value="Junior">Júnior</option>

          </optgroup>

          <optgroup label="Avançado">

            <option value="Pleno">Pleno</option>

            <option value="Senior">Senior</option>

          </optgroup>

        </select>
```

### Selecionando opções através de um campo de entrada

Se houver uma quantidade indefinida de opções, é recomendado utilizar as seguintes tags:

- `input`: é a por meio de um campo  de entrada que será escolhido uma determinada opção. A partir do momento em que for passadas as primeiras letras, já serão selecionadas algumas opções que contém estas letras e que você poderá escolher alguma delas. Para isso, é necessário passar o atributo `list` que possua o mesmo valor do `id` do elemento `datalist`.
- `datalist`: o elemento que irá conter dentro de si um conjunto de opções representadas pela tag `option`. Neste contexto, já não é necessário que `option` possua uma tag de fechamento.

```html
<input type="text" list="niveis">

<datalist id="niveis">

  <option value="Estagiario">

  <option value="Júnior">

  <option value="Pleno">

  <option value="Senior">

</datalist>
```

## 131. Tipos de entrada de dados - parte 4

### textarea

Este elemento é responsável por gerar um caixa de texto que pode ser expandida de maneira indefinida. O atributo `cols` limita a quantidade de colunas visíveis enquanto o atributo `rows` limita a quantidade de linhas visíveis.

```html
<textarea name="" cols="20" rows="5">

</textarea>
```

Há também o atributo `maxlength` que limita a quantidade de carácteres dentro de `textarea` e o atributo booleano `readonly` que torna a caixa de texto disponível apenas para leitura (não mais para a escrita).

**OBS.: `maxlength` e `readonly` também podem ser acrescentados em outros elementos.**

**OBS.: o atributo booleano `disabled` tem a mesma finalidade que `readonly`, porém deixa o elemento com uma aparência distinta.**
### Entrada de arquivos

Utilize o `<input type="file">` para fazer o upload de arquivos. Ele gera um botão que, ao clicar, permite você carregar e subir um arquivo na página.

![[Pasted image 20250515155750.png]]

### Outra forma de enviar o formulário

Além do elemento `input` do tipo `submit`, é possível também usar o elemento `button` da seguinte forma:

```html
<button type="submit">Enviar</button>
```

**OBS.: este botão, sem o `type="submit"`, pode ser também usado para outras finalidades além do envio de formulário, sendo isto feito geralmente com JavaScript.**

### Campo de entrada do tipo range

Observe o seguinte elemento:

```html
<input type="range" min="0" max="10" step="2">
```

O tipo `range` permite criar uma espécie de barra com intervalos determinados pelo atributo `step`.

![[Pasted image 20250515161355.png]]
### Entrada de dados sobre o tempo

Através do `<input type="time" name="" id="">` é possível informar o tempo da seguinte forma:

![[Pasted image 20250515160655.png]]

### Campo de entrada para cor

Elemento `input` com `type="color"` permite definir uma graduação de cor específica.

![[Pasted image 20250515161630.png]]

### Atributo booleano checked

Faz com que um elemento do tipo `checkbox` já esteja selecionado quando a página carregar.

### Atributo placeholder

Cria uma espécie de 'legenda' dentro de um campo de entrada, indicando o que deve ser inserido nele.

## 132. meter e progress

### Tag meter

Utilizada para medir algo e informar a sua condição com base numa cor (vermelho, amarelo ou verde) preenchida em uma barra. É bastante útil para indicar: o nível de bateria disponível, a quantidade de espaço já utilizada em um HD, entre outras. Exemplo:

![[Pasted image 20250520112119.png]]

Para criar esta barra preenchida desta forma e com esta cor foi necessário o seguinte elemento:

```html
<meter min="0" max="100" low="50" high="70" value="82" optimum="80"></meter>
```

Este é o conceito por trás de cada um dos atributos:

- `min`: informa o valor mínimo permitido.
- `max`: informa o valor máximo permitido.
- `low`: valor considerado baixo.
- `high`: valor considerado alto.
- `value`: valor atual.
- `optimum`: valor considerado ótimo.

**OBS.: se o valor de `optimum` for maior que o valor de `high` então a barra ficará: verde se `value` for maior ou igual a `high`, amarela se `value` for igual ou maior que `low` e vermelha se `value` estiver abaixo de `low`. O contrário acontece se `optimum` possuir um valor abaixo de `low`.**

### Tag progress

Indica uma barra de progresso, podendo ser utilizado em contextos como, por exemplo, o progresso de download de um arquivo. Este elemento possui os seguintes atributos:

- `max`: valor máximo.
- `value`: valor atual.

```html
<progress max="100" value="50"></progress>
```

Este é o resultado:

![[Pasted image 20250520113903.png]]

## 133. output

Elemento utilizado para representar a saída ou resultado de um cálculo. O correto é utilizar este elemento junto de comandos JavaScript. Exemplo:

```html
<form oninput="resultado.value=a.value*b.value">

	<input type="text" name="a"> X

	<input type="text" name="b"> =

	<output name="resultado"></output>

</form>
```

O atributo `oninput` permite inserir uma operação de cálculo, informando, neste caso, que a saída em `output` será o valor do campo de entrada com `name`  igual a `a` multiplicada pelo campo de entrada com `name` igual a `b`.

## 134. accent-color

Propriedade CSS utilizada para alterar a cor dos elementos de um formulário. Exemplo:

```css
input, progress{

    accent-color: red;

}
```

![[Pasted image 20250520121524.png]]

**OBS.: dependendo da cor escolhida, isso pode alterar outros aspectos do elemento. Exemplo: **

```css
input, progress{

    accent-color: orange;

}
```

![[Pasted image 20250520121324.png]]
