## Quarto Curso Java

<br>

### Analogia de Restaurante:

<br>

- **O "Garçom" (API):** O OMDb é como um garçom. Você (cliente/Java) faz um pedido (**HttpRequest**), o garçom leva para a cozinha (servidor do OMDb) e traz o prato (**HttpResponse**) com os dados do filme.
- **O Trio Parada Dura do Java:**
- **HttpClient:** É o seu "telefone" para ligar para a internet.
- **HttpRequest:** É a mensagem que você escreveu (ex: "Me dá os dados do filme Batman").
- **HttpResponse:** É o que chegou de volta (geralmente um JSON cheio de textos).
- **Postman:** É o seu "laboratório". Antes de escrever 20 linhas de Java, você testa no Postman para ver se a API está viva. Se funcionar lá, o erro no Java é código; se não funcionar lá, o erro é na API.

## 

* * *

# Bibliotecas vs. Frameworks em Java

**Conceito Geral:** São ferramentas que evitam "reinventar a roda", permitindo focar na **lógica do negócio** (o que o app faz) em vez de problemas técnicos repetitivos.

#### 1\. Bibliotecas (Libraries)

- **O que são:** Coleções de classes e interfaces prontas (ex: manipulação de arquivos, cálculos, criptografia).
- **Formato:** Geralmente distribuídas como arquivos **.JAR** (Java Archive).
- **Como funciona:** Você as **importa** e as utiliza quando quer. Você está no controle do fluxo.

#### 2\. Frameworks

- **O que são:** Uma "fábrica padronizada". É uma estrutura maior que dita a arquitetura do projeto e impõe regras/padrões.
- **Como funciona:** O framework "chama" o seu código. Ele fornece a base (esqueleto) e você preenche as lacunas.
- **Exemplos essenciais:**
    - **Spring:** Facilita a criação de APIs e aplicações Web complexas.
    - **Hibernate:** Simplifica a comunicação entre o Java e o Banco de Dados.

> **Nota de Estudo:** Para usar essas ferramentas com eficiência, é fundamental ter uma base sólida em **Java e Orientação a Objetos**.

## Java Records: O Container de Dados

**O que é:** Um recurso (Java 16+) para criar classes **imutáveis** (que não mudam) focadas exclusivamente em carregar **dados**, sem comportamentos complexos.

**O que ele faz por baixo dos panos:** Ao escrever apenas `public record Telefone(String ddd, String numero){ }`, o Java gera automaticamente para você:

1. **Atributos privados e finais** (imutáveis).
2. **Construtor** com todos os campos.
3. **Métodos de leitura** (como `ddd()` e `numero()`).
4. **Métodos Equals e HashCode** (para comparar objetos).
5. **Método ToString** (para imprimir os dados de forma legível).

* * *

##  Analogias para entender o Record

#### 1\. A Analogia da Ficha de Cadastro (Record) vs. Pasta de Arquivos (Classe Comum)

- **Classe Comum:** Imagine uma pasta de couro onde você tem que grampear as folhas, colocar etiquetas, criar um índice e decidir quem pode mexer. Dá muito trabalho para montar.
- **Record:** É como aquela **Ficha de Cadastro** padrão. Os campos já estão impressos (Nome, CPF, Tel). Você só preenche. Ela é o que é, não muda e serve apenas para levar a informação de um balcão para o outro.

#### 2\. A Analogia do Marmitex Lacrado

- **Classe Comum:** É um prato de restaurante onde você pode trocar o acompanhamento, pedir para tirar a cebola ou adicionar mais arroz enquanto come (os dados podem ser alterados/mutáveis).
- **Record:** É um **Marmitex selado na fábrica**. Você sabe exatamente o que tem dentro (ddd, numero), ele não pode ser aberto ou alterado depois de pronto. Se você quiser uma marmita diferente, tem que pedir uma nova. Ele serve apenas para transportar a comida do ponto A ao ponto B com segurança.

* * *

##  Por que usar no seu projeto de APIs?

Quando você busca dados no **OMDb**, o que vem é apenas informação. Você não precisa que o objeto "Filme" tenha lógica complexa; você só quer que ele segure o Nome e o Ano. Usar **Record** ali deixa seu código limpo e profissional.

**Dica para a anotação:** "Record = Menos código, mais semântica. Se o objeto é só para carregar dado, use Record."

## Imutabilidade em Java

**O que é:** A garantia de que, uma vez que um objeto foi criado na memória, ele **nunca** muda. Se você precisar de um valor diferente, o Java cria um objeto **novo**.

**A Pegadinha da Variável:**

- **O Objeto** é o conteúdo (ex: "Maria"). Ele é imutável.
- **A Variável** é apenas uma etiqueta (ponteiro). Ela pode ser descolada de um objeto e colada em outro.

**Por que é importante?**

1. **Segurança:** Você tem certeza que ninguém vai alterar um dado importante no meio do caminho.
2. **Multitarefa (Concorrência):** Várias partes do programa podem ler o mesmo objeto sem medo de ele mudar enquanto estão lendo.
3. **Performance:** O Java economiza memória reutilizando objetos iguais (como Strings repetidas).

* * *

##  Analogias para entender a Imutabilidade

#### 1\. A Analogia da Foto (Objeto) vs. O Porta-Retratos (Variável)

Imagine que você tem um **Porta-Retratos** (Variável).

- Você coloca a **Foto da Alice** (Objeto) dentro dele.
- Se você quiser que o porta-retratos mostre a Maria, você **não apaga** a cara da Alice e desenha a Maria por cima.
- Você joga a foto da Alice fora (ou guarda) e coloca uma **Foto Nova da Maria** no lugar.
- A foto (objeto) em si nunca mudou; você apenas trocou qual foto está sendo exibida no porta-retratos (referência).

#### 2\. A Analogia da Placa de Rua

Pense em uma placa que diz: **"Rua Java, 100"**.

- A placa é o objeto. Ela é feita de metal e está fixada ali.
- Se a prefeitura decidir mudar o nome da rua, eles não raspam o metal ali na esquina. Eles fabricam uma **placa nova** e substituem a antiga.
- Quem olhar para a esquina (variável) agora verá um nome novo, mas a placa antiga nunca deixou de dizer o que dizia até ser removida.

## **

* * *

<br>
Diferença entre Biblioteca e API**

- **Biblioteca:** É um código pré-pronto que você "baixa" para dentro do seu projeto. O seu computador é quem faz o trabalho duro.
    - _Exemplo:_ Biblioteca de PDF no Python. Você usa o **seu** processador para gerar o arquivo. É como ter a ferramenta na sua maleta.
- **API (Serviço Externo):** É uma interface que permite que o seu código "converse" com o sistema de outra pessoa ou empresa. O trabalho duro é feito no servidor deles, e você só recebe o resultado.
    - _Exemplo:_ API de Clima ou Banco de Dados na nuvem. Você pede a informação via internet, o servidor deles processa e te envia a resposta. É como contratar um serviço especializado por telefone.

* * *

O `finally` é um bloco opcional que vem depois do `try-catch`. A principal regra dele é: **ele sempre será executado**, independentemente de o código ter funcionado perfeitamente ou ter dado erro.

**Para que serve?**

1. **Evitar Repetição:** Você não precisa escrever o mesmo código de "finalização" dentro do `try` e do `catch`.
2. **Segurança (Limpeza):** É o lugar ideal para fechar conexões que não podem ficar abertas, como:
    - Conexão com o **Banco de Dados** do seu estoque.
    - Arquivos de **Excel/PDF** que o sistema estava lendo.
    - Liberação de memória.

**Exemplo Prático (Mental):** Imagine que você abre a porta do armazém do Sorter (**try**).

- Se você achar a peça (**sucesso**) ou se não achar (**catch**), você **PRECISA** trancar a porta antes de ir embora.
- Esse ato de "trancar a porta" é o seu **finally**.

```java
try {
metodoQuePodeLancarExcecao();
System.out.println("Executou");

System.out.println("Finalizou!");
} catch (Exception e) {
System.out.println("Deu erro!");

System.out.println("Finalizou!");
}
```

**

* * *

<br>
CTRL + ALT + I  - Deixa o Código mais limpo**

**

* * *

<br>
**

```java
  FileWriter escrita = new FileWriter(”Filmes.txt”);
  escrita.write(meuTitulo.toString()):
  escrita.close();

```

**<br>
**

## **Pacote** `**java.io**`**: Entrada e Saída de Dados**

**O** `**java.io**` **é o sistema de logística do Java. Ele decide como a informação entra (Input) e como ela sai (Output) do seu programa.**

#### **1\. A Classe** `**File**` **(O Endereço/Etiqueta)**

**Ela não é o arquivo em si, mas a** **referência** **a ele.**

- **O que faz:** **Verifica se o arquivo existe, cria pastas (**`**mkdir**`**) ou deleta arquivos.**
- **Analogia:** **É a** **etiqueta de identificação** **de uma caixa no estoque. A etiqueta diz onde a caixa está (C:\\estoque\\motores.txt), mas não é o que tem dentro da caixa.**

#### **2\.** `**FileReader**` **e** `**FileWriter**` **(O Mensageiro Lento)**

**Usados para ler e escrever arquivos de texto,** **caractere por caractere****.**

- **Analogia:** **Imagine um funcionário que leva** **uma peça por vez** **do almoxarifado para a bancada. Ele vai e volta centenas de vezes. Funciona, mas cansa e demora.**

#### **3\.** `**BufferedReader**` **e** `**BufferedWriter**` **(O Carrinho de Transporte)**

**Eles usam um** **Buffer** **(uma memória temporária) para ler/escrever linhas inteiras de uma vez.**

- **Analogia:** **É o funcionário que usa um** **carrinho de mão****. Em vez de ir e voltar para cada parafuso, ele enche o carrinho (Buffer) e leva tudo de uma vez.** **É muito mais rápido e eficiente.** **No seu projeto, use sempre esses aqui para ler listas de peças.**

#### **4\.** `**FileInputStream**` **e** `**FileOutputStream**` **(Cargas Especiais)**

**Usados para dados binários (fotos, áudios, PDFs).**

- **Analogia:** **É o transporte de** **produtos líquidos ou químicos****. Você não consegue ler "letra por letra", você precisa de uma tubulação específica (Stream) para mover essa carga bruta de um lado para o outro.**

#### **5\.** `**ObjectInputStream**` **e** `**ObjectOutputStream**` **(Teletransporte)**

**Servem para salvar um** **Objeto Java inteiro** **(como o seu Record de Peça) direto em um arquivo e recuperá-lo depois.**

- **Analogia:** **É como tirar uma** **foto 3D da peça** **e depois materializá-la de novo exatamente como ela estava. Você salva o "estado" do objeto.**

* * *

## **💡 Aplicação Real no seu Sistema do Sorter:**

- `**File**`**:** **Você vai usar para conferir se o arquivo** `**estoque_sorter.txt**` **já existe no PC da manutenção.**
- `**BufferedWriter**`**:** **Você vai usar para salvar cada nova peça que seu amigo da automação cadastrar, escrevendo uma linha para cada item.**
- `**BufferedReader**`**:** **Quando você abrir o programa, ele vai ler esse arquivo linha por linha e carregar tudo na sua** `**List<Material>**`**.**

* * *

## **Lendo Arquivos com a Classe** `**Scanner**`

**Enquanto o** `**FileReader**` **lê caracteres "crus", o** `**Scanner**` **é uma ferramenta mais inteligente que consegue quebrar o texto em partes (linhas, números, palavras).**

#### **1\. O Funcionamento do** `**Scanner**` **(O Leitor de Código de Barras)**

**Para ler um arquivo, você entrega um objeto** `**File**` **(o endereço) para o** `**Scanner**`**. Ele então percorre o arquivo linha por linha.**

- `**hasNextLine()**`**:** **Pergunta: "Ainda tem linha para ler?". Retorna verdadeiro ou falso.**
- `**nextLine()**`**:** **É o comando de: "Pule para a próxima linha e me dê o texto que está nela".**

#### **2\. Analogia: O Conferente de Estoque**

**Imagine que você tem uma lista de peças impressa num papel (****o arquivo****).**

- **O** `**File**`**:** **É a folha de papel na prancheta.**
- **O** `**Scanner**`**:** **É o** **conferente** **(você).**
- `**hasNextLine()**`**:** **É você olhando para a folha e vendo que ainda não chegou no fim da página.**
- `**nextLine()**`**:** **É você lendo a linha atual do motor, anotando mentalmente e descendo o dedo para a próxima linha.**

#### **3\. O** `**try-catch**` **Obrigatório (FileNotFoundException)**

**O Java é** **realista****: ele sabe que o arquivo pode ter sido deletado, renomeado ou estar em outro setor. Por isso, ele te obriga a tratar o erro:**

- `**try**`**:** **"Tente ler o arquivo** `**estoque.json**`**".**
- `**catch**`**:** **"Se o arquivo sumiu, avise ao usuário: 'Arquivo não encontrado!' em vez de travar o programa".**

* * *

## **Por que usar** `**Scanner**` **no seu Projeto do Sorter?**

1. **Versatilidade:** **Você usa a mesma ferramenta para ler o que o seu amigo digita no teclado (**`**System.in**`**) e para ler o arquivo onde as peças estão salvas.**
2. **Facilidade:** **No seu sistema, cada linha do arquivo pode ser uma peça. Com o** `**Scanner**`**, você lê a linha inteira, quebra as informações e transforma no seu** **Record de Material****.**

> **Dica de Ouro:** **Sempre dê o** `**scanner.close()**` **ao terminar. É como devolver a prancheta para o lugar; se você ficar com ela na mão, ninguém mais consegue ler a lista.**

<br>

<br>