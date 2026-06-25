## Scripts SQL e Automação

Scripts são ferramentas essenciais para a Engenharia de Dados, permitindo a reprodutibilidade de ambientes.

### Boas Práticas na Escrita de Scripts:

1. **Limpeza**: Utilize `DROP TABLE IF EXISTS` para evitar erros de duplicidade antes da criação.
2. **Sequenciamento**: A ordem de execução importa, especialmente devido às dependências de chaves estrangeiras.
3. **Delimitadores**: Utilize o ponto e vírgula (`;`) para encerrar cada comando.
4. **Extensão**: Sempre utilize a extensão `.sql`.

### Exemplo de Script Estrutural

SQL

```
DROP TABLE IF EXISTS PATIENTS;

CREATE TABLE PATIENTS (
  PATIENT_ID CHAR(9) NOT NULL,
  FIRST_NAME VARCHAR(15) NOT NULL,
  LAST_NAME VARCHAR(15) NOT NULL,
  DEPT_ID CHAR(9) NOT NULL,
  PRIMARY KEY (PATIENT_ID)
);
```