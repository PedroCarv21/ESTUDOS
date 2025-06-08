## 136. HTML do formulário

### Atributo autocomplete="off"

Utilize em um campo de entrada (ou no elemento `form` se for para todos os campos de entrada daquele formulário) para que não sejam feitas aquelas sugestões de preenchimento do campo. Exemplo de um formulário sem `autocomplete="off"`:

![[Pasted image 20250531185744.png]]

Agora com `autocomplete="off"`:

![[Pasted image 20250531185838.png]]

**OBS.: esse atributo nem sempre funciona.**
## 138. pseudo-classes :focus, :invalid e :valid

### :focus

Estabelece algumas estilizações quando um elemento é focado (ou selecionado) como, por exemplo, um elemento `input`:

```css
input:focus{
	background-color: red;
}
```

Ao pressionar o campo de entrada, o fundo dele ficará vermelho.

As próximas pseudo-classes são utilizadas em elementos que possuem o atributo booleano `required`.
### :invalid

Estabelece algumas estilizações quando as regras daquele elemento não são obedecidas. Exemplo:

```html
 <input id="email" class="dados_pessoais" type="email" required placeholder="Digite um email válido">
```

```css
input:invalid{

    border-bottom: 1px solid red;

}
```

Neste exemplo, o campo de entrada ficará com a borda inferior vermelha enquanto não fornecer um e-mail válido. Ou seja, a borda ficará vermelha já no momento em que a página irá carregar.
#### Combinação de pseudo-classes

É possível utilizar mais de uma pseudo-classe para um mesmo seletor, combinando assim as funcionalidades de cada uma. Por exemplo:

```css
input:focus:invalid{

    border-bottom: 1px solid red;

}
```

Este código informa que o campo de entrada só será considerado inválido ou não a partir do momento em que ele for 'focado' ou selecionado.

### :valid

Estabelece algumas estilizações quando as regras daquele elemento são obedecidas. 