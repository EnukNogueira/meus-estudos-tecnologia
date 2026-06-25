## MANIPULAÇÃO DE DADOS EM GERAL

### Inserção de Dados (`INSERT INTO`)

É possível realizar inserções unitárias ou em lote (_bulk insert_) separando as tuplas por vírgula.

SQL

```
-- Inserção Unitária de Registro
INSERT INTO tabelaclientes (id_cliente, Nome_Cliente, inf_contato, Endereço_Cliente)
VALUES ('1', 'Ana', 'empresa.teste@gmail.com', 'Rua Tururu');

-- Inserção em Lote (Melhor performance: reduz overhead de transação)
INSERT INTO tabelaclientes (id_cliente, Nome_Cliente, inf_contato, Endereço_Cliente)
VALUES 
    ('2', 'Anais', 'empresa2.teste@gmail.com', 'Rua Tururu'),
    ('3', 'Enais', 'empresa3.teste@gmail.com', 'Rua Tururu'),
    ('4', 'Teste', 'empresa4.teste@gmail.com', 'Rua Tururu');

```

* * *

##  Consultas de Dados: Comando SELECT

O `SELECT` recupera dados de tabelas projetando colunas específicas e aplicando filtros horizontais na busca.

SQL

```
-- Sintaxe Geral de Projeção de Colunas Específicas
SELECT COLUMN1, COLUMN2 FROM TABLE_1;

-- Projeção de Todas as Colunas (Evitar em produção devido ao custo de I/O de rede)
SELECT * FROM TABLE_1;

-- Filtragem de Registros com Cláusula WHERE (Predicado Condicional)
SELECT * FROM nome_da_tabela WHERE nome_da_coluna = 'China';

```

### Funções de Agregação e Modificadores

#### COUNT

Conta o número de registros que atendem a um critério.

SQL

```
-- Contagem total de linhas da tabela
SELECT COUNT(*) FROM FilmLocations;

-- Contagem condicional baseada em predicado string
SELECT COUNT(Locations) 
FROM FilmLocations 
WHERE Writer = 'James Cameron';

```

#### DISTINCT

Elimina linhas duplicadas do conjunto de resultados antes de retorná-lo.

SQL

```
-- Retorna os títulos únicos, descartando duplicatas
SELECT DISTINCT Title FROM FilmLocations;

-- Combinação de Agregação com Modificador de Distinção
SELECT COUNT(DISTINCT ReleaseYear) 
FROM FilmLocations 
WHERE ProductionCompany = 'Warner Bros. Pictures';

```

* * *

##  Cenários Avançados e Manipulação de Fluxo

### Cenário 1: Carga de Dados Baseada em Queries (_Subqueries_ no Insert)

Útil para migração de dados históricos ou processamento de tabelas de agregação (_Gold Layers_).

SQL

```
INSERT INTO tabelapedidosgold (
    ID_pedido_gold, 
    Data_Do_Pedido_gold, 
    Status_gold, 
    Total_Do_Pedido_gold, 
    Cliente_gold, 
    Data_De_Envio_Estimada_gold
)
SELECT
    id,
    data_do_pedido,
    status,
    total_do_pedido,
    cliente,
    data_de_envio_estimada
FROM tabelapedidos
WHERE total_do_pedido >= 400;

```

### Cenário 2: Transferência de Dados entre Tabelas com Expurgamento

Processo comum de arquivamento ou segregação de dados (_Cold Storage_).

SQL

```
-- Passo 1: Inserir dados na tabela de histórico baseado no predicado de idade
INSERT INTO Ex_Alunos (ID, nome, idade)
SELECT ID, nome, idade
FROM Alunos
WHERE idade > 20;

-- Passo 2: Expurgar os dados migrados da tabela original (Garantindo a atomicidade do processo)
DELETE FROM Alunos
WHERE idade > 20;

```

### Cenário 3: Sincronização de Estoque com Junções Relacionais (`JOIN` + `UPSERT`)

Cenário clássico de Engenharia de Dados: atualizar registros existentes ou inseri-los caso não existam, realizando cálculos matemáticos baseados no relacionamento entre tabelas.

SQL

```
-- Operação de Upsert combinando dados calculados de vendas e estoque atual
INSERT OR REPLACE INTO Estoque (ID_produto, quantidade)
SELECT 
    Vendas.ID_produto, 
    Estoque.quantidade - Vendas.quantidade
FROM Vendas
JOIN Estoque ON Vendas.ID_produto = Estoque.ID_produto;

```

> **Nota sobre o JOIN:** O comando `JOIN` correlaciona as linhas da tabela `Vendas` com as da tabela `Estoque` na memória RAM do servidor através do operador de igualdade `ON Vendas.ID_produto = Estoque.ID_produto`. Isso permite que a subtração matemática ocorra linha a linha antes da gravação final no bloco de armazenamento do banco de dados.

- **DDL (Data Definition Language)**: Conjunto de comandos SQL usados para definir ou modificar a estrutura de objetos de um banco de dados (tabelas, índices, etc.).
- **ALTER TABLE**: Comando utilizado para alterar a estrutura de uma tabela existente (adicionar/remover colunas, alterar tipos de dados).
- **TRUNCATE TABLE**: Comando que remove permanentemente todos os registros de uma tabela, mantendo sua estrutura intacta.
- **DROP TABLE**: Comando que remove a definição da tabela e todos os seus dados do banco de dados.
- **NOT NULL**: Restrição que impede a inserção de valores nulos em uma coluna específica.

## Manipulação de Dados (DML)

### Inserção de Dados (`INSERT INTO`)

Para inserir registros, definimos as colunas e os valores correspondentes. É possível inserir múltiplos registros de uma vez separando-os por vírgula.

SQL

```
INSERT INTO tabelaclientes (id_cliente, Nome_Cliente, inf_contato, Endereço_Cliente)
VALUES 
('2', 'Anais', 'empresa2.teste@gmail.com', 'Rua Tururu'), 
('3', 'enais', 'empresa2.teste@gmail.com', 'Rua Tururu'), 
('4', 'teste', 'empresa2.teste@gmail.com', 'Rua Tururu');

```

### Carga de Dados entre Tabelas

Podemos povoar uma tabela utilizando os resultados de uma consulta em outra. O comando `INSERT INTO ... SELECT` é extremamente eficiente para migração e backup.

SQL

```
INSERT INTO tabelapedidosgold (ID_pedido_gold, Data_Do_Pedido_gold, Status_gold, Total_Do_Pedido_gold, Cliente_gold, Data_De_Envio_Estimada_gold)
SELECT id, data_do_pedido, status, total_do_pedido, cliente, data_de_envio_estimada
FROM tabelapedidos
WHERE total_do_pedido >= 400;

```

> **Nota :** Ao mover dados entre tabelas, o uso de `JOIN` aliado ao `INSERT` permite realizar cálculos e filtros complexos em uma única transação, minimizando o impacto no servidor.