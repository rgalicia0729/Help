# Curso de Backend con Node.js

https://platzi.com/clases/1646-backend-nodejs/22026-creando-tu-primer-servidor-con-expressjs/

## ¿Qué es Express.js y para qué sirve?

Express.js es un framework para crear Web Apps, Web APIs o cualquier tipo de Web Services, es libre bajo la licencia MIT.

Express es muy liviano y minimalista además de ser extensible a través de Middlewares.

Los Middlewares interceptan el request y el response para ejecutar una acción en medio.

## Crear un servidor con Express

Para iniciar un proyecto con express, lo mas recomendable es crear un archivo package.json, lo puedes hacer de la siguiente manera:

    npm init -y

Agregar un script en el package.json para developer y production de la siguiente manera:

```json
{
  "dev": "DEBUG=app:* nodemon index",
  "start": "NODE_ENV=production node index"
}
```

Agregar una configuración de EsLint para el diseño del codigo, para esto creamos un archivo con el nombre de .eslintrc y agregamos lo siguiente:

```json
{
  "parserOptions": {
    "ecmaVersion": 2018
  },
  "extends": ["eslint:recommended", "prettier"],
  "env": {
    "es6": true,
    "node": true,
    "mocha": true
  },
  "rules": {
    "no-console": "warn"
  }
}
```

Luego vamos aconfigurar prettier para formatear nuestro codigo, de la siguiente manera:

```json
{
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
```

Para instalar express lo hacemos de la siguiente manera:

    npm i -S express

Vamos a instalar una dependencia para manejo de variables de entorno llamada dotenv.

    npm i -S dotenv

Luego vamos a instalar las dependencias de desarrollo, estaso son dependencias que solo se van a utilizar miestras estamos desarrollando nuestro proyecto, vamos a instalar las siguientes.

    npm i -D nodemon eslint eslint-config-prettier eslint-plugin-prettier prettier

Para que nuestro codigo realice el formateo automatico cada vez que se hace commit y se sube al repositorio vamos a instalar un hook:

    npx mrm lint-staged
