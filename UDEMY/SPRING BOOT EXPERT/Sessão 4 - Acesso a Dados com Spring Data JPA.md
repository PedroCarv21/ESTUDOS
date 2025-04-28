
## 41. Introducação ao Spring Data JPA

### Como funciona a JPA

A JPA possui a seguinte estrutura:

![[Pasted image 20250416151022.png]]

1. **Banco de dados**: deve ser escolhido algum banco de dados como MySQL, SQL Driver, entre outros.
2. **Data Source**: uma fonte escolhida para extrair dados (seja um banco de dados, arquivos, API, etc...). Neste caso, é um banco de dados.
3. **EntityManagerFactory**: é uma interface responsável por criar instâncias de Entity Managers.
4. **EntityManager**:  é uma ferramenta do JPA que gerencia as entidades durante as operações CRUD.

Em suma, haverão entidades representando tabelas do banco e, para que sejam feitas operações CRUD, será necessário um EntityManager criado através de um EnitytManagerFactory.

Por meio da utilização do JPA, o framework Spring Data JPA consegue fornecer outros recursos que simplificam a manipulação de dados. Entre eles está os JPA Repositories (que armazenam dentro de si o EntityManager).


![[Pasted image 20250416160337.png]]