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
