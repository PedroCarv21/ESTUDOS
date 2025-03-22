
## Listas aninhadas

Nada mais são do que listas dentro de listas. Exemplo:

```
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

```
    <dl>
      <dt>HTML</dt>
      <dd>Lingaugem de marcação</dd>
      <dt>Javascript</dt>
      <dd>Linguagem de programação que roda tanto no Front quanto no Back</dd>
    </dl>
```

