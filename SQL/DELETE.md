## DELETE

- **DELETE:** Comando DML utilizado para remover um ou mais registros de uma tabela.
- **WHERE:** Cláusula de filtro fundamental. Sem ela, o comando `DELETE` removerá **todos** os registros da tabela.
- **Operadores Lógicos/Relacionais:** Símbolos como `>`, `<`, `=`, `AND`, `OR` usados para restringir quais linhas serão afetadas.
- **Integridade de Dados:** O estado de precisão e consistência dos dados; operações destrutivas devem sempre considerar se o registro a ser apagado não é necessário por outras tabelas (integridade referencial).

## Operações de Exclusão

### Exclusão Específica

Para remover registros baseados em uma condição simples (neste caso, a origem do fornecedor), utilizamos a estrutura `DELETE FROM` seguida do `WHERE`.

SQL

```
DELETE FROM tabelafornecedores 
WHERE pais_de_origem = 'Turquia';

```

### Exclusão com Operadores de Comparação

Podemos utilizar operadores relacionais para remover conjuntos de dados que atendam a uma regra numérica ou de data.

SQL

```
DELETE FROM tabelafornecedores 
WHERE id > 35;

```

## Boas Práticas e Segurança

> **Atenção:** A cláusula `DELETE`, assim como o `UPDATE`, opera de forma destrutiva. Siga sempre este checklist antes de executar:
> 
> 1. **Sempre utilize o `WHERE`:** Garanta que você está isolando apenas o registro ou grupo de registros desejado.
> 2. **Execute um `SELECT` primeiro:** Antes de rodar o `DELETE`, utilize a mesma condição dentro de um `SELECT` para visualizar exatamente quais linhas serão afetadas.
> 3. **Backup/Transação:** Em ambientes de produção, certifique-se de ter um backup recente ou utilize transações (se o SGBD permitir o _rollback_) para reverter erros.

**Exemplo de verificação prévia:**

SQL

```
-- Primeiro, valide quem será deletado
SELECT * FROM tabelafornecedores WHERE id > 35;

-- Após conferir o resultado, execute a exclusão
DELETE FROM tabelafornecedores WHERE id > 35;
```