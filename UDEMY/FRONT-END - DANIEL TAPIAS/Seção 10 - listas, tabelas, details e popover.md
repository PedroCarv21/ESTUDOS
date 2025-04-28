
## 115. Listas aninhadas

Nada mais são do que listas dentro de listas. Exemplo:

```html
<ul>
    <li>Opção 1</li>
    <li>Opção 2
      <ul>
        <li>Opção 2.1</li>
        <li>Opção 2.2</li>
      </ul>
    </li>
    <li>Opção 3</li>
</ul>
```

O resultado será este:

![[Pasted image 20250317124935.png]]

## Listas de definição

O conjunto de tags  dl, dt e dd são utilizadas em contextos de dicionários ou glossários:

- dl:  representa uma lista de definição. É nesta tag onde ficarão armazenados as tags dt e dd.
- dt: representa o termo de definição.
- dd: representa os detalhes da descrição.

```html
    <dl>
      <dt>HTML</dt>
      <dd>Lingaugem de marcação</dd>
      <dt>Javascript</dt>
      <dd>Linguagem de programação que roda tanto no Front quanto no Back</dd>
    </dl>
```

## 117. Tabelas

Para a criação de tabelas, são necessárias as tags table, tr e td. A tag tr é responsável por criar linhas enquanto a tag td é responsável por criar colunas. A tag table irá conter este conjunto de linhas e colunas.

### Exemplo de uma lista telefônica

É formada por duas colunas e 4 linhas. A primeira coluna é reservada aos nomes e a segunda aos números de telefone. A primeira linha possui a descrição de cada coluna e as demais contém os dados. Este é o código HTML

```html
<table>
  <tr>
    <td>Nome</td>
    <td>Telefone</td>
  </tr>
<tbody>
<tr>
  <td>Pedro</td>
  <td>1234567</td>
</tr>
  <tr>
    <td>Sofia</td>
    <td>567567567334</td>
  </tr>
</tbody>
</table>
```

A tabela seria apresentada da seguinte forma:

Nome	Telefone
Pedro	1234567
Sofia	567567567334

### Distinção nítida de linhas e colunas

Utilize a propriedade border em td para criar um contorno entre as linhas e colunas e também utilize a mesma propriedade em table para criar um contorno envolta de toda a tabela.

### Como mesclar uma linha ?

Utilize o atributo colspan na tag `<td></td>`, passando como valor o número de colunas que uma tag deverá ocupar.

### Como mesclar uma coluna ?

Utilize o atributo rowspan na tag `<tr></tr>`, passando como valor o número de linhas que uma tag deverá ocupar.

### Como organizar as tabelas ?

Para que uma ou mais linhas permaneçam na parte superior da tabela, indicando o cabeçalho, coloque elas dentro de uma tag `<thead></thead>`. Enquanto as demais linhas devem estar dentro de uma tag `<tbody></tbody>`.

```html
<table>
  <thead>
    <tr>
      <td>informacoes</td>
      <td>Telefone</td>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>Pedro</td>
    <td>1234567</td>
  </tr>
    <tr>
      <td>Sofia</td>
      <td>567567567334</td>
    </tr>   
  </tbody>   
</table>
```

Se você deseja que uma linha permaneça na parte inferior da tabela, coloque elas em uma tag `<tfoot></tfoot>`.
### Junção e separação de tabelas

Coloque dentro do seletor table a propriedade border-collapse. O valor collapse junta as linhas e colunas enquanto o valor separate separa as linhas e colunas.

## 118. Legendas e outras tags

Para criar uma legenda para uma tabela, utilize a tag `<caption></caption>`. Independente de onde ela estiver posicionada no container `<table></table>`, esta legenda sempre estará acima da tabela. Exemplo da legenda "Tabela de preços de cursos":

![[Pasted image 20250408124835.png]]

### Tag th

Utilize esta tag dentro `<tr></tr>` em vez da tag `<td></td>` para a criação de colunas. Elas, por padrão, criam palavras em negrito.

## 119. Tags details e summary

Estas tags são utilizadas em conjunto com objetivo de omitir alguma informação que só será exposta visualmente assim que o usuário clicar no conteúdo presente na tag `<summary></summary>`. Todo o conteúdo dentro da tag `<details></details>`, com exceção de `<summary></summary>`, ficará oculto.

O código a seguir mostra um exemplo em que a exibição da resposta só acontecerá a partir do momento em que o usuário clicar no elemento `<summary></summary>`:

```html
<h1>Qual a fórmula da água?</h1>
<ol type="A">
	<li>Duas móleculas de hidrogênio e uma de oxigênio</li>
	<li>Duas móleculas de hidrogênio e duas de oxigênio</li>
	<li>Uma mólecula de hidrogênio e uma de oxigênio</li>
</ol>
      
<details>
  <summary>Resposta:</summary>
  <p>Letra: A</p>
</details>
```

Ao carregar o documento HTML, o resultado será este:

![[Pasted image 20250410123235.png]]

### Como mudar a cor do ícone do summary ?

Coloque a propriedade color no seletor summary:

```css
summary{
    color: red;
}
```

**OBS.: não use o seletor details, pois as configurações também refletirão no conteúdo omitido.**

### Atributo open

Ao colocar este atributo booleano (que indica true quando está presente e false quando está ausente) no elemento `<details></details>`, o corpo da informação, que antes estava oculto, agora se mostrará exposto ao carregar a página.

```html
<details open>
  <summary>Resposta:</summary>
  <p>Letra: A</p>
</details>
```

### Definir declarações para o elemento details com o atributo open

Coloque o seletor details seguido de colchetes e, entre colchetes, informe o atributo open. A partir disso, coloque entre chaves as declarações desejadas:

```css
details[open]{

    background-color: rgb(142, 186, 139);

}
```

Isso fará com que determinada cor seja aplicada no conteúdo assim que as informações presentes em `<details></details>` forem expostas:

![[Pasted image 20250410125348.png]]

**OBS.: sempre que desejar selecionar um elemento com determinado atributo, siga o formato mostrado anteriormente: seletor[atributo]**

## 120. Popover

O atributo **popover** serve para criar uma espécie de pop-up no elemento que tiver tal atributo. É necessário que ele esteja vinculado a um botão por meio do atributo id no elemento que tiver popover e também através do atributo **popovertarget** presente no botão e que receberá o valor do id do outro elemento. Exemplo:

```html
<button popovertarget="mypopover">popover</button>
<p id="mypopover" popover>TESTE 1</p>
```

Neste exemplo, o parágrafo ficará oculto até que você clique no botão. No entanto, para que o parágrafo seja ocultado novamente, basta clica em qualquer lugar da tela (com exceção do próprio parágrafo).

**OBS.: neste caso, o atributo popover com o valor auto teria o mesmo funcionamento que sem este valor. Exemplo:**

```html
<button popovertarget="mypopover2">popover auto</button>
<p id="mypopover2" popover="auto">TESTE 2</p>
```

### Valor manual

Ao introduzir o valor **manual** no atributo popover, isso fará com que a ocultação do elemento seja apenas clicando no botão vinculado a ele:

```html
<button popovertarget="mypopover3">popover manual</button>
<p id="mypopover3" popover="manual">TESTE 3</p>
```

### Atributo popovertargetaction

Por meio do atributo **popovertargetaction** é possível definir se botão irá expor (através do valor **show**) ou ocultar (através do valor **hide**) o elemento vinculado a ele.

```html
<button popovertarget="mypopover4" popovertargetaction="show">SHOW</button>
<button popovertarget="mypopover4" popovertargetaction="hide">HIDE</button>

<p id="mypopover4" popover="manual">TESTE 4</p>
```

### Pseudo-classe :popover-open

Este pseudo-classe permite fazer configurações em um elemento com popover. Exemplo:

```css
#mypopover4:popover-open{

    background-color: darkblue;
    color: aliceblue;

}
```

**OBS.: se não for colocado o seletor, popover-open aplicará isso a todos os elementos com popover**

### Pseudo-elemento ::backdrop

Define as configurações do fundo de um elemento com popover no momento em que ele é mostrado.

```css
#mypopover4::backdrop{

    background-color: rgba(0, 0, 0, 0.397);

}
```

Exemplo:

![[Pasted image 20250410150830.png]]

