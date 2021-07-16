Clique [aqui](https://s3-sa-east-1.amazonaws.com/lcpi/9653c5a5-9a32-49b2-86b2-0e527bbbdc12.txt) para acessar o arquivo dom_casmurro_cap_1.txt (clique com o botão direito do mouse e depois em "Salvar link como").

## Arquivos em Python

O Python possui algumas funções prontas para manipular arquivos binários puros (onde, conhecendo a estrutura interna de qualquer formato, podemos salvar qualquer tipo de arquivo) e para manipular arquivos de texto (onde os binários são decodificados como *strings*).

Focaremos no básico de manipulação de arquivo de texto, pois, na prática, quando formos trabalhar com arquivos mais complexos, é provável que usaremos bibliotecas específicas para lidar com eles, e elas já terão funções próprias para ler e salvar esses arquivos da maneira correta.

## Abrindo e fechando arquivos

Podemos criar arquivos novos ou abrir arquivos já existentes utilizando a função *open*. Ela possui 2 argumentos: o caminho do arquivo e o modo de operação.

| Modo     | Símbolo | Descrição                                                    |
| -------- | ------- | ------------------------------------------------------------ |
| *read*   | r       | lê um arquivo existente                                      |
| *write*  | w       | cria um novo arquivo                                         |
| *append* | a       | abre um arquivo existente para adicionar informações ao seu final |
| *update* | +       | ao ser combinado com outros modos, permite alteração de arquivo já existente (ex: r+ abre um arquivo existente e permite modificá-lo) |

Após abrirmos (ou criarmos) um arquivo, podemos realizar diversas operações. Ao final de todas elas, devemos **fechar** o nosso arquivo usando a função *close*. Essa etapa é importante por 2 motivos:

1. Se alteramos o arquivo mas não o fechamos, as alterações não serão salvas;
2. Se esquecemos de fechar um arquivo, outros programas podem ter problemas ao acessá-lo.

## Roteiro básico

Vamos seguir os seguintes passos para manipular nossos arquivos:

1. Abrir ou criar um arquivo:

```py
arquivocriado = open("criado.txt", "w")
```

A linha de comando acima abre (ou cria se não existe) um arquivo chamado "criado.txt" para escrita ("w", de write) e guarda na variável "arquivocriado" as informações para manipulá-lo.

```py
arquivolido = open("teste.txt", "r")
```

A linha acima lê ("r", de read) um arquivo já existente chamado "teste.txt" e guarda na variável "arquivolido" as informações para manipulá-lo.

1. Carregar os dados do arquivo (leitura)

```py
dados = arquivolido.read()
print(dados)
```

A função read() retorna todo o conteúdo do arquivo como uma string.

Precisamos carregar o conteúdo do arquivo em algum formato que sabemos trabalhar. A read() carrega o conteúdo de um arquivo de texto em uma string.

1. Manipular os dados do arquivo (escrita)

```py
arquivocriado.write("linha 1")
arquivocriado.write("linha 2")
arquivocriado.write("linha 3")
```

Em casos mais complexos, iremos manipular o conteudo LIDO no passo anterior para posteriormente reescrevê-lo. Em outros mais simples, podemos escrever diretamente no arquivo.

1. Fechar o arquivo

```py
arquivocriado.close()
arquivolido.close()
```

Essa etapa é muito importante para garantir a integridade dos novos dados no arquivo. As modificações são salvas somente ao fechar o arquivo.

## Comando with

Um jeito mais inteligente de se trabalhar com arquivos é utilizar a sintaxe do "with". Ele garante que após a finalização do bloco, o arquivo será fechado.

```python
with open('teste.txt', 'r') as arquivolido:
   dados = arquivolido.read()
   print(dados)
```

É possível ler o arquivo linha a linha, como no exemplo:

```py
with open('teste.txt', 'r') as arquivolido:
   linha = arquivolido.readline()
   while linha != '':
       print(linha, end='')
       linha = arquivolido.readline()


# OU

with open('teste.txt', 'r') as arquivolido:
    for linha in arquivolido:
        print(linha, end='')
```

O mesmo pode ser feito para escrever no arquivo:

```py
with open('teste.txt', 'r') as arquivolido:
    with open('copiateste.txt', 'w') as arquivocriado:
        for linha in arquivolido:
            arquivocriado.write(linha)
```

No comando acima, as linhas do arquivo "teste.txt" são copiadas e salvas no arquivo "copiateste.txt".

Clique [aqui](https://s3-sa-east-1.amazonaws.com/lcpi/3ada13e0-1fd2-4602-9786-24bc0b16b2df.csv) para baixar o arquivo brasil_covid.csv.

## CSV

O formato CSV (Comma Separated Values, ou Valores Separados por Vírgula) é um arquivo de texto que representa dados em forma de tabela de forma simples.

Cada linha do arquivo de texto é uma linha da tabela, e as colunas são separadas por vírgulas.

1, 2, 3, 4

5, 6, 7, 8

9, 10, 11, 12

Poderíamos manipular estes arquivos diretamente usando as funções de arquivo vistas anteriormente. Um fator complicador é que o formato CSV não é bem padronizado: apesar do nome, é normal que outros separadores sejam usados ao invés de vírgula, como ";", para permitir que a vírgula seja usada em um campo. Idem para a separação entre linhas. Existe um módulo em Python para manipular arquivos CSV que nos ajuda a tratar essas diferenças. Todo programa que for utilizar o módulo CSV deverá importá-lo em seu início através do comando: import csv

```py
import csv

with open('tabelaExemplo.csv', 'w') as arquivo:
    escritor = csv.writer(arquivo, delimiter = ';', lineterminator = '\n') #criando um escritor
    lista = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    escritor.writerows(lista) # writerows escreve cada "sublista" da lista como uma linha

with open('tabelaExemplo.csv', "r") as arquivo:
    leitor = csv.reader(arquivo, delimiter = ';', lineterminator = '\n') #criando um leitor
    print("O conteúdo do arquivo é:")
    print(leitor)
    for linha in leitor:
        print(linha)
```

## DictReader e DictWriter

Podemos também trabalhar com dicionários, nos quais a primeira linha é lida como a chave e as demais são os respectivos valores:

```py
import csv

with open('email.csv', 'r') as emails:
    leitor = csv.DictReader(emails, delimiter=';') #a primeira linha é lida como um cabeçalho
    for linha in leitor:
        print(linha['Login email']) #podemos chamar um valor específico de cada linha pela chave no cabeçallho


with open('names.csv', 'w', newline='') as csvfile:
    chaves = ['first_name', 'last_name'] # definimos o cabeçalho
    writer = csv.DictWriter(csvfile, fieldnames=chaves) # especificamos o cabeçalho

    writer.writeheader() # escrevemos o cabeçalho
    writer.writerow({'first_name': 'Senhor', 'last_name': 'Batata'}) # escrevemos linhas com as chaves e valores
    writer.writerow({'first_name': 'Will', 'last_name': 'Smith'})
    writer.writerow({'first_name': 'Elon', 'last_name': 'Musk'})
```

Clique [aqui](https://www.exchangerate-api.com/docs/free-exchange-rate-api) para acessar a documentação da Exchange Rate API.

## Application Programming Interface

Hoje em dia é muito comum que diferentes aplicações consumam dados pela internet, muitas vezes dados providenciados por terceiros. Por exemplo, um aplicativo de entrega de alimentos pode usar dados de geolocalização do Google para localizar restaurantes próximos ao usuário e exibir a rota percorrida pelo entregador.

Como as aplicações podem rodar em diferentes plataformas (Windows, Android, MacOS, iOS, um navegador de internet...), é importante estabelecer uma linguagem comum para que todos consigam consumir esses dados.

Essa "linguagem comum" é o que chamamos de API: *Application Programming Interface*. A organização que disponibiliza os dados estabelece algumas "regrinhas" para fazermos requisições, e em contrapartida ela garante que os recursos fornecidos também seguirão certos padrões, facilitando a vida dos programadores.

Portanto, quando decidimos utilizar uma API, a primeira coisa que precisamos fazer é estudar sua documentação. Vejamos alguns dos pontos mais relevantes para procurar.

Todos os exemplos de requisição que mostraremos aqui podem ser colados em seu navegador ou estudados usando um `requests.get` no Python e imprimindo seu campo *text*.

### URI base

Várias APIs fornecem um "endereço base". Todas as suas requisições incluirão esse endereço, e ao final dele nós colocamos detalhes específicos para cada um dos recursos disponíveis.

Por exemplo, na *AlphaVantage* (https://www.alphavantage.co/), uma API de dados de bolsas de valores e criptomoedas, a URI base é:

```
https://www.alphavantage.co/query?
```

Após a interrogação nós colocaremos os campos para nossa consulta. Por exemplo, para fazer uma consulta sem autenticação para valores da IBM, de 5 em 5 minutos, o endereço completo fica:

```
https://www.alphavantage.co/query?function=TIME_SERIES_INTRADAY&symbol=IBM&interval=5min&apikey=demo
```

Note o formato com `&NomeDoCampo=ValorDoCampo`. Ele é bastante comum. Outro formato bastante comum é o de "subdiretórios".

Um exemplo é a PokéAPI. A URI base é:

```
https://pokeapi.co/api/v2/
```

Para procurar por pokémons, adicionamos pokemon/. Em seguida, podemos colocar números (índices) ou nomes de Pokémon, como:

```
https://pokeapi.co/api/v2/pokemon/ditto/
https://pokeapi.co/api/v2/pokemon/25
```

Se ao invés de pokémons estivéssemos interessados em tipos de pokémon, usaríamos *types/* e o nome ou índice do tipo desejado:

```
https://pokeapi.co/api/v2/type/ghost
```

### Formato

#### Tipo de dado

Algumas APIs possuem formatos fixos de dados. Outros permitem que você escolha. É comum, por exemplo, que uma API permita que você escolha entre JSON, XML, CSV e/ou outros formatos.

Caso você tenha entrado no *AlphaVantage* e se registrado para obter uma chave (falaremos mais adiante), você pode especificar, por exemplo, que gostaria de resultados no formato CSV:

```
https://www.alphavantage.co/query?function=TIME_SERIES_INTRADAY&symbol=IBM&interval=5min&dataformat=csv&apikey=demo
```

Substitua "demo" por sua chave no exemplo acima e ele funcionará.

#### Schema

É bastante comum que as APIs disponibilizem um "modelo" genérico de como será formatado o seu JSON, XML etc para que os desenvolvedores saibam quais campos esperar e quais tipos de dados serão possíveis para cada campo. Por exemplo:

```
{
    'nome':string,
    'pontuacao':integer
}
```

### Autenticação

Outro aspecto importante é a autenticação. Enquanto algumas APIs são grátis, outras são pagas. Ainda temos algumas híbridas: você pode gratuitamente acessar certos recursos, ou consumir um certo volume de dados, e acima disso você deverá pagar. Os dois modelos mais comuns de autenticação:

- Chave: ao fazer seu registro, você recebe uma chave que será inclusa na requisição, como é o caso do *AlphaVantage*.
- OAuth: um esquema um pouco mais complexo onde são combinados códigos de autorização, identificação do cliente e segredo do cliente em um `POST`, e o servidor cria uma sessão por um tempo limitado e fornece o ID da mesma. APIs de gigantes da internet (como Google e Facebook) costumam usar esse modelo.

### Rate limiting

Um dado parcialmente relacionado ao item anterior. As APIs costumam limitar o número de requisições que você pode fazer em um instante de tempo (3 requisições por minuto, 10000 requisições por dia etc). Temos dois motivos:

- Segurança: evitar uma sobrecarga no servidor deles que possa indisponibilizar a API para todos os usuários.
- Venda de planos: várias APIs pagas possuem diferentes planos de pagamento. Os planos mais caros costumam permitir mais requisições do que os mais baratos ou gratuitos.

### Wrappers

Algumas APIs possuem tantas buscas diferentes e os resultados podem ser tão complexos que mesmo vindo em formatos simples como JSON pode ser um pouco trabalhoso montar as requisições e isolar os dados que queremos. Por conta disso, frequentemente são fornecidas *wrapper libraries*: bibliotecas escritas em linguagens de programação específicas que já trazem classes e funções prontas para fazer requisições automaticamente e já quebrar o resultado em objetos fáceis de serem utilizados. Elas também costumam oferecer alguns benefícios adicionais, como *caching*: de tempos em tempos a base de dados é totalmente ou parcialmente baixada por completo e salva localmente, o que ajuda a economizar requisições e, consequentemente, uso de dados (bastante útil considerando em usuários de dispositivos móveis, por exemplo).

### Sandbox

Várias APIs possuem no mesmo site de sua documentação uma área conhecida como *sandbox*, onde você pode simular requisições no próprio navegador e ver não só a resposta formatada, como informações sobre como montar aquela requisição em software.

Aqui podemos observar a área de *sandbox* para fazer consultas de gastos por meio de cartão de pagamento do Portal da Transparência do governo federal. Note que ele mostra o *schema* e apresenta campos para preenchermos as buscas.

![img](https://s3-sa-east-1.amazonaws.com/lcpi/449b5eed-9152-4bf6-85c5-c2f42992cc66.png)

E aqui, o resultado: ele gera o endereço completo para a busca baseado nos valores preenchidos nos campos e mostra a resposta formatada.

![img](https://s3-sa-east-1.amazonaws.com/lcpi/558def2b-d0a6-4ed8-8902-8cafb6ed560e.png)

## Consumindo APIs em Python

As APIs são meios de nos conectarmos a recursos na internet. Portanto, já possuímos as ferramentas na mão desde os capítulos anteriores. Você irá construir a lógica para decidir o que você irá buscar/consultar, montará uma *string* seguindo o formato indicado pela documentação da API (como todos os exemplos deste capítulo). Em seguida você tratará a resposta de acordo:

- Se for JSON, utilize o método *json* da própria *requests*.

- Se for CSV, utilize o módulo *CSV* estudado anteriormente.

- Se for XML, podemos utilizar o módulo *BeautifulSoup*, que não será estudado aqui.

- Para outros formatos, provavelmente a solução mais fácil será baixar um módulo preparado para lidar com eles.

  > **Descobrindo APIs:** tem boas ideias e gostaria de saber se existe uma boa API para ajudar? Confira alguns bons repositórios de API organizados por categoria:
  >
  > https://github.com/n0shake/public-apis
  >
  > https://github.com/public-apis/public-apis
  >
  > https://any-api.com/
  >
  > Sites de governos costumam ter uma grande riqueza de dados também. Segue abaixo algumas sugestões (oficiais ou mantidas por voluntários) com dados do Brasil como um todo. Experimente buscar por bases de dados de sua cidade ou estado!
  >
  > http://www.transparencia.gov.br/swagger-ui.html
  >
  > http://www.dados.gov.br/
  >
  > https://brasil.io/home/