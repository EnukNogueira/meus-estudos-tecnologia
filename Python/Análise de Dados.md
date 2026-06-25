## Análise de Dados

### O que é uma Biblioteca?

Conjunto de módulos e funções úteis para a pessoa usuária.  Para instalar uma biblioteca ou atualizar usamos o comando no terminal chamado `pip`. 

<br>

Analogia: ele é como se fosse o bibliotecário da biblioteca.

<br>

Como utilizar? Como eu referi anteriormente se deve usar o comando no terminal um exemplo claro seria assim: `pip install matplotlib`

Documentação do pip: [https://pypi.org/](https://pypi.org/)

Como instalar um pip ou pesquisar: [https://packaging.python.org/en/latest/tutorials/installing-packages/](https://packaging.python.org/en/latest/tutorials/installing-packages/)

<br>

### Importar uma biblioteca

É preciso importar uma biblioteca para utilizar em um código/projeto python 

para isso seria necessário seguir esse exemplo: `import matplotlib` 

Outro exemplo de como usar é usar o `as`(como) que reduz o código que você utiliza da biblioteca: `import matplotlib.pyplot as plt` como pode ver quando eu coloco o `as` e em seguida escrevo `plt` ele simplifica quando eu for chamar a biblioteca, agora quando eu for chamar eu só preciso escrever `plt`.

Outro comando muito usado é o `!pip list` ele mostra todas as biblioteca instaladas no seu computador ou maquina virtual.

<br>

Dicas para o notebookLM: quando for utilizar parar tirar duvidas ou estudar perguntar coisas como: Quais são os erros mais comuns ao usar essa função segundo a documentação?

<br>

Bibliotecas na pratica:

<br>

```python
import matplotlib.pyplot as plt

estudantes = [”Enuk, "Nuk", "Nunuk”]
notas = [8.5, 9, 2.5]

plt.bar(x = estudantes, height = notas)
```

<br>

Como pode ver é assim que se chama uma biblioteca para o código. O matplotlib, cria um gráfico ao utilizar esse sistema de lógica.

<br>

choice = escolha

help(choice) é um comando que você irá digitar no terminal, fazendo isso ele vai te explicar o que essa função da variável faz.

<br>

#### outro exemplo:

```python
from random import choices

alunos = choice(estudantes)
print(alunos)
```

<br>

Usando essa variável da biblioteca ela irá escolher aleatoriamente um aluno ao qual você digitou em outro exemplo acima.

<br>

Este código resulta na importação de 2 ou mais métodos de uma biblioteca, não necessitando repetir a importação desta a cada método desejado. Podemos, por exemplo, importar 2 métodos da biblioteca _random_ para colher uma amostra de 5 valores de uma lista de 20 valores gerada aleatoriamente com números de 0 a 99

```python
from random import randrange, sample

lista = []

for i in range(0, 20):
lista.append(randrange(100))

sample(lista, 5)
```

<br>

Esta forma é utilizada para importar todos os métodos de uma dada biblioteca. A diferença desta para o `import math` é que, neste caso, não precisamos usar o nome da biblioteca para chamar um método. Podemos passar apenas o nome dele. Por exemplo, se formos calcular a raiz quadrada de certo número poderíamos seguir por uma das duas formas:

<br>

import math  
<br>

```python
n = int(input("Digite um número positivo para calcular sua raiz quadrada:"))
print(f"\nA raiz quadrada de {n} é igual a {math.sqrt(n)}")
```

<br>

**Usando `from nome_biblioteca import *`**

```python
from math import * 
n = int(input("Digite um número positivo para calcular sua raiz quadrada:"))
print(f"\nA raiz quadrada de {n} é igual a {sqrt(n)}")
```

**Note que, no segundo exemplo, suprimimos o nome** `**math**` **utilizando o método desejado e escrevendo o código com menos caracteres.**

**<br>
**

### Funções 

Sequencias de instruções que aplicam determinada tarefa

podem ser reutilizadas em diferentes partes do código

recebem parâmetro de entrada `(inputs)`

podem retornar valores

<br>

### Bult in functions

São funções embutidas 

podem ser invocadas a qualquer momento

exemplo: `print() type(), list()`

**<br>
**

**Código de exemplo:**

```python
#notas do estudante
notas = {'1 trimestre': 8.5, '2 trismestre': 9.5,'3 trimestre': 7}
print(notas)
#calculando a soma
soma = 0
for nota in notas.values():
  soma += nota
print(soma)


```

<br>

Utilizando a função embutida sum( ). Como pode ver o código abaixo ficou muito mais simples que o de cima.

```python
somatorio = sum(notas.values())
print(somatorio)
```

Utilizando a função embutida len( )

```python
qtd_notas = len(notas) #a função len verifica a quantidade de numeros dentro da variavel
print(qtd_notas)
```

Calculando a média:

```python
media = somatorio/qtd_notas
media = round(media,1)#Arredonda a média
print(media)

```

### Funções sem parâmetros 

Formato padrão: 

```python
def <nome>():
 <instrucoes>

def media():
  calculo = (10 + 9 + 8) / 3
  print(calculo)

print(media)
```

Funções com parâmetros

Formato padrão

```python
def <nome>(<parm_1>, <parm_2>,  …, <parm_n>):
  <instrucoes>

def media(nota_1, nota_2, nota_3): #Isso é um parametro
 calculo = (nota_1+ nota_2 + nota_3)/3
 print(calculo)
 media(3, 6, 9)#Isso são os argumentos, são os parametros que substituem os parametros 
```

<br>

```python
notas = [8.5, 9.0, 6.0, 10.0]
def boletim(lista):
  media = sum(lista) / len(lista)
   if media >=6:
      situacao= "Aprovado"
   else:
      situacao = "Reprovado"

  return(media, situacao)

media, situacao = boletim(notas)
print(f'O estudante atingiu uma média de {media} e foi {situacao}.')



```

Função Lambda 

Chamada de função anônima também, não precisa ser definida e pode ser descrita em uma única linha 

```python
lambda <variavel>: <expressao>
"""Toda essa parte do código faz o que: a pessoa adiciona a nota que ela quer, depois adiciona +0.5 no valor da nota que a pessoa digitou"""

nota = float(input("Digite a nota do estudante: "))

def qualitativo(x):
  return x + 0.5
qualitativo(nota)
```

Agora usando o Lambda

```
nota = float(input("Digite a nota do estudante: "))

qualitativo = lambda x: x + 0.5
qualitativo(nota)
```

Função Map

Formato padrão:

`map(<lambda function>, <iterador>)`

<br>

```python
notas =⁠ [6.0, 7.0, 9.0, 5.5, 8.0]
qualitativo = 0.5

notas_atualiadas = map(lambda x: x + qualitativo, notas)
notas_atualizadas = list(notas_atualizadas)
print(notas_atualizadas)

```

<br>

## Lista

Coleção

ao ordenada de elementos que podem ser ou não do mesmo tipo

<br>

```python
notas_turma = ['teste' 8.0, 9.0 , 10.0, 'Birulinha', 7.0, 8.0, 9.0]
nomes = []
notas_juntas =[]
for i in range(len(notas_turma)):
 if o % 4 == 0:
    nomes.append(notas_turma[i])
 else:
    notas_juntas.append(nortas_turma[i])
print(nomes)
print(notas_juntas)



```

O código acima faz o seguinte, tem uma lista que segue um padrão de 4 coisas dentro dele como pode ver o nome teste e + 3 valores. Com isso da para separar, por exemplo pegar essa lista que está tudo misturado e separar em uma lista só para nomes e uma lista só para notas, para isso usaremos o `for`(para) e o método `i` e o `in`(em) e também o range(distancia) dentro do range usaremos o len que como falei antes ele conta a quantidade exata de itens dentro de uma estrutura como uma lista. 

<br>

Fazendo isso depois vamos usar o nome da variável(nomes) e o método append que serve para adicionar mais coisas na lista. e entre os parênteses vamos chamar o método principal onde está todas as informações e colocar o `[i]` para poder criar essa nova lista que separa e esse processo se repete agora para separar também em uma lista só de números.

<br>

```python
notas =[]
for i in range(0, len(notas_juntas), 3)
  notas.append([notas_juntas[i], notas_juntas[i+1], notas_juntas[i+2]])
print(notas)

notas[0][2]
```

Dentro dos parênteses começamos com 0 pois assim definimos o numero que alista irá começar, depois o len para chamar a quantidade exata da variável`(notas_juntas)` e por ultimo o 3 para sempre pular de 3 em 3 para separar quando começa a nota de cada aluno.  

<br>

Exemplo: agora de como ficaria quando funcionar, em si esse código agora faz o que ele separa as notas de cada aluno em uma lista separada pra cada. E também é possível puxar um determinado valor da lista graças ao código que fizemos.

![](Files/image%202.png)

## Tuplas

Estrutura de dados usada para armazenar itens em uma única variável

Exemplo: 

<br>

```python
nome= ('Ana', 9.0, 8.0, 7.0)
for i in range(4):
    print(nome[i])

```

<br>

Não se pode usar o método append pois é uma lista imutável, significa que não pode aver alterações. Usada somente para dados que não queira que seja alterado.

<br>

O `[i]` é a forma que o Python usa para **acessar um item específico** dentro de uma sequência, como uma lista. O ato de usar os colchetes com um número dentro é chamado de **indexação**.

<br>

Neste código, a instrução `range(3)` faz a variável `i` mudar de valor a cada volta do loop: primeiro ela vale 0, depois 1, depois 2. Consequentemente, o comando `alunos[i]` vai visitar e imprimir a casa 0, depois a casa 1, e finalmente a casa 2.

<br>

## List comprehension

Forma simples de criar listas.

<br>

```python
[expressão for item in lista]

notas = [[9.0, 9.0, 10.0],[5.0, 7.0, 6.0],[4.0, 8.0, 10.0],[2.0, 1.0, 0.0],[9.0, 5.0, 10.5])

def media(lista: list =[0] -> float:

calculo =sum(lista) / len(lista)

return calculo

medias =[round(media(nota),1) for nota in notas]
medias
```

1. **`def media(...)`**: É o comando padrão para criar a função chamada "media".
2. **`lista`**: É o nome da variável de entrada (o parâmetro).
3. **`: list`**: Esta é a dica de tipo. Você está documentando o código, avisando a quem for ler (e ao seu editor de texto) que o dado injetado ali deve ser obrigatoriamente uma lista.
4. **`= [0]`**: Este é o valor padrão, que age como um sistema de segurança ou _backup_. Se quem estiver usando o código esquecer de enviar uma lista para a função, o Python não vai travar com um erro. Ele vai assumir automaticamente que a variável `lista` recebe a lista `[0]`.
5. **`-> float:`**: É a dica do tipo de saída. Isso avisa que, no final da execução, o valor que a função vai devolver (usando o comando `return`) será um número com casas decimais (conhecido no Python como _float_, ou ponto flutuante).

**Analogia Prática** Imagine o manual de instalação de um equipamento. Essa linha de código diz: "Vou montar uma operação chamada 'media'. O cabo que você vai conectar na entrada (`lista`) precisa ser do tipo conjunto de fios (`: list`). Se você ligar a máquina sem conectar nenhum cabo, ela vai puxar um cabo neutro de emergência por conta própria (`= [0]`). A energia resultante que vai sair na ponta final do equipamento será de corrente contínua decimal (`-> float`)."

```
[expr for item in cond]
nomes= [('Enuk', 'J720'), ('Enu','J721'), ('En','J722'), ('EnI',J723),('E','J724')]
notas = [[9.0, 9.0, 10.0, 7.5, 1,5])

nomes =[nome[0] for nome in nomes]

estudantes = list(zip(nomes, medias))
print(estudantes)

candidatos = [estudante[0] for estudante in estudantes if estudante[1] >= 8.0]
print(candidatos)


```

- **`for nome in nomes`:** O Python entra na lista original e começa a visitar cada item um por um. A variável temporária `nome` representa a tupla inteira que está passando na esteira naquele exato milissegundo. Na primeira volta do loop, `nome` equivale a `('Enuk', 'J720')`.
- **`nome[0]`:** É a ação executada em cada volta. Aqui o sistema recebe a instrução: "Desta tupla que está na minha frente agora, pegue apenas o dado que está na posição 0" (que é a string 'Enuk'). O 'J720' é ignorado.
- **`[ ... ]`:** Os colchetes externos indicam que todos os dados coletados pelo braço robótico na etapa 2 devem ser empacotados em uma nova lista.

<br>

## Exceções 

Erros detectados durante a execução do programa

Interrompem o fluxo do programa o encerrando. Usamos as exceções para o código não quebrar. Seguindo o exemplo de códigos a seguir ele vai mostrar o motivo do erro para o usuário. 

<br>

```
except <nome_da_excecao as e>:
```

Podemos fazer o código assim: 

```
try:
    nome = input("Digite o nome do(a) estudante: ")
    resultado = notas[nome]
except KeyError:
    print("Estudante não matriculado(a) na turma")
else:
print(resultado)
finally:
  print('A consulta foi encerrada')

#Outro forma de fazer:

try:
    nome = input("Digite o nome do(a) estudante: ")
    resultado = notas[nome]
except Exception as e:
    print(type(e), f"Erro: {e}")

```

<br>

Finally é usado para finalizar o código depois que o usuário digitar a “pesquisa”

<br>

Outra forma de trabalhar com exceções, é criar uma própria pensando em um comportamento que não queremos que ocorra em nosso programa. Para isso, usamos a palavra-chave `raise` que permitirá que lancemos uma exceção.

## Raise

A estruturação é a seguinte:

```
raise ValueError("A lista de notas deve possuir dez elementos")
Copiar código
```

Usamos a palavra-chave `raise`, o tipo de erro que queremos levantar, ou seja, a exceção, e a mensagem que queremos passar para o usuário.

<br>

Matplotlib

<br>

```python
for rodada in historico:
    if rodada.get("nome do jogador") == name:
        resposta_usuario = rodada.get(name)
        resposta_correta = rodada.get("resposta_correta")
       
        if resposta_usuario == resposta_correta:
            acertos += 1
        else:
            erros += 1
# Teste de biblioteca Matplotlib
categorias = ['Acertos', 'Erros']
quantidades = [acertos, erros]
cores = ['#4CAF50', '#F44336'] #Igual no minecraft quando criava uma textura.

plt.bar(categorias, quantidades, color=cores)
plt.title(f'Resultado de {name}')
plt.xlabel('Resultados')
plt.ylabel('Quantidade de Partidas')

import math
plt.yticks(range(0, max(quantidades) + 2))

#Imprime o gráfico
plt.show()

```

<br>

Para analisar os dados do jogo eu iria eu preciso fazer como está no código acima:  for(para determinar o trecho do código que vai ser “puxado” `in` para analisar 1 item por vez do histórico. 

`rodada.get` o .get faz o código puxar um dado especifico.    
<br>

`plt.bar` é o comando oficial da biblioteca matplotlib que manda criar o gráfico de barras.

`plt.title` o proprio nome já fala irá colocar um titulo superior 

`plt.xlabel(’Resultados’)` Nome dos eixos (vertical e horizontal)

`plt.show()` Abre uma janela separada que irá mostrar os dados em gráficos.

<br>