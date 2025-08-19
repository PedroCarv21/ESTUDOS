
## 33. Resolvendo conflitos - Github

### Conflito na hora do merge

Em casos onde 2 ou mais programadores estão tentando mesclar com a branch `main` uma alteração na mesma linha de código do mesmo arquivo, haverá um conflito.

O primeiro programador até conseguirá mesclar sua alteração com a `main`, mas os demais terão o seguinte problema:

![[Pasted image 20250818154830.png]]

Neste caso, clique em `Resolve conflicts` e decida qual das versões do código você deseja manter. Exemplo:

![[Pasted image 20250818155227.png]]

Na branch `main` se encontra o seguinte código:

```
metodo(){
 programador1
}
```

Já na branch `programdor2` se encontra o seguinte código:

```
metodo(){
 programador2
}
```

Você deve escolher qual deve permanecer e clicar em `Mark as resolved` e, por fim, em `Commit merge`.

## 34. Resolvendo conflitos - Local

### Visualização do conteúdo do arquivo

Digite `cat` mais o nome do arquivo.

### Fazendo `merge` pelo Git

Digite `git merge` mais o nome da branch que deseja mesclar. Caso ocorra um conflito, irá aparecer, no arquivo do se repositório local, a mesma estrutura que apareceu lá no GitHub quando ocorreu um conflito:

![[Pasted image 20250818155227.png]]

Faça a alteração no arquivo, crie um novo commit e, por fim, execute o `git push`.