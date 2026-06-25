## ALTER TABLE

O `ALTER TABLE` é essencial quando os requisitos de negócio mudam e a estrutura da tabela precisa evoluir.

### Adicionar Colunas

Adicionar uma nova coluna a uma tabela existente. Por padrão, novos registros receberão o valor `NULL`.

SQL

```
ALTER TABLE author 
ADD telephone_number BIGINT;

```

### Modificar Tipos de Dados

Utilizado quando a definição original da coluna não atende mais à necessidade de armazenamento (ex: permitir caracteres especiais em um número de telefone).

SQL

```
ALTER TABLE author 
MODIFY telephone_number CHAR(20);

```

## 3\. Criação e Ciclo de Vida de Tabelas

### Criando Tabelas com Integridade

Ao criar uma tabela, é fundamental definir os tipos de dados e aplicar restrições como `PRIMARY KEY` e `NOT NULL` para garantir a integridade da entidade.

SQL

```
CREATE TABLE COUNTRY (
    ID int NOT NULL,
    CCODE char(2),
    Name varchar(60),
    PRIMARY KEY (ID)
);

```

### Removendo Dados vs. Removendo Tabelas

É crucial distinguir entre esvaziar uma tabela e excluí-la:

- **TRUNCATE**: Limpa apenas o conteúdo. A tabela permanece disponível.

SQL

```
TRUNCATE TABLE author;

```
- **DROP**: Exclui o objeto (tabela) e todos os seus dados.

SQL

```
    DROP TABLE COUNTRY;
    ```

> **Dica de Engenharia**: Em ambientes de desenvolvimento e testes, é prática comum realizar um `DROP TABLE` antes de um `CREATE TABLE` para garantir um estado limpo, mas **nunca** utilize esta prática em ambientes de produção sem backups validados.

---

## 4. Perguntas de Fixação

**1. Qual é a diferença fundamental entre os comandos `TRUNCATE` e `DROP`?**
*   a) `TRUNCATE` remove a estrutura da tabela, enquanto `DROP` mantém a estrutura.
*   b) `TRUNCATE` remove apenas os dados, mantendo a estrutura da tabela para uso posterior, enquanto `DROP` remove tanto os dados quanto a definição da própria tabela.
*   c) Não há diferença; ambos realizam a mesma função em diferentes dialetos SQL.
*   d) `DROP` só pode ser usado em chaves primárias, enquanto `TRUNCATE` atua apenas em colunas de texto.

**2. Por que a restrição `NOT NULL` é comumente associada a colunas definidas como `PRIMARY KEY`?**
*   a) Porque o SQL padrão exige que chaves primárias sejam sempre caracteres.
*   b) Porque colunas `NOT NULL` são automaticamente transformadas em índices de performance.
*   c) Porque uma chave primária serve para identificar de forma única um registro e, portanto, não pode conter valores ausentes (NULL).
*   d) Porque o tipo de dado `INT` sempre exige a restrição `NOT NULL` obrigatoriamente.

**3. Se você precisa alterar o formato de uma coluna para aceitar caracteres especiais (como parênteses em números), qual comando SQL é o mais adequado?**
*   a) `ALTER TABLE table_name ADD column_name;`
*   b) `TRUNCATE TABLE table_name;`
*   c) `ALTER TABLE table_name MODIFY column_name CHAR(20);`
*   d) `DROP TABLE table_name;`

```

- **Integridade da Entidade**: Regra que garante que cada tabela possua uma **chave primária** única, que não aceita valores nulos, permitindo identificar cada registro de forma exclusiva.
- **Integridade Referencial**: Regra que assegura que uma **chave estrangeira** esteja sempre vinculada a uma chave primária existente em outra tabela, mantendo a consistência lógica.
- **Integridade de Domínio**: Conjunto de restrições que valida o conteúdo de uma coluna (ex: tipo de dado, formato, intervalos de valor e obrigatoriedade).
- **Script SQL**: Conjunto de instruções SQL compiladas em um único arquivo (.sql) para automação de tarefas de definição, manipulação e controle de dados.