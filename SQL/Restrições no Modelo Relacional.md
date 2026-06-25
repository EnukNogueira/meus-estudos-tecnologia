## Restrições no Modelo Relacional

O design de bancos de dados eficientes depende do uso rigoroso de restrições para manter a acuracidade dos dados.

### A. Integridade da Entidade

Toda tabela deve possuir uma **PRIMARY KEY**.

- **Propriedade**: Exclusividade e não nulidade.
- **Exemplo**:

SQL

```
CREATE TABLE BookShop (
    BOOK_ID INT PRIMARY KEY,
    TITLE VARCHAR(100),
    AUTHOR_ID INT
);

```

### B. Integridade Referencial

Impede a criação de registros "órfãos" através da **FOREIGN KEY**.

- **Regra**: O valor inserido na chave estrangeira deve obrigatoriamente existir na tabela de referência.
- **Exemplo**:

SQL

```
CREATE TABLE BookShop (
    BOOK_ID INT PRIMARY KEY,
    TITLE VARCHAR(100),
    AUTHOR_ID INT,
    FOREIGN KEY (AUTHOR_ID) REFERENCES BookShop_AuthorDetails(AUTHOR_ID)
);

```

### C. Integridade de Domínio

Valida o dado no nível da coluna utilizando restrições como **CHECK** e **NOT NULL**.

- **Exemplo**:

SQL

```
CREATE TABLE BookShop (
    BOOK_ID INT PRIMARY KEY,
    TITLE VARCHAR(100) NOT NULL,
    PRICE DECIMAL(5, 2) CHECK (PRICE >= 0),
    PUBLISHED_DATE DATE
);
```