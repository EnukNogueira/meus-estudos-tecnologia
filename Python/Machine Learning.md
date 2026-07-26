## Machine Learning

#### Classificação em machine learning

<br>

O Machine Learning (ML), como uma subárea da inteligência artificial, se concentra no desenvolvimento de **algoritmos** que são utilizados no computador para realizar tarefas sem a necessidade de programar explicitamente as regras que serão utilizadas. Esses algoritmos baseiam suas decisões a partir de dados com o objetivo de compreender e identificar o padrão existente nesses dados, para então utilizar esse conhecimento na realização das predições.

* * *

<br>

### Como funciona o Machine Learning

O funcionamento do Machine Learning tem 3 etapas principais:

- **1 - Coleta dos dados**

A primeira etapa de um projeto de ML é a extração ou coleta de dados. Os dados são essenciais e podem ser considerados a matéria-prima dos algoritmos. A quantidade e qualidade desses dados têm um impacto muito grande no aprendizado dos modelos. Com poucos dados, o modelo pode não ter informações suficientes para aprender. Com dados de pouca qualidade, o modelo pode não conseguir diferenciar bem o padrão dos dados ou compreender o padrão de forma diferente do que ocorre com os dados do mundo real.

- **2 - Treinamento dos modelos**

Após coletar dados e assegurar que estão com qualidade, chega à etapa de treinar os modelos. O treinamento consiste no algoritmo procurar o padrão presente nos dados e construir uma regra para tomar decisões posteriormente em novos dados.

- **3 - Avaliação**

Com o modelo treinado, chega a etapa de avaliar o desempenho do modelo, para identificar se realmente aprendeu o padrão dos dados e se é capaz de aplicar de forma satisfatória a regra gerada pelo algoritmo em dados novos, que não foram utilizados durante o momento do treinamento.

* * *

<br>

Scikit-Learn 

Uma biblioteca do Python que oferece uma ampla variedade de algoritmos e também oferece ferramentas de pré-processamento dos dados, análise e avaliação de modelos. 

Documentação da biblioteca: [https://scikit-learn.org/stable/index.html](https://scikit-learn.org/stable/index.html)

* * *

<br>

Overfitting (Sobre ajuste):

O overfitting ocorre quando um modelo se ajusta demais aos dados de treinamento. Isso indica que o modelo capturou não só o padrão dos dados, mas também ruídos e variações aleatórias que estão presentes nos dados usados para treinamento. Como resultado disso, o modelo tem um resultado muito bom ao ser avaliado com os dados de treinamento, porém seu desempenho nos dados de teste ou em dados novos cai consideravelmente.

Características do overfitting:

- Erro muito baixo nas predições em dados de treinamento;
- Erro muito alto nas predições em dados de teste;
- Modelo muito complexo que tenta memorizar os dados de treinamento ao invés de aprender o padrão dos dados.

### Underfitting (Subajuste):

O underfitting ocorre quando um modelo é muito simples e não consegue capturar o padrão presente nos dados. Isso indica que o modelo não foi capaz de aprender os relacionamentos existentes nos dados de treinamento e acaba tendo um desempenho ruim tanto em dados de treinamento quanto de teste.

Características do underfitting:

- Erro muito alto nas predições em dados de treinamento;
- Erro muito alto nas predições em dados de teste;
- Modelo muito simples que não consegue representar bem os dados.

O objetivo principal da criação de modelos de machine learning é encontrar um equilíbrio entre o overfitting e underfitting, para que tenha um ajuste adequado. Um modelo bem ajustado é capaz de aprender o padrão dos dados e generalizar para novos dados, fazendo predições com consistência sem que seja muito influenciado pelos ruídos presentes nos dados de treinamento.

* * *

<br>

### Índice Gini

Este índice informa **o grau de heterogeneidade** dos dados. Seu objetivo é medir a frequência de um elemento aleatório de um nó ser rotulado de maneira incorreta. Em outros termos, esse índice quantifica e determina a impureza de um nó por meio do seguinte cálculo:

![Imagem](https://cdn3.gnarususercontent.com.br/3067-classificacao/imagens/Aula3-img1.png)

Onde:

- `P(i)` representa a frequência relativa das classes em cada um dos nós;
- `k` é o número de classes.

Se o índice Gini for igual a 0, isso indica que o nó é puro. No entanto, se o valor dele se aproxima mais do valor 1, o nó é impuro.

### Entropia

A ideia básica da entropia é medir **a desordem dos dados** de um nó por meio da variável classificadora. Assim, como o índice de Gini, ela é utilizada para caracterizar a impureza dos dados e pode ser calculada por meio da seguinte fórmula:

![Imagem](https://cdn3.gnarususercontent.com.br/3067-classificacao/imagens/Aula3-img2.png)

Onde:

- `pi` representa a proporção de dados no conjunto de dados, pertencentes à classe específica `i`;
- `c` é o número de classes.

Depois que é realizada a primeira escolha de divisão, o processo é repetido para cada subconjunto até que uma condição de parada seja atingida ou que todos os subconjuntos finais estejam totalmente puros, ou seja, com apenas dados de uma das classes da variável alvo. A partir da regra gerada, novos dados podem ser classificados passando por cada uma das decisões da árvore até chegar na escolha final.

* * *

<br>

### Score

O método `score()` tem como objetivo comparar as previsões feitas pelo modelo com os valores reais dos dados. Além disso ele calcula uma taxa de acerto em porcentagem.

* * *

<br>

### **Holdout**

Consiste em dividir os dados em duas partes: treinamento e teste:

- Treinamento para treinar o modelo. 
- Teste para avaliar o desempenho do modelo em dados não visto anteriormente.

Também é utilizado em alguns casos mais um método além desses 2 que é o de validação que é utilizado na comparação  de diferentes modelos.

<br>

### **Acurácia**

É a métrica mais comum e básica em problemas de classificação. É utilizada para medir a proporção de dados previstos corretamente pelo modelo em relação ao total dos dados. Essa métrica é útil quando as classes da variável alvo estão balanceadas.

<br>

### **Retorno (recall)**

Mede a proporção de dados positivos que foram corretamente identificados pelo modelo, ou seja, revela a capacidade do modelo em evitar a classificação incorreta de dados positivos como negativos. 

<br>

### **Precisão**

Mede a proporção de dados classificados como positivos que são realmente positivos, ou seja, revela a capacidade do modelo em evitar a classificação incorreta de dados negativos como positivos. É usada quando o risco ou custo de classificar falsos positivos é alto

<br>

### **F1-Score**

Fornece um equilíbrio entre o recall e a precisão, sendo útil quando as classes da variável alvo estão desbalanceadas

* * *

<br>

## Guia de um projeto de ML

1. Um olhar geral sobre o problema 
2. Obtenha os dados
3. Visualize e explore o conjunto de dados para gerar insights
4. Prepare os dados para os algoritmos 
5. Selecione um modelo e treine
6. Otimize seu modelo
7. Apresente sua solução
8. Coloque seu modelo em produção e mantenha seu sistema

* * *

<br>

## Análise Exploratória de Dados

Como criar um mapa com “pontinhos” 

Exemplo:

```python
fig = px.scatter_mapbox(df_rent, lat="Latitude", lon="Longitude", color="Price", size="Size", color_continuous_scale=px.colors.cyclical.IceFire, size_max=15, zoom=10, opacity=0.4)

fig.update_coloraxes(colorscale = [[0, 'rgb(166,206,227, 0.5)'],[0.02, 'rgb(31,120,180, 0.5)'],[0.05, 'rgb(178,223,138, 0.5)'], [0.10, 'rgb(51,160,44, 0.5)'],[0.15, 'rgb(251,154,153, 0.5)'], [1, 'rgb(227,26,28, 0.5)']],)

fig.update_layout(height=800, map´box=dict(center=go.layout.mapbox.Center(lat=-23.543138,lon=-46.69486)))
fig.show()
```

* * *

<br>

### Info

`df.info()` o método `.info` ele irá me dar uma visão geral sobre as minhas colunas. Falando se tem valores nulos(null) ou não nulos(non-null)

### Hist

`df.hist(bins=30, figsize=(30, 15))`  da a distribuição dos dados criando histogramas para cada uma das features.

<br>