## Primeiro curso Java

<br>

Variável (sempre inicia com letra minúscula) = int ano =2022;

<br>

- O operador AND(&&), que traduzindo para o português seria E, seria utilizado para ver se ambos os números são true(verdadeiros)

<br>

- O operado OR (||), que traduzindo para o português seria OU, seria utilizado para verificar se somente uma condição seria verdadeira. 

<br>

- O operador NOT(!) que traduzindo para o português seria NÃO, seria utilizado para mostrar que a condição é false(falsa)

<br>

- Operador de pré-incremento: serve para adicionar mais um valor na variável antes de usar em uma expressão.  

<br>

```java
int num = 5 
int resultado = ++num;
System.out.println(num); // Imprime 6
System.out.println(resultado); // Imprime 6
```

<br>

- Já o operador pós incremento serve para adicionar um valor na variável depois de uma expressão 

```java
int num = 5 
int resultado = num++;
System.out.println(num); // Imprime 6
System.out.println(resultado); // Imprime 5

```

<br>

**ca⁠melCase**  

- nomes de classe devem começar com a letra maiúscula e usar a convenção **PascalCase** 

Exemplo 1: `MinhaClasse .`

<br>

- Nomes de métodos devem começar com a letra minúscula e usar a convenção camelCase

Exemplo 2: `minhaClasse( );`

<br>

- Nomes de constantes devem ser escritas com a letra MAIÚSCULA e separadas por underline

Exemplo 3: `MINHA_VARIAVEL`

<br>

- Nomes de variável devem começar com a letra minúscula e usar o camelCase

Exemplo 4: `minhaClasse`

<br>

Aspas triplas “”” servem para criar um bloco de texto onde possibilita pular linhas. 

<br>

Exemplo 1: 

<br>

`String sinopse;` 

`sinopse = """ Filme Top gun Filme de aventura nota 8 ano de lançamento: 2023 """;`

<br>

Scanner é uma classe que é usado quando voce quer colocar algum texto ou resposta no código quando ele for executado. No caso o java le e guarda o que o usuário digitou.

<br>

Exemplo de como imprimir um numero que o usuário digitará: `int anoDeLancamento = leitura.nextInt( );`

O comando .nextInt serve para imprimir um numero inteiro que o usuário colocará 

mesma coisa sera o comando .nextLine que é para escrever uma linha de texto.

.nextDouble seria para colocar números sem ser inteiros.