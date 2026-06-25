## Terceiro Curso Java  

Construtores são métodos especiais em uma classe que são chamados quando um objeto dessa classe é criado. O principal objetivo de um construtor é inicializar os atributos do objeto, ou seja, atribuir valores iniciais a eles.

Em Java, um construtor tem o mesmo nome da classe e não possui um tipo de retorno, nem mesmo `void`. Você pode ter mais de um construtor em uma classe, o que é conhecido como sobrecarga de construtores. Isso permite que você crie objetos de diferentes maneiras, dependendo dos parâmetros que você deseja passar.

Por exemplo, no contexto da aula que estamos estudando, temos os construtores nas classes `Filme` e `Serie`, que herdam da classe `Titulo`. Esses construtores são usados para garantir que, ao criar um novo objeto, você forneça informações essenciais, como o nome e o ano de lançamento.

Resumindo, ele atribui os valores iniciais do objeto. Mas por que ele faz isso? Para deixar o código mais limpo e fácil de entender como por exemplo:

<br>

1. **Inicialização Clara**: Os construtores permitem que você inicialize os atributos de um objeto de forma clara e concisa no momento da criação. Isso evita a necessidade de chamadas separadas para métodos de configuração, como `setNome()` ou `setAnoDeLancamento()`, tornando o código mais direto.
2. **Obrigatoriedade de Dados**: Ao definir parâmetros obrigatórios no construtor, você garante que um objeto não será criado sem informações essenciais. Isso ajuda a evitar erros e inconsistências no estado do objeto.
3. **Sobrecarga**: Com a sobrecarga de construtores, você pode oferecer diferentes maneiras de criar um objeto, dependendo das necessidades do contexto. Isso proporciona flexibilidade e clareza sobre quais dados são necessários em cada situação.
4. **Encapsulamento**: Os construtores ajudam a encapsular a lógica de inicialização, permitindo que você mantenha a lógica de criação de objetos em um único lugar, o que facilita a manutenção e a leitura do código.
5. **Validações**: Você pode incluir validações diretamente no construtor, garantindo que os dados fornecidos estejam corretos antes que o objeto seja criado.

### <br>

###  Analogia envolvendo Elétrica:

Imagine que você tem uma classe chamada `PainelEletrico`. Você não quer criar um painel "vazio" que não serve para nada. Você quer que, no momento da criação, ele já receba as informações principais.

Java

<br>

```
public class PainelEletrico {
    String localizacao;
    int voltagem;

    // ISSO É O CONSTRUTOR
    public PainelEletrico(String localizacao, int voltagem) {
        this.localizacao = localizacao;
        this.voltagem = voltagem;
        System.out.println("Painel instalado com sucesso em: " + localizacao);
    }
}

```

### Por que isso é importante para você?

1. **Segurança dos Dados:** Assim como você não liga um motor sem saber a voltagem, o construtor garante que o seu objeto Java não comece a rodar "sem rumo". Ele te obriga a passar os dados necessários.
2. **Organização:** Lembra que você achou o Java extenso? O construtor ajuda a resumir. Em vez de criar o objeto e depois dar 10 comandos para preencher os dados, você faz tudo em uma linha só:
    - `PainelEletrico p1 = new PainelEletrico("Galpão A", 380);`

#### <br>

#### Quando usar o SUPER?

1. **Sempre que a classe Pai não tiver um construtor vazio:** Se o "Pai" exige uma informação (como a marca) para nascer, o "Filho" é obrigado a passar essa informação via `super()`.
2. **Na primeira linha do construtor:** O Java exige que o `super()` seja a primeira coisa a ser feita. Você não pode instalar a fiação do disjuntor antes de ter a base do componente montada.

### Exemplo:

```
// Classe Pai (O projeto geral)
class Componente {
    String marca;

    Componente(String marca) {
        this.marca = marca;
    }
}

// Classe Filha (O item específico)
class Disjuntor extends Componente {
    int amperagem;

    Disjuntor(String marca, int amperagem) {
        super(marca); // <--- OBRIGATÓRIO! Chama o construtor do Pai primeiro.
        this.amperagem = amperagem; // Depois configura o que é específico do disjuntor.
    }
}
```

Se você não colocar o `super()`, o Java vai tentar chamar um construtor vazio no Pai automaticamente. Se o Pai não tiver um (porque você criou um construtor com parâmetros), o código **não compila**. É como tentar ligar um motor 380V em uma rede que exige uma chave de partida específica que você "esqueceu" de acionar.

<br>

### Analogia Checklist de Segurança

  Pensa no construtor como o **Checklist de Partida** de uma máquina industrial:

- **Sem Construtor:** É como tentar ligar a máquina e depois sair correndo para ver se tem óleo, se a fase está certa e se o botão de emergência está destravado. O risco de quebra é alto.
- **Com Construtor:** A máquina **só aceita o comando de ligar** se você já informou o óleo, a fase e o status do botão no momento do "start". Se faltar um dado, ela nem tenta girar o motor.

<br>

## 1\. Polimorfismo no Barramento (`ArrayList<Titulo>`)

- **O que é:** Criar uma lista do tipo "Pai" (`Titulo`) que aceita qualquer "Filho" (`Filme` ou `Serie`).
- **Por que importa:** Isso torna seu código **escalável**. Se amanhã você criar uma classe `Documentario`, não precisará mudar nada na lista; ela já está preparada para receber qualquer coisa que herde de `Titulo`.

## 2\. O Poder do Construtor

- **O que é:** `new Filme("Nome", Ano)`.
- **Por que importa:** Garante que o objeto nasça "energizado". Evita que você crie um filme sem nome ou sem ano, o que causaria erros (bugs) em outras partes do sistema. É o seu **checklist de segurança** na partida do motor.

## 3\. A palavra-chave `var` 

- **O que é:** `var filme = new Filme(...)`.
- **Por que importa:** Deixa o código mais limpo. O Java olha para o lado direito e já sabe qual é o tipo do lado esquerdo. Menos texto, mesma segurança.

## 4\. Inspeção de Tipo (`instanceof`)

- **O que é:** `item instanceof Filme filme`.
- **Por que importa:** É o seu "multímetro". Antes de tentar acessar um método que só existe em `Filme`, você testa se o objeto realmente é um filme. Se for, ele faz o **Casting** (converte o tipo) automaticamente para você usar.

## 5\. Iteração Inteligente (`for-each`)

- **O que é:** `for(Titulo item : lista)`.
- **Por que importa:** É a forma mais segura e limpa de percorrer todos os componentes do seu sistema de uma vez, sem precisar controlar índices manuais (como o antigo `i++`).

<br>

## Diferença entre comparable e comparador

## 1\. O Problema

Ao tentar usar o método `Collections.sort(lista)` em uma lista de objetos personalizados (como uma lista de "Contas"), o Java não sabe qual critério usar para ordenar (se é pelo número, pelo nome do titular, etc.). Por isso, o código nem compila se você não definir uma regra.

## 2\. Comparable (Ordem Natural)

- **O que é:** É usado para definir a "ordem padrão" de um objeto.
- **Como funciona:** A sua classe (ex: `Conta`) deve implementar a interface `Comparable` e o método `compareTo`.
- **Lógica:** \* Retorna um número **negativo** se o objeto atual deve vir antes.
    - Retorna **zero** se forem iguais.
    - Retorna um número **positivo** se o objeto atual deve vir depois.
- **Uso:** Após implementar, basta chamar `Collections.sort(lista)`.

## 3\. Comparator (Ordens Alternativas)

- **O que é:** É usado quando você quer ordenar de uma forma diferente da padrão (ex: a ordem natural é pelo número, mas você quer ordenar pelo nome do titular) ou quando não pode modificar a classe original.
- **Como funciona:** Você cria uma classe separada que implementa a interface `Comparator` e o método `compare(objeto1, objeto2)`.
- **Uso:** Você passa esse comparador como um segundo argumento: `Collections.sort(lista, novoMeuComparator())`.

## Pontos Importantes:

- **Consistência:** O resultado do método de comparação deve ser consistente com o método `.equals()` da classe (se dois objetos são iguais no `equals`, a comparação deve retornar zero).
- **Java Moderno:** O artigo menciona que, a partir do Java 8, essas implementações ficaram muito mais simples usando **Expressões Lambda**, o que evita a necessidade de criar várias classes separadas apenas para comparação.

**Em resumo:** Use `Comparable` para a regra de ordenação que mais faz sentido para aquele objeto e `Comparator` para todas as outras variações que você precisar.

<br>

<br>

<br>

<br>

<br>