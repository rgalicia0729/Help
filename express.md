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

Luego vamos aconfigurar prettier para formatear nuestro codigo, creando un archivo en la raiz del proyecto con el nombre de .prettierrc y le agregamos la siguiente configuración:

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

Luego vamos a instalar las dependencias de desarrollo, estas son dependencias que solo se van a utilizar miestras estamos desarrollando nuestro proyecto, vamos a instalar las siguientes.

    npm i -D nodemon eslint eslint-config-prettier eslint-plugin-prettier prettier

Para que nuestro codigo realice el formateo automatico cada vez que se hace commit y se sube al repositorio vamos a instalar un hook:

    npx mrm lint-staged

Ya tenemos todo configurado, ahora vamos a iniciar con nuestro proyecto.

Vamos a crear un archivo de configuración, en un directorio llamado config vamos a crear un archivo con el nombre de index.js y vamos agregar lo siguiente, esto para cargar variables de entorno.

```javascript
require("dotenv").config();

const config = {
  dev: process.env.NODE_ENV !== "production",
  port: process.env.PORT || 3000,
};

module.exports = { config };
```

Ahora vamos a crear un servidor con express, ejemplo de hola mundo.

```javascript
const express = require("express");
const app = express();

const { config } = require("./config");

app.get("/", function(req, res) {
  res.json({ saludo: "Hola Mundo" });
});

app.listen(config.port, function() {
  console.log(`Listening http://localhost:${config.port}`);
});
```

# Como crear una API con Restful

## Anatomía de una API Restful

REST (Representational State Transfer) es un estilo de arquitectura para construir web services, no es un estándar pero si una especificación muy usada.

Las peticiones HTTP van acompañadas de un “verbo” que define el tipo de petición:

- GET. Lectura de datos.
- PUT. Reemplazar datos.
- PATCH. Actualizar datos en un recurso específico.
- POST. Creación de datos.
- DELETE. Eliminación de datos.

No es recomendable habilitar un endpoint de tipo PUT y DELETE para toda nuestra colección de datos, sólo hacerlos para recursos específicos, ya que no queremos que por error se puedan borrar todos nuestros datos.

Es una buena practica crear un directorio de routes y dentro de este directorio vamos a crear un archivo llamado movies.js, puedes ver un ejemplo de como crear un CRUD, moviesMocks es solo un archivo que continene la información falsa de peliculas en formato JSON.

```javascript
const express = require("express");
const moviesMocks = require("../utils/mocks/movies");

function moviesApi(app) {
  const router = express.Router(app);
  app.use("/api/movies", router);

  /**
   * Endpoint para listar todas las peliculas
   */
  router.get("/", async function(req, res, next) {
    try {
      const movies = await Promise.resolve(moviesMocks);

      res.status(200).json({
        data: movies,
        message: "Peliculas encontradas exitosamente",
      });
    } catch (error) {
      next(error);
    }
  });

  /**
   * Endpoint para listar una pelicula por id
   */
  router.get("/movieId", async function(req, res, next) {
    try {
      const movie = await Promise.resolve(moviesMocks[1]);

      res.status(200).json({
        data: movie,
        message: "Pelicula encontrada exitosamente",
      });
    } catch (error) {
      next(error);
    }
  });

  /**
   * Endpoint para crear una nueva pelicula
   */
  router.post("/", async function(req, res, next) {
    try {
      const createMovieId = await Promise.resolve(moviesMocks[0].id);

      res.status(201).json({
        data: createMovieId,
        message: "Pelicula creada exitosamente",
      });
    } catch (error) {
      next(error);
    }
  });

  /**
   * Endpoint para actualizar los datos de una pelicula
   */
  router.put("/:movieId", async function(req, res, next) {
    try {
      const updateMovieId = await Promise.resolve(moviesMocks[0].id);

      res.status(200).json({
        data: updateMovieId,
        message: "Pelicula actualizada exitosamente",
      });
    } catch (error) {
      next(error);
    }
  });

  /**
   * Endpoint para eliminar una pelicula
   */
  router.delete("/:movieId", async function(req, res, next) {
    try {
      const deleteMovieId = await Promise.resolve(moviesMocks[0].id);

      res.status(200).json({
        data: deleteMovieId,
        message: "Pelicula eliminada exitosamente",
      });
    } catch (error) {
      next(error);
    }
  });
}

module.exports = moviesApi;
```
