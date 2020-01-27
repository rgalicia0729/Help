# Curso de GraphQL

## Introducción al curso y prerequisitos del curso

Bienvenido al Curso Básico de GraphQL. En este curso el profesor Adrián Estrada, desarrollador Node.js trabajando para NodeSource, te mostrará las bases de GraphQL y por qué es tan importante en el mundo.

Para este curso es necesario tener buenas bases de Node y conocimientos de bases de datos no relacionales como MongoDB. Puedes checar el Curso Básico de Node.js y el Curso Básico de MongoDB.

## ¿Qué es GraphQL?

En esta clase el profesor Adrián Estrada nos explica qué es GraphQL, su importancia y las ventajas que tiene.

GraphQL es un nuevo paradigma aplicado para el intercambio de información entre diferentes aplicaciones. Anteriormente existían protocolos como CORBA, SOAP, RPC y el más reciente y utilizado REST. GraphQL creado en el 2015 por Facebook puede ser visto como una evolución al protocolo REST.

## Schema y types

El Schema es la base de una API en GraphQL, es el encargado de describir todos los tipos de información que va a contener.

Para la creación de este proyecto usaremos una herramienta llamada npx, para ello primero debes instalarlo con el comando:

    npm i -g npx

Una vez instalado, dentro de la carpeta de nuestro proyecto vamos a correr el siguiente comando:

    npx license mit > LICENSE && npx gitignore node && git init && npm init -y

Ya que termina de correr el comando es momento de añadir la dependencia de GraphQL a nuestro proyecto:

    npm i graphql

Dentro de GraphQL contamos con distintos tipos de datos escalares:
    
- String
- Int
- Float
- Boolean
- ID

## Queries y Resolvers

Una query permite ejecutar una petición al API, dentro de una query debes indicar la consulta que quieres ejecutar y los campos que deseas obtener. GraphQL te va a devolver la información que solicitaste dentro del objeto data.

El resultado de tu petición no se va a ejecutar de manera mágica, para ello debes definir el objeto resolvers, este objeto va a contener una propiedad del mismo nombre que la query que va a resolver o ejecutar.

https://graphql.org/learn/queries/

## Sirviendo el API en la web

Ya viste que nuestra API funciona a través de la línea de comandos, pero necesitamos que está funcione dentro de la web, para ello necesitas de las dependencias de express y un middleware de GraphQL, vamos a instalarlo con el siguiente comando:

    npm i express express-graphql

Para evitar el proceso de detener nuestro servidor cada que ejecutamos un nuevo cambio vamos a utilizar la dependencia de desarrollo Nodemon:

    npm i nodemon -D

## Custom Types

Para este proyecto vamos a seguir el estándar de estilos Standard, para instalarlo corremos el siguiente comando:

    npm i standard -D

GraphQL nos permite configurar nuestros propios tipos de datos, estos deben tener la siguientes sintaxis:

  type <Nombre del tipo> {
    propiedad: Tipo de dato
  }

Dentro de nuestros tipos de datos podemos configurar un campo de un tipo como obligatorio con el signo “!”, quedando por ejemplo:

  type Course {
    title: String!
  }
