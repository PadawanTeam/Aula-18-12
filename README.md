# Aula-18-12
Resumo da Aula de 18-12, iniciando com banco de dados

#Iniciando com banco de dados (MongoDb e MySql)

##Neste "capitulo" vamos ter uma introdução a banco de dados.

------------------------------------------------------------------------------------------------------------------------------------------

###O que é banco de dados?

Como o próprio nome diz, um banco de dados consiste em banco para armazenarmos dados.

Os dados podem ser qualquer coisa que possa ser armazenado para algum fim, geralmente compor uma informação. Por exemplo,
podemos armazenar um número (1997), sozinho ele não representa nada, mas se ele for acompanhado da descrição "Ano de nascimento: ", está
compondo uma informação (o ano de nascimento de alguem, em 1997).

Os bancos de dados são parecidos com planilhas do excell, para cada coluna podemos adicionar N dados, pore exemplo, digamos que temos
a coluna anoNascimento, em cada linha abaixo dessa coluna, teremos informações diferentes. Para construirmos uma informação, vamos 
armazenar além do ano de aniversário, um nome, assim teremos uma informação completa (nome e ano de Nascimento)!

| nome | anoNascimento |
|------|-----------------|
| Felipe | 1993 |
|Dracula| 1820 |
|João|2000|

Com essas informações em nosso banco de dados, podemos por exemplo, validar se o usuário cadastrado, tem idade para 
dirigir (if dataNascimento>=18), dentre outras validações ou simplesmente para fins de cadastro/exibição.

Os bancos de dados, assim como um programa na maioria das linguagens, tem tipos diferentes de dados, por exemplo, no java temos
String para textos, int para numeros inteiros, etc, no banco de dados também temos esses tipos (a sintase varia de banco pra banco).

Temos também alguns modificadores, como NOT_NULL (o campo não pode ficar vazio), AUTO_INCREMENT (A cada registro novo ele assume +1),
PRIMARY_KEY (É a chave primária, para fazer relacionamento em outras tabelas), FOREIGN_KEY (Seria uma chave secundária, também
para fins de relacinamento).

####Exemplo de relacionamento

PRIMARY KEY, é o campo chave da tabela, é o campo cujo valor não repete.

FOREIGN KEY, é o campo na tabela que se relaciona com o campo chave(PRIMARY KEY) de outra tabela.

ex:
Tabela PAI:


|cod|Nome|
|---|----|
|1 | Carlos|
|2 | Eduardo|


obs.: o campo cod é PRIMARY KEY

Tabela FILHO


|cod | nome | cod_pai|
|----|------|--------|
|1 | Carlinhos | 1|
|2 | Carlos Jr | 1|
|3 | Eduardinho | 2|

obs.: o campo cod é PRIMARY KEY, e o campo cod_pai é FOREIGN KEY que se relaciona com a chave primaria da tabela PAI.

(Exemplo retirado de um forum de PHP).

------------------------------------------------------------------------------------------------------------------------------------------
###Um pouco sobre mongoDb

O mongoDb é um banco de dados não relacional, que trabalha com documentos/objetos json, o mesmo tipo de objetos que criamos no dia a dia da 
programação em js!

Exemplo de objeto json:

```javascript
  {
  Nome: "João",
  anoNascimento: 1997
  }
  ```
  Ao acessar a variável nome, teremos o resultado João e ao acessar anoNascimento teremos 1997!
  

------------------------------------------------------------------------------------------------------------------------------------------
###Nos familiarizando com SQL e alguns comandos

Quando vamos programar em qualquer linguagem, temos comandos e frammeworks que nos auxiliam  no tratamento dos dados, escrita das
funções e métodos, comandos para aplicar lógica ao nosso programa etc, tudo isso deve ser escrito nos padrões que foram criados,
por exemplo, um if sempre será um if (onde validamos uma condição e fazemos algo caso seja verdadeiro e outra coisa se for falso).
Então, com o SQL não é diferente, temos comandos especificos que servem para funções especificas, vamos conhecer um pouco mais das mais
famosas:

####CREATE TABLE

O create table cria as tabelas em nosso banco, podemos criar já com as nossas colunas, por exemplo:

```javascript
CREATE TABLE tabelaX
(
nome VARCHAR(55),
anoAniversario INT(10)
);
```

Note que passamos o comando SQL, nome da tabela seguido pelo nome de cada coluna com o seu respectivo tipo de dado que vai aceitar e o
seu tamanho.

####INSERT

O insert é a instrução para inserir dados em uma tabela, exemplo:

```javascript
INSERT INTO tabelaX VALUES(
'Felipe',1993);
```
Note que estamos passando o primeiro valor (um nome, varchar), segundo valor (um inteiro) dizendo que estão na tabelaX, criada 
anteriormente


####SELECT

O select é a instrução para trazermos os conteudos das colunas em nossas tabelas!

SELECT * FROM tabelaX

O resultado seria:

| nome | dataNascimento |
|------|-----------------|
| Felipe | 1993 |

O asterisco representa o "TUDO", nessa instrução, pedimos para selecionar TODOS os dados da tabelaX

####UPDATE

O update é a instrução utilizada para atualizar as colunas em uma tabela, ou seja, eles já existem e queremos atualizar!

Exemplo:
```javascript
UPDATE tabelaX SET nome = "Felipe Alencar", anoNascimento = 1990.
```

------------------------------------------------------------------------------------------------------------------------------------------

###Nos familiarizando com MongoDB

Como o mongoDB utiliza objetos json, os comandos são diferentes do SQL, em vez de usarmos comandos como SELECT, INSERT, utilizamos funções! Como no javascript (ou até mesmo java) para chamarmos funções (ou métodos, no java), utilizamos sempre o "." (Ponto), funções 
são identificadas com "()" no final!


####Criando um Banco de Dados


para criarmos um banco:
```javascript
use mercado
```

A partir desse momento, já estamos utilizando uma base nova, mas se nenhuma alteração for feita e o usuário sair da 
aplicação, ela será simplesmente apagada (pois não foi salva), ao inserir dados, ela se salva.


####Inserindo dados (Criando collection)

Nossas collections são como as tabelas em banco de dados que utiliza SQL, para criarmos elas, utilizamos uma função que 
se chama insert()

```javascript
db.mercado.insert({
                    yogurte:'Danone',
                    cerveja:'Heineken',
                    pao:'Pullman'
                    })
```

Note que estamos usando a função insert(), passando um objeto json dentro dela (Reconhecido pelo {}) e já colocando
dados dentro dele!

####Buscando dados

Para burcas os dados dentro das nossas collections, também utilizamos uma função, ela se chama find():

```javascript
db.mercado.find()
```
o resultado será:
```javascript
{ "_id" : ObjectId("5856fed84b5807ff7c76fd23"), "yogurte" : "Danone", "cerveja" : "Heineken", "oao" : "Pullman" }
```


------------------------------------------------------------------------------------------------------------------------------------------

