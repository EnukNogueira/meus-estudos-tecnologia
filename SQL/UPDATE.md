## UPDATE

# Alterando o status com a cláusula `UPDATE`

No _SQLite Online_, na parte superior direita, clicamos no ícone identificado pelo símbolo de `+` para abrir uma nova aba de código. Começamos escrevendo `UPDATE`, seguido pelo nome da tabela que queremos alterar, nesse caso`tabelapedidos`. Em seguida, passamos a cláusula `SET`, que significa definir. Depois passamos a coluna `status` igual à `'Enviado'`. Na mesma linha, precisamos definir onde queremos que apareça essa mensagem. Portanto, precisamos especificar. Passamos então `WHERE status` igual à `'Processando'`.

```
UPDATE tabelapedidos SET status = 'Enviado' WHERE status = 'Processando';
Copiar código
```

Na barra de menu superior, clicamos no botão "Run" para rodar o código. Deu tudo certo. Agora, entenderemos o passo a passo de como fazemos essa consulta.

Primeiro pedimos que seja feito um `UPDATE`. Nisso, precisamos especificar onde isso acontecerá, nesse caso, na tabela de pedidos. Em seguida, definimos o que queremos colocar nessa tabela. Queremos definir como status "enviado" onde agora está o status "processando".

> Se analizarmos cada parte do código, considerando as palavras em inglês, conseguimos entender muito bem o que é feito em cada trecho.

Agora verificaremos se deu certo. Para isso, na linha 3, para consultar a tabela, escrevemos `SELECT * FROM tabelapedidos`.

```
SELECT * FROM tabelapedidos;
Copiar código
```

Selecionamos apenas essa linha de código e clicamos em "Run". Feito isso, temos o seguinte retorno:

| ID  | Data\_do\_Pedido | Total\_do\_Pedido | Cliente | Data\_de\_Envio\_Estim... |
| --- | --- | --- | --- | --- |
| 6   | 2023-08-06 | 200 | 6   | 2023-08-09 |
| 7   | 2023-08-07 | 380.9 | 9   | 2023-08-18 |
| 8   | 2023-08-08 | 600.25 | 14  | 2023-08-11 |
| 9   | 2023-08-09 | 120.5 | 4   | 2023-08-14 |
| 10  | 2023-08-10 | 420.75 | 10  | 2023-08-16 |
| 11  | 2023-08-11 | 180 | 1   | 2023-08-22 |
| 12  | 2023-08-12 | 320.25 | 7   | 2023-08-19 |
| 13  | 2023-08-13 | 90.75 | 3   | 2023-08-07 |
| //Dados omitidos | <br> | <br> | <br> | <br> |

# Alterando os dados de uma linha com a cláusula `UPDATE`

Também podemos utilizar essa cláusula para modificar apenas uma linha de várias colunas ao mesmo tempo. Para isso, abrimos uma nova aba clicando no botão indicado pelo símbolo de `+`, na lateral superior direita da tela.

O que faremos agora é atualizar o endereço e e-mail da pessoa cliente de ID número 2. Para fazer essa alteração, começamos escrevendo `UPDATE tabelaclientes` seguido de `SET informacoes_de_contato` igual à `'j.santos@email.com'`.

Na mesma linha, adicionamos vírgula e pulamos para a linha seguinte. Nela, escrevemos `endereco_cliente` igual à `'Rua dos paralelepipedos, 30'`. Abaixo, para especificarmos o cliente que queremos mudar, passamos a cláusula `WHERE` seguido de `id_cliente` igual à `2`.

```
UPDATE tabelaclientes SET informacoes_de_contato = 'j.santos@email.com', 
endereço_cliente = 'Rua dos paralelepipedos, 30 '
WHERE id_cliente = 2;
Copiar código
```

Clicamos em "Run" para rodar o código. Na linha 5 passamos o `SELECT * FROM tabelaclientes` para acessar a tabela de clientes e verificar se deu certo. Selecionamos apenas essa linha e clicamos em "Run".

```
SELECT * FROM tabelaclientes;
Copiar código
```

Feito isso, temos o retorno abaixo.

| ID  | Nome Cliente | Informacoes\_de\_Contato | Endereço\_Cliente |
| --- | --- | --- | --- |
| 1   | Ana Silva | ana [silva@email.com](mailto:silva@email.com) | rua florescasa 1 |
| 2   | João Santos | [j.santos@email.com](mailto:j.santos@email.com) | Rua dos paralelepipedos, 30 |
| 3   | Maria Fernandes | maria [fernandes@email.com](mailto:fernandes@email.com) | Rua Santo Antonio, 10 |
| 4   | Carlos Pereira | carlos [pereira@email.com](mailto:pereira@email.com) | Avenida rio, 67 |
| //Dados omitidos | <br> | <br> | <br> |