## Instalando o Python no Windows : Vídeo

## Instalando o Python no Mac OS X

Comando para instalação do HomeBrew:

```language
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Instalando o Python no Linux (debian/ubuntu):

```console
apt install python3 python3-pip
```

# Jupyter Notebook

Com o Python instalado, você já pode abrir o prompt de comando para digitar os seguintes comandos:

- Para instalar o programa **Jupyter Notebook**, que utilizaremos para escrever nossos códigos Python:

  ```
  pip install notebook
  ```

- Para garantir que estamos utilizando a versão mais recente do **Jupyter Notebook**:

  ```
  pip install notebook --upgrade
  ```

- Para iniciar o programa **Jupyter Notebook**:

  ```
  jupyter notebook
  ```

  Ao exercutar este comando, uma janela deverá se abrir em seu navegador (Chrome, Firefox, Edge, etc) com o Jupyter Notebook (uma alternativa é copiar e colar a URL que aparece em seu prompt de comando).

Apenas para dar uma pequena prévia, vamos criar um novo arquivo selecionando "New" e então "Notebook: Python 3" (nesse momento, você pode optar por selecionar alguma pasta do seu computador, como *Meus Documentos*, para que o novo arquivo seja criado dentro dela).

Uma nova janela se abrirá. Essa janela é a interface de escrita para o arquivo que você acabou de criar.

Como você pode ver, existe uma célula vazia nesse arquivo. Nós vamos clicar nela e escrever:

```
print("Hello, World!") 
```

E, com essa célula selecionada, vamos clicar em "Run".

Alguns comentários finais:

1. Existe uma versão do Jupyter Notebook online. Basta entrar no [site](https://jupyter.org/) dele para testar.
2. Existe ainda outra ferramenta online para escrever notebooks chamada *Google Colaboratory* (ou Colab), um serviço gratuito do Google que você pode acessar por [aqui](https://colab.research.google.com/) sem instalar nada em seu PC (nem mesmo o Python). Para utilizá-lo, basta fazer o login com uma conta do Google. Seus arquivos serão salvos no Google Drive dessa conta do mesmo modo que um Google Docs ou Google Spreadsheet.

E é isso, acabou. Ou melhor, só está começando! A partir de agora você pode seguir para as próximas aulas para aprender cada vez mais.

## Variáveis

Variáveis são pedacinhos de memória onde armazenamos valores. Sempre que referenciamos o nome de uma variável, o valor é acessado. Definimos uma variável dando um nome a ela e usando o sinal de igual (=) para atribuir um valor.

```py
x = -10 # uma variável do tipo inteiro (int)
y = 3.14 # uma variável do tipo real (float)
escola = "Let's Code" # uma variável literal (string)
primeiraAula = True # uma variável lógica (booleana)
```

Note que o operador igual (=) NÃO possui o mesmo comportamento da matemática. Na matemática, ele é um operador bidirecional: x = 2y seria a mesma coisa que 2y = x. No Python, ele é o que chamamos de um operador de ATRIBUIÇÃO: A expressão à direita do sinal é resolvida e seu resultado é armazenado na variável à esquerda.

## Comentários

```py
# Linhas iniciadas com # são comentários.
# Comentários são ignorados pelo Python e servem para explicar o código.
'''
O símbolo # é um comentário de apenas 1 linha.
Usando 3 aspas simples consecutivas é possível abrir um bloco de comentário
de múltiplas linhas. O bloco se encerra com outras 3 aspas simples.
'''
```

## Operadores aritméticos

```py
# Podemos fazer operações aritméticas simples
a = 2 + 3  # Soma
b = 2 - 3  # Subtração
c = 2 * 3  # Multiplicação
d = 2 / 3  # Divisão
e = 2 // 3 # Divisão inteira
f = 2 ** 3 # Potência
g = 2 % 3  # Resto de divisão

print (a, b, c, d, e, f, g)

# Podemos fazer operações dentro do print

print (a+1, b+1)

#Podemos fazer operações com variáveis não inteiras
nome = input('Digite seu primeiro nome:')
nome = nome + ' Schmitt'
print(nome)
```

## Operadores relacionais

Observe o código abaixo:

```py
comparacao1 = 5 > 3
print(comparacao1)
comparacao2 = 5 < 3
print(comparacao2)
```

Ao ser executado, a saída que teremos na tela será:

```python
True
False
```

Isso ocorre porque 5 é maior que 3. Portanto, comparacao1 recebeu uma expressão cujo valor lógico é **verdadeiro**, portanto seu resultado foi *True*, e o oposto ocorreu para comparacao2.

O Python possui 6 operadores relacionais:

- Maior que: **>**

- Maior ou igual: **>=**

- Menor que: **<**

- Menor ou igual: **<=**

- Igual: **==**

- Diferente:

   

  !=

  > Note que o operador para comparar se 2 valores são iguais é **==**, e não **=**. Isso ocorre porque o operador **=** é o nosso operador de **atribuição**: ele diz que a variável à sua esquerda deve receber o valor da expressão à direita. O operador **==** irá testar **se** o valor à sua esquerda é igual ao valor à sua direita e irá responder *True* ou *False*, como todos os outros operadores de comparação.

## Operadores lógicos

Em alguns casos também precisamos testar se duas ou mais condições são verdadeiras. Para isso utilizaremos as *conjunções lógicas*:

> - **and**: verdadeiro se condição 1 for verdadeira **e** condição 2 for verdadeira
> - **or**: verdadeiro se condição 1 for verdadeira **ou** condição 2 for verdadeira

No exemplo abaixo, o resultado é verdadeiro para comparacao1 e falso para comparacao2.

```py
comparacao1 = 5 > 3 and 6 > 3
comparacao2 = 5 < 3 and 6 > 3
```

Já no exemplo seguinte, tanto comparacao1 quanto comparacao2 retornam o valor verdadeiro.

```py
comparacao1 = 5 > 3 or 6 > 3
comparacao2 = 5 < 3 or 6 > 3
```

Também é possível *negar* uma expressão lógica usando o *not*. Em outras palavras, se `comparacao1 = 5 > 3` é verdadeira, `comparacao1 = not(5 > 3)` será falsa, e vice-versa.

## Outputs

Chamamos de **saídas** ou **outputs** do nosso programa todos os dados que são gerados pelo programa e fornecidos para o usuário.

Já conhecemos a função *print()* que recebe um valor ou uma sequência de valores e realiza a tarefa de imprimí-los na tela.

```py
y = 3.14 # uma variável do tipo real (float)
escola = "Let's Code" # uma variável literal (string)

# Podemos exibir textos na tela e/ou valores de variáveis com a função print().
print('eu estudo na ', escola)
print('pi vale', y)

# Podemos fazer operações dentro do print:
print (y+1, y**2)
```

## Inputs

Já as **entradas** ou **inputs** do nosso programa são as informações que o usuário possui e deve fornecer ao código.

```python
# Podemos ler valores do teclado com a função input().
# Ela permite que a gente passe uma mensagem para o usuário.
nome = input('Digite o seu nome: ')

# Tudo que é lido por input() é considerado uma string (str).
# Para tratar como outros tipos de dados é necessário realizar a conversão:
peso = float(input('Digite o seu peso: ')) # lê o peso como número real
idade = int(input('Digite a sua idade: ')) # lê a idade como número inteiro

print(nome, 'pesa', peso, 'kg e tem', idade, 'anos de idade.')
```

## If

O if testa uma condição:

- se ela for verdadeira, seu conteúdo é executado;
- caso contrário, seu conteúdo é ignorado.

```py
idade = int(input('Digite sua idade:'))
if idade >= 12:
    print('Você pode entrar na montanha russa.')
print('Obrigado por participar.')

altura = float(input('Digite sua altura, em metros:'))
if idade >= 12 and altura >= 1.60:
    print('Você pode entrar na montanha russa.')
print('Obrigado por participar.')
```

Utilizamos um 'tab' antes de cada linha pertencente ao if. No exemplo acima, a linha 'obrigado por participar' sempre será exibida. Já a linha 'Você pode entrar na montanha russa.' só será exibida se a idade digitada for maior ou igual a 12 e a altura digitada for maior ou igual a 1.60.

## Else

Em alguns casos, queremos que o programa escolha entre 2 casos mutuamente exclusivos. Para isso utilizamos o else. O else não possui condição para verificar. O else sempre vem imediatamente após um if e é executado se o if for ignorado.

```py
idade = int(input('Digite sua idade:'))
altura = float(input('Digite sua altura, em metros:'))
if idade >= 12 and altura >= 1.60:
    print('Você pode entrar na montanha russa.')
else:
    print('Você não pode entrar na montanha russa.')
print('Obrigado por participar.')
```

É possível "aninhar" diversos if's e else's. O programa abaixo só deixa a pessoa entrar no brinquedo se tiver idade e altura mínimas:

```py
idade = int(input('Digite sua idade:'))
if idade >= 12:
    resposta = input('Você gostaria de entrar nesta montanha russa?')
    if (resposta == 'sim'):
        print('Por favor, entre!')
    else:
        print('Ok então')
else:
    print('Você não tem idade suficiente para entrar nesse brinquedo.')
```

## Elif

Podemos testar diversos casos mutuamente exclusivos utilizando o 'elif'.

O comando elif é a contração de "else if" - ou seja, caso um if não seja executado, você pode propor uma nova condição para ser testada.

```py
exercicios = int(input('Quantos exercícios de Python vc já fez?'))

if exercicios > 30:
    print('Já está ficando profissional!')
elif exercicios > 20:
    print('Tá indo bem, bora fazer mais alguns!')
elif exercicios > 10:
    print('Vamos tirar o atraso?')
else:
    print('Xiiii...')
```

Observe que a união das 3 estruturas (if-elif-else) implica que seu código seguirá apenas um dos possíveis caminhos, obrigatoriamente.

# While

O while é bastante parecido com um 'if': ele possui uma expressão, e é executado caso ela seja verdadeira. Mas o if é executado apenas uma vez, e depois o código segue adiante.

O while não: ao final de sua execução, ele torna a testar a expressão, e caso ela seja verdadeira, ele repete sua execução.

```py
horario = int(input('Qual horario é agora? '))

# Testando a condição uma única vez com o if:
if 0 < horario < 6:
    print('Você está no horario da madrugada')
else:
    print('Você nao está no horario da madrugada')

# Testando a condição em loop com o while:
while 0 < horario < 6:
    print('Você está no horario da madrugada')
    horario = horario + 1
else:
    print('Você nao está no horario da madrugada')

# O while permite continuar decrementando o número de pipocas até chegar em 0:
num_pipocas = int(input('Digite o numero de pipocas: '))

while num_pipocas > 0:
    print('O numero de pipocas é: ', num_pipocas)
    num_pipocas = num_pipocas - 1
```

## Validação de entrada

Uma utilidade interessante do while é obrigar o usuário a digitar apenas entradas válidas.

```py
# o exemplo abaixo não aceita um salário menor do que o mínimo atual:
salario = float(input('Digite seu salario: '))
while salario < 998.0:
    salario = float(input('Entre com um salario MAIOR DO QUE 998.0: '))
else:
    print('O salario que você entrou foi: ', salario)
# o exemplo abaixo só sai do loop quando o usuário digitar "OK":
resposta = input('Digite OK: ')
while resposta != 'OK':
    resposta = input('Não foi isso que eu pedi, digite OK: ')
```

## Contador

Todo tipo de código que deve se repetir várias vezes pode ser feito com o while, como somar vários valores, gerar uma sequência etc. Nestes casos, é normal utilizar um contador:

```py
# Declaramos um contador como 0:
contador = 0
# Definimos o número de repetições:
numero = int(input('Digite um numero: '))
# Rodamos o while até o contador se igualar ao número de repetições:
while contador < numero:
    print(contador)
    contador = contador + 1
```

## Break

Um jeito de forçar um loop a ser interrompido é utilizando o comando 'break'. O loop abaixo em tese seria infinito, mas se a condição do if for verificada, o break é executado e conseguimos escapar do loop:

```py
while True:
    resposta = input('Digite OK: ')
    if resposta == 'OK':
        break
```