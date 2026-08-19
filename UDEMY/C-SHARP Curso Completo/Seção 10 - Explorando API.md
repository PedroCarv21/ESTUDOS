# 95. Arquivo Escrevendo Dados

## Verificando o sistema operacional

Para acessar uma pasta e criar um arquivo, é necessário antes saber qual sistema operacional o programa está rodando para que depois, posso percorrer o caminho até a pasta onde será criado o arquivo. Para isso, pode ser criado um método que verifique isso. Exemplo:

```csharp
public static string ParseHome(this string path)
{
    string home = (Environment.OSVersion.Platform == PlatformID.Unix
        || Environment.OSVersion.Platform == PlatformID.MacOSX)
        ? Environment.GetEnvironmentVariable("HOME")
        : Environment.ExpandEnvironmentVariables("%HOMEDRIVE%%HOMEPATH%");

    return path.Replace("~",  home);
}
```

A sequência de comandos `Environment.OSVersion.Platform == PlatformID.Unix || Environment.OSVersion.Platform == PlatformID.MacOSX` irá verificar se o sistema operacional é Linux ou MacOS e, em caso afirmativo, irá retornar uma informação vinculada a variável de ambiente `HOME`. 

Caso não seja Linux e nem MacOS, o método irá considerar que se trata de um sistema Windows e irá utilizar o método `ExpandEnvironmentVariables()` também para capturar os valores das variáveis de ambiente `%HOMEDRIVE%` e `%HOMEPATH%`. Por fim, será retornado a string com o caminho alterado.
## Procurando pelo arquivo

O cominho até o arquivo deve ser representado por uma string conténdo um `@` antes das aspas. Isso é necessário para que sejam ignorados caracteres especiais, como `\n`. Além disso, utilize o método `ParseHome()` para que a busca seja feita de maneira adequada.

```csharp
var path = @"~/ARQUIVOS_CRIADOS_POR_PROGRAMAS/arquivo_do_programa.txt".ParseHome();
```

O método para verificar se o arquivo existe ou não é o `File.Exists()` e o parâmetro passado deve ser o caminho; caso o arquivo não exista, utilize o método `File.CreateText()` para criar um arquivo baseado no caminho (passado como parâmetro) e utilize o `using` para gerenciar a abertura e fechamento de recursos que trabalham com arquivos. Por fim, utilize o comando `WriteLine()` para escrever no arquivo.

```csharp
if (!File.Exists(path))
{
    using (StreamWriter sw = File.CreateText(path))
    {
        sw.WriteLine("Testando o");
        sw.WriteLine("meu novo");
        sw.WriteLine("sistema.");
    }
}
```

Caso queira adicionar texto em arquivo já existente, utilize o `AppendText()` em vez do `CreateText()`. Exemplo:

```csharp
using (StreamWriter sw = File.AppendText(path))
{
    sw.WriteLine("Acrescentando");
    sw.WriteLine("Mais Texto");
}
```

# 96. Arquivo: Lendo Dados

Instancie a classe `StreamReader()`, passando como argumento o caminho, e utilize o método `ReadToEnd()` para que seja lido e retornando o conteúdo do arquivo num formato string. Exemplo:

```csharp
using (StreamReader sw = new StreamReader(path))
{
    string texto = sw.ReadToEnd();
    Console.WriteLine(texto);
}
```

# 97. Usando FileInfo

`FileInfo` é uma classe utilizada para obter informações e manipular arquivos. Estes são alguns métodos do `FileInfo`:

- **`Name`:** retorna o nome do arquivo.
- **`FullName`:** retorna o caminho completo até o arquivo.
- **`IsReadOnly`:** verifica se o arquivo está disponível apenas para leitura ou não.
- **`Extension`:** retorna a extensão do arquivo.
- **`DirectoryName`:** retorna o nome do diretório.
- **`Exists`:** verifica se o arquivo existe.
- **`Delete()`:** deleta o arquivo.
- **`CopyTo()`:** cria uma copia do arquivo e o armazena na pasta passada como argumento. Exemplo:
  
```csharp
var path = @"~/ARQUIVOS_CRIADOS_POR_PROGRAMAS/arquivo_do_programa.txt".ParseHome();
var path2 = @"~/ARQUIVOS_CRIADOS_POR_PROGRAMAS/copia/copia_arquivo.txt".ParseHome();

if (!File.Exists(path))
{
    using (StreamWriter sw = File.CreateText(path))
    {
        sw.WriteLine("Testando o");
        sw.WriteLine("meu novo");
        sw.WriteLine("sistema.");
    }
}
else
{
    FileInfo info = new FileInfo(path);
    info.CopyTo(path2);   
}
```

**OBS.: não crie uma cópia de um arquivo no mesmo lugar duas vezes, pois isso irá gerar uma exceção.**

- **`MoveTo()`** move um arquivo de um local para outro de acordo com o caminho informado.

**OBS.: se o caminho de destino tiver, no fim dele, um nome de arquivo diferente do nome atual, isso significa que o nome será alterado.**
# 98. Trabalhando com Diretórios

Métodos estáticos do `Directory` para a manipulação de arquivos:

- **`Exists()`:** verifica se um diretório existe de acordo com o caminho passado como argumento.
- **`Delete()`:** deleta a pasta de acordo o caminho passado como argumento, porém com algumas condições: se o segundo argumento for `false` então a pasta será deletada caso esteja vazia; se for `true`, então a pasta será deletada mesmo não estando vazia.
- **`CreateDirectory()`:** cria uma pasta no local informado como argumento.
- **`GetCreationTime()`:** retorna a data e a hora em que a pasta foi criada de acordo com o caminho passado como argumento.
- **`GetDirectories()`:** retorna um array de strings, sendo cada string o nome de uma pasta. Deve ser passado o caminho como argumento.
- **`GetFiles()`:** retorna um array de strings, sendo cada string o nome de um arquivo. Deve ser passado o caminho como argumento.
- **`GetDirectoryRoot()`:** retorna o diretório raiz do caminho informado.
- **`Move()`:** move um diretório de um lugar para outro de acordo com os caminhos passados como argumentos.
**OBS.: se o caminho de destino tiver, no fim dele, um nome de diretório diferente do nome atual, isso significa que o nome será alterado.**
# 99. Usando DirectoryInfo

## Classe `DirectoryInfo`

Essa classe é utilizada para manipulação e consulta de informações relacionadas a diretórios. Os seus métodos são de instância, portanto, é necessário instanciar a classe `DirectoryInfo` antes:

```csharp
DirectoryInfo dInfo = new DirectoryInfo(path);
```

Os principais métodos são:

- **`GetFiles()`:** retorna um vetor de elementos `FileInfo`.
- **`GetDirectories()`:** retorna um vetor de elementos `DirectoryInfo`.
- **`Exists`:** verifica se o diretório existe.
- **`Create()`:** cria um novo diretório.
- **`Root`:** retorna o diretório raiz.
- **`CreationTime`:** retorna a data e a hora em que o diretório foi criado.
- **`FullName`:** retorna o caminho completo do diretório.
- **`Parent`:** retorna o caminho até o diretório anterior ao diretório presente. É possível também criar uma cadeia de métodos `Parent`. Por exemplo:
  
  ```csharp
  Console.WriteLine(dInfo.Parent.Parent);
  ```
# 100. Usando Path

Estes são os métodos de classe do `Path`:

- **`GetExtension()`:** retorna a extensão.
- **`GetFileName()`:** retorna o nome do arquivo.
- **`GetFileNameWithoutExtension()`:** retorna o nome do arquivo sem extensão.
- **`GetDirectoryName()`:** retorna o nome do diretório atual.
- **`HasExtension()`:** verifica se possui uma extensão ou não (caso seja um diretório).
- **`GetFullPath()`:** retorna o caminho completo.
- **`GetPathRoot()`:** retorna o diretório raiz.
# 101. Usando DateTime

Criando uma instância de `DateTime`, será possível verificar depois os dados de dia, mês e ano. Exemplo:

```csharp
var data = new DateTime(2002, 11, 8);
Console.WriteLine(data);
Console.WriteLine(data.Year);
Console.WriteLine(data.Month);
Console.WriteLine(data.Day);
```

## Métodos estáticos

- **`DateTime.Today`:** retorna somente a data de hoje
- **`DateTime.Now`:** retorna a data e a hora atuais.
- **`DateTime.Now.Hour`:** retorna a hora atual.
- **`DateTime.Now.Minute`:** retorna o minuto atual.
- **`DateTime.Now.AddDays()`:** adiciona ou subtrai (caso informe um valor negativo) uma quantidade de dias.
- **`DateTime.Now.ToString("dd")`:** retorna o dia atual.
- **`DateTime.Now.ToString("d")`:** retorna a data atual.
- **`DateTime.Now.ToString("D")`:** retorna as informações sobre a data de um modo mais personalizado. Exemplo: terça-feira, 18 de agosto de 2026
- **`DateTime.Now.ToString("g")`:** retorna a data e hora atuais sem o minuto.
- **`DateTime.Now.ToString("G")`:** retorna a data e hora atuais.
- **`DateTime.Now.ToString("dd-MM-yyyy HH:mm:ss")`:** retorna a data e hora atuais de acordo com o formato passado como argumento.

# 102. Usando `TimeSpan`

A struct `TimeSpan` é utilizada para representar o tempo de duração. Essa é a forma de instanciá-la:

```csharp
var duracao = new TimeSpan(days: 10, hours: 5, minutes: 30, seconds: 20);
```

Estes são algum dos métodos utilizados para consultar as informações de data/hora e manipular esses valores:

- **`Add()`:** adiciona mais tempo. Alguns argumentos de exemplos que podem ser passados são `TimeSpan.FromMinutes()` ou `TimeSpan.FromDays()`, ambos os métodos recebendo números inteiros como argumentos.
- **`Subtract()`:** subtrai o tempo. Pode-se utilizar os mesmos tipos de argumentos que são passados para o `Add()`.
- **`TotalMinutes`:** transforma todo o tempo de um objeto `TimeSpan` em minutos.
- **`Parse()`:** transforma uma string em um objeto `TimeSpan`. Detalhe: o dia e a hora ficam separados por um ponto. Ex.: 20.14:23:10

## Calculando tempo restante

É possível subtrair um um objeto `DateTime` de outro objeto `DateTime`, o que resultará em um objeto `TimeSpan`. Exemplo:

```csharp
var tempoRestante = DateTime.Now.AddDays(5) - DateTime.Now;
Console.WriteLine(tempoRestante);
```