## Listas

Listas são coleções de objetos em Python. Ao invés de declarar 1 variável para cada valor que gostaríamos de armazenar, podemos criar uma lista para armazenar vários valores.

```py
# Criando uma lista vazia.
listavazia = []

# Criando uma lista com alguns valores.
numeros = [1, 3, 7, 8, 9]

# Listas podem mesclar diferentes tipos de valores.
listamista = [14, "let's code", 0.1, True]

# Acessamos cada elemento da lista através de um índice entre colchetes.
# Os índices começam em 0.
print(numeros[0])
print(numeros[1])
print(numeros[2])
print(numeros[3])
print(numeros[4])

# Listas são mutáveis: podemos alterar o valor de seus itens.
numeros[2] = 5
print(numeros)

# Um jeito inteligente de trabalhar com listas é utilizando loops.
indice = 0
while indice < 5:
    print(numeros[indice])
    indice = indice + 1
```

## Funções de listas

Algumas funções podem nos ajudar a trabalhar com listas. Ao percorrermos nossa lista com um while, poderíamos usar len() caso não soubéssemos o comprimento da lista.

```py
indice = 0
while indice < len(numeros):
    print(numeros[indice])
    indice = indice + 1
```

Outra função útil é `lista.append()`, que coloca um elemento novo ao final da lista.

```py
animais = []
resposta = 's'
while resposta == 's' or resposta == 'S':
    resposta = input('Deseja adicionar um animal à lista (s/n)? ')
    if (resposta == 's' or resposta == 'S'):
        animal = input('Digite o nome do animal: ')
        animais.append(animal) # adiciona o novo animal à lista
print(animais)
```

A função `lista.remove()` deleta um elemento da lista. (mas dá erro se o elemento não existir).

```py
animal = input('Digite o animal a ser deletado da lista: ')
animais.remove(animal)
print(animais)
```

Algumas outras funções úteis:

- ```
  lista.count()
  ```

   

  conta quantas vezes um elemento aparece.

  ```py
  jogadores = ['Ronaldo', 'Rivaldo', 'Ronaldo', 'Adriano']
  ronaldos = jogadores.count('Ronaldo')
  print(jogadores)
  print('Quantidade de Ronaldos: ', ronaldos)
  ```

- ```
  lista.index()
  ```

   

  busca em um elemento e fala em qual posição ele aparece.

  ```py
  rivaldo = jogadores.index('Rivaldo')
  print("Rivaldo está na posição ", rivaldo)
  ```

- ```
  lista.sort()
  ```

   

  ordena uma lista.

  ```py
  jogadores.sort()
  print("jogadores em ordem alfabética: ", jogadores)
  ```

- As funções

   

  ```
  max(lista)
  ```

   

  e

   

  ```
  min(lista)
  ```

   

  obtém, respectivamente, o maior e o menor valor.

  ```py
  digitos = [3, 1, 4, 1, 5, 9, 2, 6, 5]
  maior = max(digitos)
  menor = min(digitos)
  print(digitos)
  print("Maior = ", maior, "e menor = ", menor)
  ```

## Tuplas

```py
# Uma tupla é uma coleção de objetos que lembra muito as listas.

# Ao invés de colchetes, usamos parênteses para declarar as tuplas:
numeros = (1,2,3,5,7,11)

# Podemos declarar sem parênteses também:
numeros = 1,2,3,5,7,11

# Para acessar um valor, utilizamos a mesma sintaxe das listas:
print(numeros[4])
print(type(numeros))

'''
Porém, tuplas são imutáveis: não é possível adicionar ou modificar valores.
Descomentar a linha abaixo provocará erro de execução:
'''
# numeros[4] = 8

# Podemos gerar uma tupla a partir de uma lista...
lista1 = [3, 1, 4, 1, 5, 9, 2, 6, 5]
tupla1 = tuple(lista1)
print(tupla1)

# ...ou uma lista a partir de uma tupla:
tupla2 = [1, 6, 1, 8]
lista2 = list(tupla2)
print(lista2)

# Também pode-se usar o unpacking com uma tupla:
a, b, c, d, e, f = numeros # "desempacota" a tupla numeros
print("O primeiro vale:", a, "e o ultimo vale:", f)
```

## Funções de strings

```py
# Suponhamos que temos a seguinte string:

frase = 'uma FRASE'

# Podemos acessar individualmente cada caractere em uma frase.
# A ideia é a mesma de acessar uma lista:
print(frase[0])
print(frase[1])
print(frase[2])

tamanho = len(frase)
print("A frase possui", tamanho, "caracteres")

# Porém, strings são imutáveis: não podemos alterar caracteres individuais
# A linha abaixo, se for descomentada, dará erro no programa:
# frase[4] = 'C'

# Podemos converter strings para listas:
listafrase = list(frase)
print(listafrase)

# A função join() intercala cada elemento de uma lista com uma string.
stringfinal = '-py'.join(listafrase)
print(stringfinal)

# Usar um join() com uma string vazia é útil para transformar a lista de volta
# em string:
stringfinal = ''.join(listafrase)
print(stringfinal)

# Existem algumas funções interessantes que retornam a string "tratada":
s1 = frase.capitalize() # 1a letra maiúscula, restante minúscula
s2 = frase.title() # todo início de palavra em maiúscula, resto minúscula
s3 = frase.upper() # string inteira em maiúscula
s4 = frase.lower() # string inteira em minúscula
s5 = frase.replace('F', 'C') # substitui a primeira substring pela segunda

print(s1)
print(s2)
print(s3)
print(s4)
print(s5)
# Note que NENHUMA delas ALTERA a string original, elas sempre retornam
# a string nova.
print('String original:', frase)

# Outra possibilidade com strings é quebrar a string em uma lista de substrings
# Sempre que o caractere especificado é encontrado, a string é quebrada
quebra1 = frase.split(' ') # quebra a frase no caractere espaço em branco
quebra2 = s3.split('A') # quebra a frase em maiúsculas no caractere 'A'

print(quebra1)
print(quebra2)

# Podemos inserir quebras de linha com '\n'
frase = 'uma\nFRASE'
print(frase)
# Podemos inserir tabulação com '\t'
frase = 'uma\n\tFRASE'
print(frase)
# Para conseguir representar a barra '\', precisamos de 2 barras:
frase = 'uma\\FRASE'
```

Clique [aqui](https://docs.python.org/3.8/library/stdtypes.html#str) para acessar a documentação de Strings do Python 3.

## Uso de operadores aritméticos com strings

```python
# Dois operadores aritméticos possuem um comportamento especial em strings:
# Operador de soma (+): concatena (une) 2 strings.
palavra1 = "Let's"
palavra2 = "Code"
palavra3 = palavra1 + palavra2
print(palavra3)

# Operador de multiplicação (*): copia uma string 'n' vezes:
palavra = 'uma'
trespalavras = 3*palavra
print(trespalavras)
```

## Formatação de strings

Uma última função interessante de strings é o .format() Para entender como ela funciona, podemos pensar em um contrato. É normal que ele venha com campos em branco para serem preenchidos posteriormente. Ex:

Eu, ______________**, portador do RG ________________ e nascido ao dia \**/\**/**, autorizo o uso de minha imagem.

Ao inserirmos no contrato nossas informações pessoais, ele se torna completo.

O .format() serve para "preencher" os "campos em branco" de uma string.

Os campos em branco serão representados por pares de chave: {}

```py
prod = 'chocolate'
preco = 3.14
print('O produto {} custa {}.'.format(prod, preco))

# Na linha acima, prod substituirá o primeiro {}, e preco o segundo {}.
# Saída: O produto chocolate custa 3.14.

# É possível colocar algumas opções especiais de formatação. Por exemplo:

stringoriginal = 'O litro da gasolina custa {:.2f}'
'''
: indica que passaremos opções
.2 indica apenas 2 casas após o ponto decimal
f indica que é um float
'''
preco = 3.14159265
stringcompleta = stringoriginal.format(preco)
print(stringcompleta)
# Saída: O litro da gasolina custa 3.14
# O preço sai com apenas 2 casas após a vírgula!

# Pode-se chamar as variávies em diferentes ordens:

print('{2}, {1} and {0}'.format('a', 'b', 'c'))
# Saída: c, b and a

print('{0}{1}{0}'.format('abra', 'cad'))
# Saída: abracadabra


# Podemos especificar um número de dígitos obrigatório por campo.
# Vejamos o exemplo:

dia = 1
mes = 8
ano = 2019
data1 = '{}/{}/{}'.format(dia, mes, ano)
print(data1)
# Saída: 1/8/2019
# O dia e o mês ocupam apenas 1 espaço


data2 = '{:2d}/{:2d}/{:4d}'.format(dia, mes, ano)
# A opção 'd' significa que o parâmetro é um número inteiro.
print(data2)
# Saída:  1/ 8/2019
# Agora, dia e mês ocupam obrigatoriamente 2 espaços:  1/ 8/2019

# Podemos forçar que os espaços em branco sejam preenchidos com o número 0:
data3 = '{:02d}/{:02d}/{:04d}'.format(dia, mes, ano)
print(data3)
# Saída: 01/08/2019
# Agora sim a data está no formato usual, dd/mm/aaaa: 01/08/2019

# Um modo mais simples de utilizar o format
nome = "Pietro"
profissao = "professor"
escola = "Let's Code"

print(f"{nome} é {profissao} da {escola}.")
# Saída: Pietro é professor da Let's Code.
```

O .format() possui muitas opções interessantes. Há um site inteiro dedicado a explicar e exemplificar todas essas opções: https://pyformat.info/

## Dicionários

Um dicionário é uma coleção, assim como as listas e as tuplas. Porém, enquanto as tuplas eram indexadas por um índice, os dicionários são indexados por chaves. Todo elemento em um dicionário possui uma chave e um valor. Chaves tipicamente são strings, valores podem ser qualquer tipo de dado.

```py
# O dicionário é definido pelos símbolos { e }

dicionario = {}

# O dicionário não possui um "append".
# Adicionamos valores diretamente:

dicionario['cat'] = 'gato'
dicionario['dog'] = 'cachorro'
dicionario['mouse'] = 'rato'

print(dicionario)
print(type(dicionario))

'''
Saída:
{'cat': 'gato', 'dog': 'cachorro', 'mouse': 'rato'}
<class 'dict'>
'''

# Dicionários, assim como as listas, são mutáveis:
dicionario['dog'] = 'cão'
print(dicionario)
# Saída: {'cat': 'gato', 'dog': 'cão', 'mouse': 'rato'}

# Podemos criar o dicionário diretamente também:
dicionario2 = {'Curso': 'Python Pro', 'Linguagem':'Python', 'Módulo':2}
print(dicionario2)
# Saída: {'Curso': 'Python Pro', 'Linguagem': 'Python', 'Módulo': 2}

# Podemos utilizar o operador "in" para verificar se uma chave existe:
if 'cat' in dicionario:
    print('cat existe!') # Sim
if 'bird' in dicionario:
    print('bird existe!') # Não
if 'gato' in dicionario:
    print('gato existe!') # Não

'''
Também podemos utilizar as funções .keys() e .values() para obter listas
com apenas as chaves ou apenas os valores do dicionário.
'''
chaves = dicionario.keys()
print(chaves)
# Saída: dict_keys(['cat', 'dog', 'mouse'])

valores = dicionario.values()
print(valores)
# Saída:dict_values(['gato', 'cão', 'rato'])

# Já a função .items(), retorna uma lista de tuplas (chave, valor) de um dicionário

itens = dicionario.items()
print(itens)
# Saída:dict_items([('cat', 'gato'), ('dog', 'cão'), ('mouse', 'rato')])
```

## Percorrendo coleções

O for é um tipo especial de loop feito para percorrer elementos de uma coleção. Acima vimos exemplos usando um while e um contador para percorrer uma lista. O for elimina a necessidade de inicializarmos um contador, incrementarmos e verificar a condição de parada. Sintaxe:

```py
for (variável temporária) in (lista):
    # instruções...
    # ...
```

O for se repete uma vez para cada elemento da lista. A cada repetição, a variável temporária assume o valor de um elemento da lista, na ordem da lista.

```py
fib = [1, 1, 2, 3, 5, 8, 13]
for elemento in fib:
    print(elemento)
```

## Percorrendo sequências numéricas

O for pode ser usado, junto com a função range(), para gerar sequências numéricas e contagens. Existem 3 meios de usar o range(): especificando 1, 2 ou 3 parâmetros.

```py
# Com 1 parâmetro, ele será interpretado como valor final (exclusivo).
# O valor inicial será 0 e o incremento será 1.

for numero in range(10):
    print(numero)
    # este exemplo imprime os números de 0 a 9, de um em um

# Com 2 parâmetros, o primeiro será o valor inicial (inclusivo) e o
# segundo será o final (exclusivo).
# O incremento continuará sendo 1.

for numero in range(1,11):
    print(numero)
    # este exemplo imprime os números de 1 a 10, de um em um

# Com 3 parâmetros, o terceiro será interpretado como incremento.
for numero in range(1,20,2):
    print(numero)
    # este exemplo imprime os ímpares positivos menores do que 20
    # ele começa valendo 1 e salta de 2 em 2 até atingir ou passar 20

# O incremento pode ser também um decremento (incremento negativo).
for numero in range (10,0,-1):
    print(numero)
    #Imprimindo os números de 1 a 10 em ordem decrescente
```

## Funções

Funções são uma espécie de "subprograma". Elas são como pequenos pedacinhos de programa que podem ser chamadas pelo nome. Para criar uma função usamos o comando "def" e o nome da função. Elas são um bloco de comando assim como if/elif/else, while e for.

```py
def hello():
    print("Olá, mundo!")
```

Quando uma função é chamada pelo nome, o fluxo do programa é interrompido. Em seguida, a função inteira é executada, e ao final dela, o programa volta a ser executado do mesmo ponto que parou.

```py
hello()

# Saída: Olá, mundo!
```

É possível passarmos informações para uma função. Chamamos essas informações de "parâmetros" ou "argumentos. Na definição da função, daremos nome a esses parâmetros. Dentro da função, eles serão tratados como se fossem variáveis.

```py
def ola(nome):
    print("Olá", nome)
```

Ao chamarmos a nossa funcao, passamos os parâmetros entre parênteses. O nome ou valor passado *não precisam* ser iguais aos declarados na função! O nome do parâmetro interno da função é um "apelido" que a função dará para o valor ou variável que passamos.

```py
ola("Maria")
# Saída: Olá, Maria

aluno = "João"
ola(aluno)
# Saída: Olá, João
```

A função pode receber vários parâmetros separados por vírgula.

```python
def dadosPessoais(nome, idade, cidade):
    print("Seu nome é {}, você tem {} anos e mora em {}.".format(nome, idade, cidade))

dadosPessoais("José", 30, "Maceió")
# Saída: Seu nome é José, você tem 30 anos e mora em Maceió.
```

Os parâmetros podem ser passados fora de ordem. Porém, para isso precisamos explicitar qual parâmetro estamos passando, para evitar ambiguidade ou erros de interpretação do Python.

```python
dadosPessoais(idade=56, cidade="Florianópolis", nome="Ana")
# Saída: Seu nome é Ana, você tem 56 anos e mora em Florianópolis.
```

## Funções com resposta

Uma função pode ter uma "resposta". Por exemplo, nossa função pode ser uma conta, e o resultado da conta pode ser útil em nosso programa. Dizemos que essas funções "retornam" um valor. Utilizamos a palavra "return" para fazer uma função retornar sua resposta. Quando uma função retorna um valor, ela pode ser usada em expressões matemáticas ou lógicas, ter seu valor atribuído a uma variável, etc.

```py
def somatorio(lista):
    soma = 0
    for item in lista:
        soma = soma + item
    return soma

numeros = [1, 2, 3, 4, 5]
soma_dos_numeros = somatorio(numeros)
print("A soma dos elementos da lista vale: ", soma_dos_numeros)

if somatorio(numeros) > 50:
    print("Que soma grande!")
else:
    print("Que soma pequena!")
    
'''
Saída:
A soma dos elementos da lista vale:  15
Que soma pequena!
'''
```

## Funções recursivas

Algumas funções são chamadas funções recursivas. A recursividade (ou recursão) é uma propriedade na qual uma função faz referência a si mesma. Quando a função encontra uma nova referência, ela irá pausar sua execução atual e iniciar a execução da nova instância, para só então retomar sua execução.

Assim como nos loops, é necessário ter alguma condição para que as chamadas recursivas sejam interrompidas, evitando que executem para sempre.

```py
def funcaoRecursiva(numero):
    if (numero != 1):
        funcaoRecursiva(numero - 1)
    print(numero)

print("Testando a função recursiva:")
funcaoRecursiva(10)
```

Note que no exemplo acima passamos 10 para a função. Sua execução foi interrompida por uma nova chamada passando 9, depois 8, depois 7... Ao chegar em 1, ele foge da condicional e imprime 1, encerrando a execução. Então a instância que recebeu 2 tambem conclui sua execução, depois a chamada 3, a 4... A 10, que foi a 1a chamada, encerra por último.

Dizemos que é um comportamento de pilha - exatamente como uma pilha de pratos sobre a mesa: O primeiro prato que foi colocado sobre a mesa será o último a sair, pois todos os pratos colocados sobre ele precisam ser retirados antes de você poder retirar o último.

Problemas recursivos normalmente são problemas do tipo "dividir para conquistar": Temos um "caso base", ou seja, um ou mais casos onde há uma resposta direta; E temos um "caso geral", que é uma versão reduzida do problema original.

## Agrupando parâmetros

Podemos utilizar o operador ***** - que, neste caso, não será uma multiplicação. Ao colocarmos o ***** ao lado do nome de um parâmetro na definição da função, estamos dizendo que aquele argumento será uma coleção. Mais especificamente, uma tupla. Porém, o usuário não irá passar uma tupla. Ele irá passar quantos argumentos ele quiser, e o Python automaticamente criará uma tupla com eles:

```py
def piscina(*infos):
    vol = infos[0]*infos[1]*infos[2]
    return vol

volume = piscina(5, 4, 5)

print('O volume é: ', volume)
```

Podemos utilizar o operador ***** na chamada da função também. Na definição, o operador ***** indica que devemos agrupar itens avulsos em uma coleção. Na chamada, ele indica que uma coleção deve ser expandida em itens avulsos:

```py
def piscina(prof, largura, comprimento):
    vol = prof*largura*comprimento
    return vol

lista = [5, 4, 5]

volume = piscina(*lista)

print('O volume é: ', volume)
```

## Parâmetros opcionais

Outra possibilidade são funções com parâmetros opcionais. Note que isso é diferente de termos quantidade variável de parâmetros. No caso da quantidade variável, normalmente são diversos parâmetros com a mesma utilidade (números a serem somados, valores a serem exibidos etc), enquanto os parâmetros opcionais são informações distintas que podem ou não ser passadas para a função.

Para criar parâmetros opcionais, usaremos ***\***, e os parâmetros passados serão agrupados em um dicionário: o nome do parâmetro será uma chave, e o valor será... O valor.

```py
def piscina(prof, **infos):
    vol = prof*infos['largura']*infos['comprimento']
    return vol

volume = piscina(5, largura=4, comprimento=5)

print('O volume é: ', volume)
```

Analogamente ao caso dos parâmetros múltiplos, é possível que o usuário da função já tenha os dados organizados em um dicionário. Neste caso, basta usar ***\*** na chamada da função para expandir o dicionário em vários parâmetros opcionais:

```py
def piscina(prof, largura=4, comprimento=5):
    vol = prof*largura*comprimento
    return vol

infos = {'largura': 10, 'comprimento': 20}

volume = piscina(5, **infos)

print('O volume é: ', volume)
```
