[Link para os scripts criado]()

# Utilizando ODBC em Node.js

ODBC (Open Database Connectivity) é uma API que permite acesso a vários bancos de dados usando uma única interface. Em Node.js, é possível utilizar o módulo odbc para interagir com bancos de dados via ODBC.

## Instalação
De início, é preciso instalar o pacote `odbc` via npm:
~~~
npm install odbc
~~~

## Exemplo de uso em Node.js
~~~
const odbc = require('odbc');

const connectionString = 'DSN=myDataSource;UID=myUsername;PWD=myPassword'; // Substitua pelos seus próprios dados
const connection = odbc.connect(connectionString);

const query = 'SELECT * FROM myTable';

connection.query(query, (error, result) => {
  if (error) {
    console.error('Erro ao executar a consulta:', error);
    return;
  }
  console.log('Resultado da consulta:', result);
});

connection.close((error) => {
  if (error) {
    console.error('Erro ao fechar a conexão:', error);
    return;
  }
  console.log('Conexão fechada com sucesso.');
});
~~~

# Utilizando prisma como ORM em Node.js

Prisma é um ORM (Object-Relational Mapping) moderno para Node.js e TypeScript, que oferece uma maneira fácil e segura de interagir com um banco de dados relacional. Ele permite que você escreva consultas de banco de dados em uma sintaxe amigável e tipo seguro, facilitando a manipulação de dados no seu aplicativo Node.js.

## Instalação

Para começar a usar o Prisma, é possível instalá-lo via npm:

~~~
npm install @prisma/cli @prisma/client
~~~