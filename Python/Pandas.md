# Pandas

###### Asimov Academy

Para utilizar a biblioteca utilize o seguinte código:

```python
import numpy as np
import pandas as pd
```

Como fazer faturamento com a biblioteca pandas? 

```python
df_data.groupby("City")["Total"].sum()
```

O que isso significa? 

- `df.data` Significa: é um **DataFrame** (um objeto do Pandas que funciona como uma tabela de Excel na memória do seu computador). 
- `groupby` Significa: _Pegue a tabela e junte todas as linhas que possuem a mesma cidade_. Ele separa os dados em grupos invisíveis baseados na coluna `"City"`.
- `["Total"]` Significa: _Olhando para cada grupo de cidades, foque apenas na coluna chamada 'Total'_ (que provavelmente contém os valores das vendas/faturamento).e o método 
- `.sum()` Significa: _Some todos os valores da coluna 'Total' dentro de cada grupo_.

> Analogia Prática: Gerente de Vendas

Imagine que você está na sua mesa com um relatório impresso de todas as vendas da empresa. O relatório tem as colunas: **Cidade**, **Produto** e **Total** (valor pago).  
Para calcular o faturamento por cidade manualmente, você faria exatamente o que o código faz:  

- **`df_data`:** Você olha para o relatório completo.
- **`.groupby("City")`:** Você separa as folhas do relatório em pilhas na sua mesa. Uma pilha só com folhas de "Guarulhos", outra pilha só com folhas de "Curitiba", e assim por diante.
- **`["Total"]`:** Em cada pilha, você passa o dedo apenas na coluna onde está escrito o valor final de cada venda.
- **`.sum()`:** Você pega a calculadora, soma os valores daquela coluna para a pilha de "Guarulhos", anota o resultado, e depois faz o mesmo para a pilha de "Curitiba".

## Questões

Exemplo 1: 

Qual a percentual de participação na receita de cada tipo de produto?

```python
(df_data.groupby("Product line")["Total"].sum() / df_data.groupby("Product line")["Total"].sum().sum()).sort_values() * 100
```

O que isso significa?

`.sort_values()` Significa: Vai ordenar o valor do menor para o maior

`* 100⁠`  Significa: Irá multiplicar o valor por 100 para ter um valor percentual.

Exemplo 2:

Como está distribuído o tipo de produto consumido por gênero?

```
(df_data.groupby(["Product line","Gender"])[["Total"]].sum().pivot_table(index="Product line",columns="Gender")
```

O que isso significa?

`.pivot_table` Significa: transforma linhas repetitivas em uma matriz organizada, onde os gêneros viram colunas lado a lado, facilitando a comparação direta de quem consome o quê.

Exemplo 3:

Qual foi o faturamento por mês?

```
df_data["Date"] = pd.to_datetime(df_data["Date"])
df_data["Month"] = df_data["Date"].apply(lambda x: x.month)
df_data["Year"] = df_data["Date"].apply(lambda x: x.year)
df_data.groupby(["Month"])["Total"].sum()

```

O que isso significa?

`.apply(lambda x: x.month)` Significa: Irá extrair apenas o mês 

`pd.to_datetime` Significa: Converte o texto da coluna "Date" em um formato de data real que o Python entenda. Se a data for tratada como texto (String), o Python não consegue extrair o mês ou o ano.

Exemplo 4:

Qual foi o faturamento em Janeiro de 2019?

```python
df_data[(df_data["Year"] ==2019) & (df_data["Month"] == 1)]["Rating"].mean()
df_data.groupby(["Month"])["Total"].sum()
```

O que isso significa?

Isso é um **filtro composto** (usando o `&` que significa "E"). Ele isola na memória apenas as vendas que aconteceram simultaneamente no ano de 2019 e no mês 1 (Janeiro)

`.mean()` Significa: Média dos dados

Exemplo 5:

Como  se distribui o gasto por tipo de consumidor em cada filial?

```
df_data.groupby(["Customer type","City"])["Total"].sum()
```

labels(ingles) = lista(Português)

`index` = Índice

`columns` = colunas

`axis = 1 ou 0`  = eixo 1 corresponde a colunas e eixo 0 corresponde a linhas

<br>

O `np.array` é a estrutura de dados fundamental da biblioteca **NumPy** (Numerical Python). Na prática, ele cria uma matriz ou um vetor (uma lista de dados) de alta performance. O `np.array` exige uma regra rígida: **todos os elementos ali dentro precisam ser do mesmo tipo técnico** (tudo `int`, tudo `float`, etc.). Como o tipo é fixo, o NumPy aloca esses dados em blocos de memória **contíguos**  

### **Como criar uma Serie?** 

```python
import pandas as pd
import numpy as np
labels = ['a','b','c']
minha_lista = [10,20,30]
arr = np.array([10,20,30])
d = {'a':10,'b':20,'c':30}
```

Usando listas

```python
pd.Series(data=minha_lista,index=labels)
```

Como aprendido anteriormente para chamar a biblioteca simplificada usamos o método pd ou np que foi o que definimos.

### **Usando um Índice**

A chave para usar uma Serie é entender seu índice. O Pandas faz uso desses nomes ou números de índice, permitindo pesquisas rápidas de informações (funciona como uma tabela de hash ou dicionário).

Vamos ver alguns exemplos de como pegar informações de uma Serie. Vamos criar duas Series, ser1 e ser2:

```python
ser1 = pd.Series([1,2,3,4],index = ['EUA', 'Alemanha','USSR', 'Japão'])                    
ser2 = pd.Series([1,2,5,4],index = ['EUA', 'Alemanha','Italia', 'Japão']) 
```

```python
ser2['EUA']

```

A seleção do valor(1) é feita por colchetes passando essa string(’EUA’)

```python
ser1 + ser2
```

 Também pode somar as tabelas por exemplo:

```python
Alemanha    4.0
EUA         2.0
Italia      NaN
Japão       8.0
USSR        NaN
dtype: float64      
```

Ela irá somar os valores iguais e quando não tiver valores de indices iguais ela irá escrever `NaN.` Falando que não encontrou valores.                         

## **DataFrames**

DataFrame é o elemento mais importante dos Pandas e são diretamente inspirados pela linguagem de programação R. Podemos pensar em um DataFrame como um monte de objetos da série juntos para compartilhar o mesmo índice. Vamos usar Pandas para explorar esse tópico.

```python
import pandas as pd
import numpy as np
```

`NumPy` é uma biblioteca para algebra linear e algumas operações matemáticas.

`import randn` gera alguns números aleatórios.

```python
from numpy.random import randn
np.random.seed(101)
```

```python
df = pd.DataFrame(randn(5,4),index=['A B C D E'].split(),columns='W X Y Z'.split())
print(df)
```

| <br> | W   | X   | Y   | Z   |
| --- | --- | --- | --- | --- |
| A   | 2.706850 | 0.628133 | 0.907969 | 0.503826 |
| B   | 0.651118 | \-0.319318 | \-0.848077 | 0.605965 |
| C   | \-2.018168 | 0.740122 | 0.528813 | \-0.589001 |
| D   | 0.188695 | \-0.758872 | \-0.933237 | 0.955057 |
| E   | 0.190794 | 1.978757 | 2.605967 | 0.683509 |

## **Seleção e indexação**

Vamos aprender os vários métodos para pegar dados de um DataFrame

```python
  df['W']
```

```python
A    2.706850
B    0.651118
C   -2.018168
D    0.188695
E    0.190794
Name: W, dtype: float64
```

Como pode ver acima é assim que vamos puxar dados específicos da coluna

Passando uma lista com nomes das colunas

```python
df[['W','Z']]
```

<br>

| <br> | W   | Z   |
| --- | --- | --- |
| A   | 2.706850 | 0.503826 |
| B   | 0.651118 | 0.605965 |
| C   | \-2.018168 | \-0.589001 |
| D   | 0.188695 | 0.955057 |
| E   | 0.190794 | 0.683509 |

Criando uma coluna:

```python
df['new'] = df['W'] + df['Y']
print(df)
```

| <br> | W   | X   | Y   | Z   | new |
| --- | --- | --- | --- | --- | --- |
| A   | 2.706850 | 0.628133 | 0.907969 | 0.503826 | 3.614819 |
| B   | 0.651118 | \-0.319318 | \-0.848077 | 0.605965 | \-0.196959 |
| C   | \-2.018168 | 0.740122 | 0.528813 | \-0.589001 | \-1.489355 |
| D   | 0.188695 | \-0.758872 | \-0.933237 | 0.955057 | \-0.744542 |
| E   | 0.190794 | 1.978757 | 2.605967 | 0.683509 | 2.796762 |

Removendo colunas:

```python
df.drop('new',axis=1,inplace=True)
```

| <br> | W   | X   | Y   | Z   |
| --- | --- | --- | --- | --- |
| A   | 2.706850 | 0.628133 | 0.907969 | 0.503826 |
| B   | 0.651118 | \-0.319318 | \-0.848077 | 0.605965 |
| C   | \-2.018168 | 0.740122 | 0.528813 | \-0.589001 |
| D   | 0.188695 | \-0.758872 | \-0.933237 | 0.955057 |
| E   | 0.190794 | 1.978757 | 2.605967 | 0.683509 |

O `inplace` faz com que fique salvo essa modificação. Quando voce escreve 

`df.drop('new',axis=1)` ele altera somente ali na hora. quando voce usa o ('new',axis=1,inplace=True) ele salva essa remoção que você fez no código

Exemplo de como remover linhas agora:

```python
df.drop('E',axis=0)
```

| <br> | W   | X   | Y   | Z   |
| --- | --- | --- | --- | --- |
| A   | 2.706850 | 0.628133 | 0.907969 | 0.503826 |
| B   | 0.651118 | \-0.319318 | \-0.848077 | 0.605965 |
| C   | \-2.018168 | 0.740122 | 0.528813 | \-0.589001 |
| D   | 0.188695 | \-0.758872 | \-0.933237 | 0.955057 |

Selecionando linhas:

```python
df.loc['A']
```

```python
W    2.706850
X    0.628133
Y    0.907969
Z    0.503826
Name: A, dtype: float64
```

```python
df.loc [['A', 'B'], ['W']] 
```

<br>

ao utilizar o `loc` ele passa a se referir pelos indices, ao utilizar , depois do \] o loc passa a se referir pelas colunas com isso você consegue atribuir o valor de terminado da coluna e do índice selecionado.

| <br> | W   | Y   |
| --- | --- | --- |
| A   | 2.706850 | 0.907969 |
| B   | 0.651118 | \-0.848077 |

ao utilizar o `iloc` você passa a se referir por sessões numéricas.

```python
df.iloc[:-1 ,1:4]
```

o `:` se refere a selecionar todas as colunas o `-1` significa que voce irá remover a ultima coluna mas também podemos utilizar `:4` para selecionar apenas 4 ao invés de `-1`. `1:4` tudo que está antes dos `:` será incluso na linha de índice 1 e o 4 irá excluir esse ultimo valor.

## Filtros

Para fazer filtros usamos a seguinte função:

```python
df[df>0]
```

| <br> | W   | X   | Y   | Z   |
| --- | --- | --- | --- | --- |
| A   | 2.706850 | 0.628133 | 0.907969 | 0.503826 |
| B   | 0.651118 | NaN | NaN | 0.605965 |
| C   | NaN | 0.740122 | 0.528813 | NaN |
| D   | 0.188695 | NaN | NaN | 0.955057 |
| E   | 0.190794 | 1.978757 | 2.605967 | 0.683509 |

Nota-se que todos os números maiores que foram puxados para a tabela porem os menores que 0 foram removidos.

```python
df[df['W']>0]
```

| W   | X   | Y   | Z   | <br> |
| --- | --- | --- | --- | --- |
| A   | 2.706850 | 0.628133 | 0.907969 | 0.503826 |
| B   | 0.651118 | \-0.319318 | \-0.848077 | 0.605965 |
| D   | 0.188695 | \-0.758872 | \-0.933237 | 0.955057 |
| E   | 0.190794 | 1.978757 | 2.605967 | 0.683509 |

## **Mais Detalhes do Índice**

| <br> | **W** | **X** | **Y** | **Z** |
| --- | --- | --- | --- | --- |
| **A** | **2.706850** | **0.628133** | **0.907969** | **0.503826** |
| **B** | **0.651118** | **\-0.319318** | **\-0.848077** | **0.605965** |
| **C** | **\-2.018168** | **0.740122** | **0.528813** | **\-0.589001** |
| **D** | **0.188695** | **\-0.758872** | **\-0.933237** | **0.955057** |
| **E** | **0.190794** | **1.978757** | **2.605967** | **0.683509** |

### **Resetando o índice:**

```python
df.reset_index()
```

| **index** | **W** | **X** | **Y** | **Z** | <br> |
| --- | --- | --- | --- | --- | --- |
| **0** | **A** | **2.706850** | **0.628133** | **0.907969** | **0.503826** |
| **1** | **B** | **0.651118** | **\-0.319318** | **\-0.848077** | **0.605965** |
| **2** | **C** | **\-2.018168** | **0.740122** | **0.528813** | **\-0.589001** |
| **3** | **D** | **0.188695** | **\-0.758872** | **\-0.933237** | **0.955057** |
| **4** | **E** | **0.190794** | **1.978757** | **2.605967** | **0.683509** |

Nota-se que ao fazer esse comando foi criado uma nova coluna chamada index e numerados de 0 a 4 por conta do reinicio.

### **Adicionando novos indices:**

```python
df.set_index('Estados',inplace=True)
```

| W   | X   | Y   | Z   | <br> |
| --- | --- | --- | --- | --- |
| Estados | <br> | <br> | <br> | <br> |
| CA  | 2.706850 | 0.628133 | 0.907969 | 0.503826 |
| NY  | 0.651118 | \-0.319318 | \-0.848077 | 0.605965 |
| WY  | \-2.018168 | 0.740122 | 0.528813 | \-0.589001 |
| OR  | 0.188695 | \-0.758872 | \-0.933237 | 0.955057 |
| CO  | 0.190794 | 1.978757 | 2.605967 | 0.683509 |

## **Hierarquia de índices e índices múltiplos**

```python
outside = ['G1','G1','G1','G2','G2','G2']
inside = [1,2,3,1,2,3]
hier_index = list(zip(outside,inside))
hier_index = pd.MultiIndex.from_tuples(hier_index)

hier_index
```

Para explicar de uma forma simples, utilizando esse método ele irá encaixar as 2 listas em uma tupla por exemplo:

> MultiIndex (\[('G1', 1),  
>      ('G1', 2),  
>      ('G1', 3),  
>      ('G2', 1),  
>      ('G2', 2),  
>      ('G2', 3)\])

```python
df = pd.DataFrame(np.random.randn(6,2),index=hier_index,columns=['A','B'])
df
```

| <br> | <br> | A   | B   |
| --- | --- | --- | --- |
| G1  | 1   | 0.302665 | 1.693723 |
| 2   | \-1.706086 | \-1.159119 |
| 3   | \-0.134841 | 0.390528 |
| G2  | 1   | 0.166905 | 0.184502 |
| 2   | 0.807706 | 0.072960 |
| 3   | 0.638787 | 0.329646 |

Como indexar isso? Para a hierarquia de índice, usamos `df.loc []`. Se este fosse no eixo das colunas, você usaria a notação de suporte normal `df []`. Chamar um nível do índice retorna um sub-dataframe:

```python
df.loc['G1']
```

| <br> | A   | B   |
| --- | --- | --- |
| 1   | 0.302665 | 1.693723 |
| 2   | \-1.706086 | \-1.159119 |
| 3   | \-0.134841 | 0.390528 |

Utilizando o loc:

```python
df.loc['G1'].loc[1]
```

```python
A    0.302665
B    1.693723
Name: 1, dtype: float64
```

## **Dados ausentes**

```python
df = pd.DataFrame({'A': [1,2,np.nan],
                  'B': [5,np.nan,np.nan],
                  'C': [1,2,3]})
```

O `df.dropna()` é um dos métodos mais importantes e utilizados na biblioteca Pandas quando estamos na etapa de **higienização e tratamento de dados** (limpeza da base de dados).

Em bases de dados do mundo real, é extremamente comum haver falhas na recolha de informações. Isso resulta em linhas ou colunas vazias, que o Pandas identifica com a etiqueta `NaN` (_Not a Number_).

A função principal do `.dropna()` é eliminar as linhas ou colunas que contenham estes valores ausentes.

### Exemplo:

Imagina que tem um DataFrame chamado `df` com dados de vendas:

|     |     |     |
| --- | --- | --- |
| **Nome do Cliente** | **Produto** | **Total da Compra** |
| Enuk | Teclado | 500 |
| Nunukitu | Mouse | `NaN` _(Valor em falta)_ |
| `NaN` _(Sem nome)_ | Monitor | 1500 |

Se executar isso:

Python

```
df_limpo = df.dropna()

```

O Pandas vai analisar a tabela e **eliminar qualquer linha** que tenha pelo menos um valor `NaN`. O `df_limpo` ficaria apenas com a linha do Enuk, pois as linhas do nunukitu e a terceira tinham buracos.

### Como controlar a limpeza

O `.dropna()` é altamente configurável através de parâmetros.

1. **`axis` (Definir se elimina Linha ou Coluna):**
    - `axis=0` (Padrão): Elimina a **linha** inteira onde houver um `NaN`.
    - `axis=1`: Elimina a **coluna** inteira se houver algum `NaN` nela.
2. **`how` (A condição para eliminar):**
    - `how='any'` (Padrão): Se houver **pelo menos um** `NaN` na linha, elimina-a.
    - `how='all'`: Só elimina a linha se **todos** os valores daquela linha forem `NaN`. Útil para apagar linhas completamente em branco.
3. **`subset` (Foco num alvo específico):**
    - Se não quiser perder dados importantes, pode dizer ao Pandas para olhar apenas para uma coluna específica.
    - Exemplo: `df.dropna(subset=["Total da Compra"])` -> Só vai eliminar a linha se o valor em falta estiver na coluna do dinheiro. Se o nome do cliente faltar, mas o valor estiver lá, ele mantém a linha.
4. **`inplace` (Modificação direta ou cópia):**
    - `inplace=False` (Padrão): Devolve uma cópia da tabela limpa. A tabela original `df` continua intocada.
    - `inplace=True`: Altera diretamente o `df` original. Não precisa fazer a atribuição `df = df.dropna()`.

<br>

O parâmetro **`thresh`** (abreviação de _threshold_, ou "limiar" em inglês) é outra ferramenta do `.dropna()` que dá ainda mais precisão no tratamento de dados ausentes.

A melhor forma de entender o `thresh` é pensar nele como um **filtro de tolerância**.

Enquanto o `how='any'` é radical (apaga se houver um único `NaN`) e o `how='all'` é super tolerante (só apaga se tudo for `NaN`), o `thresh` permite-te definir o **número mínimo de dados válidos (não nulos)** que uma linha ou coluna precisa de ter para não ser descartada.

### Exemplo:

Imagina que vai analisar um dataset do Kaggle ou a estruturar o algum projeto do meu. Tem uma tabela onde cada linha deve ter **4 colunas** preenchidas.

Se definir `thresh=3`, está a dizendo ao Pandas: _"Só mantém a linha se ela tiver, pelo menos, 3 valores reais (válidos). Se tiver 2 ou mais `NaN`, pode deixar fora."_

Como:

Python

```
df_limpo = df.dropna(thresh=3)
```

<br>

O **`df.fillna()`** é o parceiro inseparável do `.dropna()`. Se o `.dropna()` é o comando radical que apaga os problemas, o `.fillna()` é a ferramenta da **recolha inteligente**, que serve para **preencher e substituir os valores em falta (`NaN`)** por algo que faça sentido para o teu negócio.

Na Engenharia de Dados, esta técnica chama-se **imputação de dados**. Em vez de destruir linhas inteiras e perder amostras preciosas, o panda salva o registo colocando um valor padrão no "buraco".

### Exemplo:

Imagina o mesmo relatório de vendas com falhas de preenchimento na coluna de preços e produtos:

|     |     |     |
| --- | --- | --- |
| **Nome do Cliente** | **Produto** | **Total da Compra** |
| Enuk | Teclado | 500 |
| Nunukitu | Mouse | `NaN` |
| Ana | `NaN` | 1500 |

#### 1\. Preenchimento Geral (Estratégia Simples)

Se quiser substituir **todos** os `NaN` da tabela inteira por um único valor fixo (por exemplo, zero):

Python

```
df_preenchido = df.fillna(0)

```

_Onde havia `NaN`, agora haverá `0`._

### Groupby

O método `groupby` permite agrupar linhas de dados em conjunto e chamar funções agregadas\]

```python
import pandas as pd
# Cria um DataFrame
data = {'Classe':['Júnior','Júnior','Pleno','Pleno','Sênior','Sênior'],
       'Nome':['Jorge','Carlos','Roberta','Patrícia','Bruno','Vera'],
       'Venda':[200,120,340,124,243,350]}
```

```python
df = pd.DataFrame(data)
```

| <br> | Empresa | Nome | Venda |
| --- | --- | --- | --- |
| 0   | GOOG | Sam | 200 |
| 1   | GOOG | Charlie | 120 |
| 2   | MSFT | Amy | 340 |
| 3   | MSFT | Vanessa | 124 |
| 4   | FB  | Carl | 243 |
| 5   | FB  | Sarah | 350 |

Esse gráfico é só um exemplo ele não segue o comando acima.

<br>

## Métodos para combinar DataFrame

**Exemplos de DataFrames:**

```python
import pandas as pd
df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                        'B': ['B0', 'B1', 'B2', 'B3'],
                        'C': ['C0', 'C1', 'C2', 'C3'],
                        'D': ['D0', 'D1', 'D2', 'D3']},
                        index=[0, 1, 2, 3])

df2 = pd.DataFrame({'A': ['A4', 'A5', 'A6', 'A7'],
                        'B': ['B4', 'B5', 'B6', 'B7'],
                        'C': ['C4', 'C5', 'C6', 'C7'],
                        'D': ['D4', 'D5', 'D6', 'D7']},
                         index=[4, 5, 6, 7])

df3 = pd.DataFrame({'A': ['A8', 'A9', 'A10', 'A11'],
                        'B': ['B8', 'B9', 'B10', 'B11'],
                        'C': ['C8', 'C9', 'C10', 'C11'],
                        'D': ['D8', 'D9', 'D10', 'D11']},
                        index=[8, 9, 10, 11])

```

```python
df1
```

| <br> | A   | B   | C   | D   |
| --- | --- | --- | --- | --- |
| 0   | A0  | B0  | C0  | D0  |
| 1   | A1  | B1  | C1  | D1  |
| 2   | A2  | B2  | C2  | D2  |
| 3   | A3  | B3  | C3  | D3  |

```python
df2
```

| <br> | A   | B   | C   | D   |
| --- | --- | --- | --- | --- |
| 4   | A4  | B4  | C4  | D4  |
| 5   | A5  | B5  | C5  | D5  |
| 6   | A6  | B6  | C6  | D6  |
| 7   | A7  | B7  | C7  | D7  |

```python
df3
```

| A   | B   | C   | D   | <br> |
| --- | --- | --- | --- | --- |
| 8   | A8  | B8  | C8  | D8  |
| 9   | A9  | B9  | C9  | D9  |
| 10  | A10 | B10 | C10 | D10 |
| 11  | A11 | B11 | C11 | D11 |

### **Concatenação**

**Concatenação basicamente cola DataFrames. Tenha em mente que as dimensões devem corresponder ao longo do eixo que você está concatenando. Basta usar** `**pd.concat**` **e passar uma lista de DataFrames para concatenar juntos(”Resumindo… o comando** `**pd.concat**` **junta os 3 dataframes que fiz anteriormente em somente um.)**

| **A** | **B** | **C** | **D** | <br> |
| --- | --- | --- | --- | --- |
| **0** | **A0** | **B0** | **C0** | **D0** |
| **1** | **A1** | **B1** | **C1** | **D1** |
| **2** | **A2** | **B2** | **C2** | **D2** |
| **3** | **A3** | **B3** | **C3** | **D3** |
| **4** | **A4** | **B4** | **C4** | **D4** |
| **5** | **A5** | **B5** | **C5** | **D5** |
| **6** | **A6** | **B6** | **C6** | **D6** |
| **7** | **A7** | **B7** | **C7** | **D7** |
| **8** | **A8** | **B8** | **C8** | **D8** |
| **9** | **A9** | **B9** | **C9** | **D9** |
| **10** | **A10** | **B10** | **C10** | **D10** |
| **11** | **A11** | **B11** | **C11** | **D11** |

Agora vou mostrar como ele se comporta com indices diferentes. Por que isso acontece? o **concat** espera que tem indices iguais e quando apresentamos diferentes a tabela fica do seguinte jeito:

```python
pd.concat([df1,df2,df3],axis=1)
```

| A   | B   | C   | D   | A   | B   | C   | D   | A   | B   | C   | D   | <br> |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | A0  | B0  | C0  | D0  | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 1   | A1  | B1  | C1  | D1  | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 2   | A2  | B2  | C2  | D2  | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 3   | A3  | B3  | C3  | D3  | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 4   | NaN | NaN | NaN | NaN | A4  | B4  | C4  | D4  | NaN | NaN | NaN | NaN |
| 5   | NaN | NaN | NaN | NaN | A5  | B5  | C5  | D5  | NaN | NaN | NaN | NaN |
| 6   | NaN | NaN | NaN | NaN | A6  | B6  | C6  | D6  | NaN | NaN | NaN | NaN |
| 7   | NaN | NaN | NaN | NaN | A7  | B7  | C7  | D7  | NaN | NaN | NaN | NaN |
| 8   | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | A8  | B8  | C8  | D8  |
| 9   | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | A9  | B9  | C9  | D9  |
| 10  | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | A10 | B10 | C10 | D10 |
| 11  | NaN | NaN | NaN | NaN | NaN | NaN | NaN | NaN | A11 | B11 | C11 | D11 |

Se os datas frames compartilham o mesmo tipo de colunas você irá utilizar o `axis=0` se compartilha o mesmo tipo de indice`axis=1`

### **Outros DataFrames:**

```python
esquerda = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                     'A': ['A0', 'A1', 'A2', 'A3'],
                     'B': ['B0', 'B1', 'B2', 'B3']})
   
direita = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                          'C': ['C0', 'C1', 'C2', 'C3'],
                          'D': ['D0', 'D1', 'D2', 'D3']})
```

### **Mesclar**

A função mesclar  permite que você mescle os quadros de dados juntos usando uma lógica semelhante à mesclagem de tabelas SQL juntas. Exemplo:

```python
pd.merge(esquerda,direita,how='inner',on='key')
```

| <br> | key | A   | B   | C   | D   |
| --- | --- | --- | --- | --- | --- |
| 0   | K0  | A0  | B0  | C0  | D0  |
| 1   | K1  | A1  | B1  | C1  | D1  |
| 2   | K2  | A2  | B2  | C2  | D2  |
| 3   | K3  | A3  | B3  | C3  | D3  |

### **Juntar**

Juntar é um método conveniente para combinar as colunas de dois DataFrames indexados potencialmente diferentes em um único resultado DataFrame.

```python
esquerda = pd.DataFrame({'A': ['A0', 'A1', 'A2'],
                     'B': ['B0', 'B1', 'B2']},
                      index=['K0', 'K1', 'K2']) 

direita = pd.DataFrame({'C': ['C0', 'C2', 'C3'],
                    'D': ['D0', 'D2', 'D3']},
                      index=['K0', 'K2', 'K3'])
```

```python
esquerda.join(direita)
```

| <br> | **A** | **B** | **C** | **D** |
| --- | --- | --- | --- | --- |
| **K0** | **A0** | **B0** | **C0** | **D0** |
| **K1** | **A1** | **B1** | **NaN** | **NaN** |
| **K2** | **A2** | **B2** | **C2** | **D2** |

```python
esquerda.join(direita, how='outer')
```

| <br> | **A** | **B** | **C** | **D** |
| --- | --- | --- | --- | --- |
| **K0** | **A0** | **B0** | **C0** | **D0** |
| **K1** | **A1** | **B1** | **NaN** | **NaN** |
| **K2** | **A2** | **B2** | **C2** | **D2** |
| **K3** | **NaN** | **NaN** | **C3** | **D3** |

## **Operações**

**Informação sobre valores exclusivos:**

`**.unique()**` **é um comando que irá retornas somente os valores únicos.**

```python
df['col2'].unique()
```

> **array(\[444, 555, 666\])**

`**.nunique()**` **é um comando que vai ver quantos valores únicos existem.**

```python
df['col2'].nunique()
```

> **3**

`**.value_counts()**` **é um método muito usado que além de dar os elementos unicos no indice eles nos da a contagem dos elementos também.**

```python
df['col2'].value_counts()
```

> **444    2**  
> **555    1**  
> **666    1**  
> **Name: col2, dtype: int64**

**Lambda é uma função do python onde eu consigo resumir certas operações em somente uma linha.**

Removendo colunas permanentemente:

```python
del df['col1']
```

<br>

Obter nomes de coluna e índice:

```python
df.columns
df.index
```

## **Visualização básica**

```python
df.plot()
```

**![](Files/image.png)**

## **Entrada e saída de dados**

**O pandas pode ler uma variedade de tipos de arquivos usando seus métodos** `**pd.read_.**`

_**CSV Input**_

```python
df = pd.read_csv('exemplo')
```

<br>