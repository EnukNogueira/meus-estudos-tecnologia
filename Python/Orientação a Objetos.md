## Orientação a Objetos

### **`class` (A Classe)**

- **O que é:** O **Diagrama Unifilar** ou o Projeto de Engenharia.
- **Analogia:** É o desenho técnico no papel. Ele diz que o painel precisa de barramento, disjuntor e etiqueta, mas ele sozinho não conduz corrente. É apenas a **instrução** de montagem.

### **Instanciação (O Objeto)**

- **O que é:** `restaurante_praca = Restaurante(...)`
- **Analogia:** É o **Painel Montado** e parafusado na parede da fábrica. Agora ele existe fisicamente, ocupa espaço (memória) e pode ser ligado/desligado.

* * *

## 2\. A Engenharia Interna (Métodos Mágicos)

### **`def __init__(self, ...)` (O Construtor)**

- **O que é:** O momento da montagem na bancada.
- **`self` (O Chassi):** É o próprio corpo do equipamento. Garante que as peças da "Pizzaria" não sejam misturadas com as do "Restaurante".
- **Parâmetros:** São os componentes (disjuntores, contatores) que você traz do almoxarifado para instalar no chassi.
- **Analogia:** É o ato de parafusar os componentes no trilho DIN. O `self` garante que cada parafuso vá para o trilho certo.

### **`def __str__(self)` (A Placa de Identificação)**

- **O que é:** Como o objeto se apresenta para humanos.
- **Analogia:** É aquela **plaqueta de acrílico ou metal** na porta do painel. Em vez de ler o número de série complexo da memória, você lê: _"Painel de Comando - Setor de Bombas"_.

* * *

## 3\. Comandos de Manutenção e Controle

### **`@property` (O Multímetro Inteligente)**

- **O que é:** Um método que se comporta como uma variável.
- **Analogia:** É um **Voltímetro Digital** embutido na porta. Ele lê a "sujeira" dos sinais internos (`True/False`) e te entrega uma leitura limpa e interpretada ("Ativo" ou "Inativo").

### **`@classmethod` e `cls` (O Supervisor da Planta)**

- **O que é:** Um comando que olha para a fábrica inteira, não para um disjuntor só.
- **O parâmetro `cls`:** É o acesso ao banco de dados de todos os projetos daquela linha.
- **Analogia:** É o **Inventário Técnico**. Você não pergunta para uma lâmpada "quantas lâmpadas existem na rede?". Você consulta o **Mapa Geral da Rede** (`cls.restaurantes`).

* * *

## 4\. Segurança e Boas Práticas (Encapsulamento)

### **O Underline (`_nome`, `_ativo`)**

- **O que é:** Atributo Protegido.
- **Analogia:** É a **Proteção de Policarbonato** (Acrílico) sobre os barramentos energizados. Você consegue ver o que tem ali, mas o "underline" avisa: _"Não toque direto aqui sem o procedimento correto (método)"_.

### **Inversão de Estado (`not`)**

- **O que faz:** `self._ativo = not self._ativo`
- **Analogia:** É uma **Chave Seletora de 2 Posições**. Você não precisa saber se está ligado para desligar; você apenas bate a chave para a posição oposta.

* * *

##  Resumo de Conversão (Java x Python)

|     |     |     |
| --- | --- | --- |
| **Característica** | **No Java (Burocrático)** | **No Python (Prático)** |
| **Construtor** | `public NomeDaClasse()` | `def __init__(self)` |
| **Referência Interna** | `this` | `self` |
| **Impressão de Texto** | `toString()` | `__str__` |
| **Método Global** | `static` | `@classmethod` |
| **Acesso a Dados** | `getters / setters` | `@property` |

<br>

`From modelos.restaurante import Restaurante`

<br>

Usamos o From para importas arquivos, similar ao java para deixar os arquivos separados e mais organizados, deixando o código limpo

<br>

# FastAPI

### 1\. A Filosofia do FastAPI

O criador, Sebastián Ramírez, queria unir o melhor de vários mundos. O resultado é um framework que foca em:

- **Alta Performance:** No nível de NodeJS e Go.
- **Velocidade de Escrita:** Você desenvolve entre 200% a 300% mais rápido.
- **Menos Erros:** O uso de _Type Hints_ (tipagem) ajuda a IA e o VS Code a te avisarem do erro antes de você rodar.

### 2\. O "Esquema Elétrico" (Instalação)

O artigo reforça a importância do ambiente isolado (o que a gente sempre comenta sobre não bagunçar o sistema global):

1. **Venv:** `python3 -m venv .venv` (Criar a zona de trabalho).
2. **Instalação:** `pip install fastapi` e `pip install "uvicorn[standard]"` (O motor do servidor).

### 3\. Código Base (O "Hello World")

Ele mostra a estrutura mínima que você já conhece:

- Importar o `FastAPI`.
- Criar a instância `app`.
- Usar o **Decorador** `@app.get("/")` (que define a rota).
- Uma função simples que retorna um dicionário (que o FastAPI converte automaticamente para **JSON**).

### 4\. O Diferencial: Documentação Automática

O artigo destaca que, ao rodar o servidor, você ganha dois painéis de controle "de graça":

- **/docs (Swagger UI):** Para testar os endpoints interativamente.
- **/redoc:** Uma documentação mais limpa e organizada para leitura.

<br>

Dicionario: Os dicionários são úteis para armazenar e acessar dados de maneira organizada e rápida. Eles são um tipo de conjunto de elementos em Python, pois armazenam uma coleção de itens.

testes: { “matricula” 25}

#### [`pop()`](https://www.google.com/url?q=https%3A%2F%2Fpython-reference.readthedocs.io%2Fen%2Flatest%2Fdocs%2Fdict%2Fpop.html)

Remove um item de um dicionário e o retorna.

#### [`items()`](https://www.google.com/url?q=https%3A%2F%2Fpython-reference.readthedocs.io%2Fen%2Flatest%2Fdocs%2Fdict%2Fitems.html)

Retorna uma lista de pares chave-valor do dicionário.

#### [`keys()`](https://www.google.com/url?q=https%3A%2F%2Fpython-reference.readthedocs.io%2Fen%2Flatest%2Fdocs%2Fdict%2Fkeys.html)

Retorna uma lista das chaves do dicionário.

#### [`values()`](https://www.google.com/url?q=https%3A%2F%2Fpython-reference.readthedocs.io%2Fen%2Flatest%2Fdocs%2Fdict%2Fvalues.html)

Retorna uma lista dos valores do dicionário.