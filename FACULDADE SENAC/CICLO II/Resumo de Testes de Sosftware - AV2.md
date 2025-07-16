
## Comandos ou arquivos utilizados

- **`chromedriver.exe`**: um executável que recebe comandos do seu código Java (via Selenium) e executa essas ações no Chrome.
- Classe **`BaseTest`**:
	- `System.setProperty(String key, String value)`: define uma propriedade (o mesmo que uma configuração do ambiente Java). Neste caso, será escolhida a propriedade `webdriver.chrome.driver` e o valor como sendo o caminho até o executável (ex.: `src/test/resources/chromedriver.exe`).
	- `WebDriver`: interface que automatiza o navegador como se fosse um usuário real clicando, digitando e navegando.
	- `ChromeDriver()`: uma classe que implementa a interface `WebDriver`, permitindo controlar o navegador Chrome.
	- `driver.manage().window().maximize()`
	- `driver.get()`: abra uma página web.
	- `driver.quit()`: fecha uma página web.
- Classe **`BasePO`**:
	- `PageFactory.initElements(driver, this)`: Inicializa os `WebElements` definidos na classe (normalmente uma classe de página). `@FindBy(...)` não localiza o elemento imediatamente. Ele apenas declara o que será buscado.
- Classe **`LoginPO`**:
	- `WebElement`: representa qualquer elemento HTML como, por exemplo, um campo de entrada, um link, um título, etc.
	- `@FindBy(id = "")`: localiza um elemento HTML com base no ID. Logo, é possível associar um elemento HTML com uma variável:
		- `@FindBy(id = "")`
		- `public WebElement campoDeBusca;`
- Classe **`TestLogin`**:
	- `@FixMethodOrder(MethodSorters.NAME_ASCENDING)`:  `@FixMethodOrder` indica ao JUnit que ele deve seguir uma ordem específica ao executar os métodos @Test dentro de uma classe de teste. `MethodSorters.NAME_ASCENDING` é um dos valores possíveis de ordenação. Significa que os métodos de teste serão executados em ordem alfabética crescente com base no nome do método.
	- `sendKeys("text")`: digita um texto em um campo de entrada.
	- `click()`: clica no elemento.
	- `getText()`: lê o texto que aparece no elemento.
	- `getTitle()`:  obter o título da aba do navegador da página atual carregada.