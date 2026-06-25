### PRIMARY KEY

A **Primary Key** é a espinha dorsal da integridade da tabela. Sem ela, o banco de dados perde a capacidade de identificar registros individualmente.

- **Unicidade:** Impede duplicidade.
- **Não Nulo:** Obrigatório, pois um registro sem ID não é endereçável.
- **Eficiência:** O SGBD cria índices automaticamente, acelerando consultas.

Exemplo de criação de tabela com **Primary Key**:

SQL

```
CREATE TABLE categoria_dos_produtos (
    ID_Categoria INT PRIMARY KEY, 
    insalubre VARCHAR(250), 
    quantidade VARCHAR(250), 
    Descricao_Categoria TEXT
);

```

### Foreign Key

A **Foreign Key** atua como uma ponte. Pense nela como uma "seta" que aponta para um registro específico em outra tabela, garantindo que o dado associado realmente exista.

SQL

```
CREATE TABLE tabelaprodutos (
    ID_Produto INT PRIMARY KEY,
    Nome_do_Produto VARCHAR(250),
    Descrição TEXT,
    Categoria INT,
    Preco_de_Compra DECIMAL(10,2),
    Unidade VARCHAR(50),
    Fornecedor INT,
    Data_de_Inclusao DATE,
    FOREIGN KEY (Categoria) REFERENCES tabelacategorias (id_categoria),
    FOREIGN KEY (Fornecedor) REFERENCES tabelafornecedores (id)
);

```

## <br>