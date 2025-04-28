
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

Para que um campo do formulário seja obrigatório, coloque o atributo booleano **required** e para que o campo já esteja selecionado ao carregar a página, adicione o atributo **autofocus**