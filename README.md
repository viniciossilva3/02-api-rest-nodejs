<h1 align="center">
First RESTFul API with Fastify
</h1>

### First step :

- Install the [Node.js](https://nodejs.org/en/download), is a requirement for the next steps.

### Second step:

- Create a directory to save your project using the terminal.

```bash
#Create a directory using the terminal
$ mkdir your-directory-name
```

- Create a directory with a src name inside your directory

```bash
#Create a directory with a src name inside your directory (your-directory/src)
$ mkdir src
```

- Create a file with server.ts name inside the src directory

```bash
#Create a file with server.ts name (your-directory/src/server.ts)
$ touch server.ts
```

### Third step:

- Create a package.json for your project using the following command in the terminal:

```bash
#Initialize your project using npm
$ npm init -y
```

### Fourth step:

- Install Typescript dependency, which is required for the use of typescript code in our project.

```bash
#Install Typescript how a development dependency
$ npm i -D typescript
```

### Fifth step:

- Create the typescript configuration file.

```bash
#Create the file for typescript configurations
$ npx tsx --init
```

### Seventh step:

- Update the target property within the tsconfig.json file to the following value to enable code transpilation to a newer JavaScript version:

```bash
"tsconfig.json"
{
    "target": "es2020", //Change to 2020 or other newest version
}
```

### Eighth step:

- Now we go to transpile your typescript code to a javascript version.

```bash
#Transpile your code in typescript to a javascript  code
$ npx tsc src/index.ts
```

### Ninth step:

- Now install the Fastify dependency to start your project.

```bash
#Install Fastify dependency
$ npm i fastify
```

### Tenth step:

- Write the initial code on the server.ts file based on the following example:

```bash
#src/server.ts
import fastify from 'fastify';

const app = fastify();

// GET, POST, PUT, PATCH, DELETE

// http://localhost:3333/hello

app.get('/hello', () => {
  return 'Hello World';
});

app
  .listen({
    port: 3333,
  })
  .then(() => {
    console.log('HTTP Server Running!');
  });
```

### Eleventh step:

- Transpile your code typescript to the javascript code using npx.

```bash
#Transpile your typescript code to javascript code
$ npx tsc src/server.ts
```

### Twelfth step:

- Install types for use from Typescript in the Node.js

```bash
#Install node types module for use node types with typescript
$ npm i -D @types/node
```

### Thirteenth step:

- Install TSX to transpile the typescript code to javascript code and execute your code automatically.
- Please use only on development for the best performance from your code don't use this in production mode.

```bash
#Install tsx to transpile and execute your code automatically
$ npm i -D tsx
```
### Fourteenth step:

- Create a new script on the package.json to automate execution from the TSX on your project.

```bash
#Create a new dev script on the package.json
"package.json"
{
    "scripts": {
    "dev": "tsx watch src/server.ts"
  },
}
```
### Fifteenth step:

- Install ESLint dependency and EsLint Extension for improved code consistency and error detection.
- Install EsLint config from Rocketseat to help and standardize your code styling.

```bash
# ESLint to improve code consistency and error detection. This helps identify and fix issues in your code..
$ npm i -D eslint  @rocketseat/eslint-config
``` 
### Sixteenth step:

- Create a .eslintrc.json file on workspace of your project and add the following code:

```bash
".eslintrc.json"
{
    "extends": [
        "@rocketseat/eslint-config/node"
    ]
}
```
### Seventeenth step:

- Create a new script to detect and fix lint errors  automatically and standardize your code styling.

```bash
"package.json"
{
    "scripts": {
    "lint": "eslint src --ext .ts --fix"
  },
}
```
### Eigteenth step:

- Install and configure the [Knex](https://knexjs.org/guide/#node-js) query builder. 
- The Knex Installation is for help you with  easy write queries on your database without write sql language.

```bash
#Install Knex and the driver for the database chosen for you, is the sqlite in this case
$ npm knex sqlite3
```
### Nineteenth step:

- Create de database configuration file on src directory.
- Create a database.ts file and add the following configuration for the sqlite3 connection.

```bash
"database.ts"
#Database configuration
import { knex as setupKnex, Knex } from 'knex'

export const config: Knex.Config = {
  client: 'sqlite',
  connection: {
    filename: './db/app.db',
  },
  useNullAsDefault: true,
  migrations: {
    extension: 'ts',
    directory: './db/migrations',
  },
}
export const knex = setupKnex(config)
```
- Create the knexfile.ts on workspace for export the database config.

```bash
"knexfile.ts"
import { config } from './src/database'

export default config
```
### Twentieth step:
- Create a new script on your package.json with the following command for be posible read and run tsx files with knex:

```bash
"knex": "node --import tsx ./node_modules/knex/bin/cli.js"
``` 
- For create the migrations file you can execute the following steps on your terminal.

```bash
#Create migrations file using the knex
$ npm run knex migrate:make name-your-file
``` 
- Add the code for your migration with the data for the your table and columns with the following example.
- The Up function is for the add all created table and columns.
- The Down function is for the remove all the table and columns created from the Up function.

```bash
"migration-create-transaction.ts"
import type { Knex } from 'knex'

export async function up(knex: Knex): Promise<void> {
  await knex.schema.createTable('transactions', (table) => {
    table.uuid('id').primary()
    table.text('title').notNullable()
    table.decimal('amount', 10, 2).notNullable()
    table.timestamp('created_at').defaultTo(knex.fn.now()).notNullable()
  })
}

export async function down(knex: Knex): Promise<void> {
  await knex.schema.dropTable('transactions')
}
```
- Execute migration for the create tables and columns on your database.

```bash
#Execute migration from the up function with queries for your database
$ npm run knex migrate:latest
```
- Execute rollback for remove the last created tables and columns from the up function.

```bash
#Execute migration from the up function with queries for your database
$ npm run knex migrate:rollback
```
## dotenv
- Now install dotenv package on your project and install too the [DotENV](https://open-vsx.org/extension/mikestead/dotenv) extension for the your VSCODE.

```bash
#Install dotenv on your project
$ npm install dotenv
```
- Create the enviroment variables file from your project.

```bash
".env"
DATABASE_URL="./db/app.db"
```
- Create the enviroment variable file example for your project.
- For security purposes, do not create it containing passwords or other important keys for your application, remember that it is just an example file so that future developers know what variables are necessary to use the application.

```bash
".env.example"
DATABASE_URL="your-database-url-here"
```
- Add the .env file to the .gitignore to prevent your file be uploaded on your github containing important data.

```bash
".gitignore"
.env
```
