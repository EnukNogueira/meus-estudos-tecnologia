## ORDER BY

Para utilizar a cláusula `ORDER BY` em SQL, deve inseri-la no final de uma instrução `SELECT` para ordenar os dados retornados pela sua consulta. A ordenação é feita com base numa ou mais colunas da tabela.

A sintaxe básica é a seguinte:

SQL

```
SELECT coluna1, coluna2
FROM nome_da_tabela
ORDER BY coluna1 [ASC | DESC];

```

- **`ASC` (Ascendente)**: É a ordenação padrão. Organiza os dados do menor para o maior (ou alfabeticamente de A a Z). Se não especificar nada, o SQL utilizará esta opção automaticamente.
- **`DESC` (Descendente)**: Organiza os dados do maior para o menor (ou de Z a A).

**Exemplo prático:** Imagine que tem uma tabela chamada `Clientes` e quer listar todos os clientes ordenados pelo nome de forma decrescente:

SQL

```
SELECT Nome, Email
FROM Clientes
ORDER BY Nome DESC;

```

Se pretender ordenar por mais do que uma coluna em simultâneo, basta separá-las por vírgulas. Por exemplo, para ordenar primeiro pela idade de forma crescente e, em caso de idades iguais, pelo nome de forma decrescente:

SQL

```
SELECT Nome, Idade
FROM Clientes
ORDER BY Idade ASC, Nome DESC;
```