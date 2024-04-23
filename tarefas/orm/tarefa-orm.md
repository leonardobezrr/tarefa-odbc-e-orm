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
## Configuração

Após instalar o Prisma, é preciso configurar seu arquivo `schema.prisma` para definir o modelo de dados e a conexão com o banco de dados. Aqui está um exemplo de arquivo `schema.prisma`:

~~~
// schema.prisma

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id       Int      @id @default(autoincrement())
  name     String
  email    String   @unique
  posts    Post[]
}

model Post {
  id        Int      @id @default(autoincrement())
  title     String
  content   String
  published Boolean  @default(false)
  author    User?    @relation(fields: [authorId], references: [id])
  authorId  Int?
}
~~~
## Exemplo de Uso

Aqui está um exemplo simples de como usar o Prisma em um aplicativo Node.js:

~~~
const { PrismaClient } = require('@prisma/client');

const prisma = new PrismaClient();

async function main() {
  // Criar um novo usuário
  const newUser = await prisma.user.create({
    data: {
      name: 'John Doe',
      email: 'john@example.com',
    },
  });
  console.log('Novo usuário criado:', newUser);

  // Consultar todos os usuários
  const allUsers = await prisma.user.findMany();
  console.log('Todos os usuários:', allUsers);
}

main()
  .catch((error) => {
    console.error('Erro no aplicativo:', error);
  })
  .finally(async () => {
    await prisma.$disconnect();
  });
~~~
