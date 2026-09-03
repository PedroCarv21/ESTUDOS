
# 5. Sobre a série - Série NET e DB

## O que é ADO.NET?

É um conjunto de classes e componentes da plataforma .NET que funciona como uma ponte entre o código do seu programa e o banco de dados.

O **ADO.NET** faz parte da **BCL (Base Class Library)**, que fornece as classes base (como `Connection`, `Command` e `DataReader`) que o ADO.NET utiliza para gerenciar conexões e consultas.

## O que é o Dapper?

É um **micro-ORM**, pois não tenta abstrair completamente o banco de dados. Em vez disso, fornece um jeito simples e rápido de mapear resultados de queries SQL para objetos C#. O Dapper é - próximo do ADO.NET puro, mas com muito menos código e é ideal quando você já tem queries SQL prontas e quer apenas mapear resultados para objetos.
## O que é Entity Framework (EF) Core?

Diferente do Dapper, que ainda permite bastante a criação de queries SQL, o EF é um ORM completo que abstrai boa parte da interação com o banco. Ele mapeia classes diretamente para tabelas, permitindo consultas com LINQ e geração automática de SQL.

Além disso, o EF possui:

- **Acompanhamento de mudanças (Change Tracking):** é capaz de criar de queries mais sofisticadas com base nas alterações que foram realizadas (e acompanhadas pelo EF Core) lá no banco de dados.
- **Logs:** mostram exatamente quais códigos SQL o EF Core cria a partir das suas consultas em LINQ.
- **Migrations:** são um recurso que atualiza automaticamente o esquema do banco de dados para mantê-lo sincronizado com as suas classes de modelo em C#.