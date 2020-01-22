# Webpack 4

¡Te damos la bienvenida al Curso de Webpack 4!

Leonidas Esteban es Frontend Chapter Lead en @GrowMobility además de Google Developer Expert y Best Platzi Teacher. Él es tu profesor en este curso donde aprenderás cómo usar Webpack para empaquetar tus dependencias tanto en ambientes de producción como desarrollo.

No es requisito para tomar el curso pero te recomendamos revisar la Carrera de Arquitectura Frontend y tomar cursos como los de Angular, React y Vue.

Recuerda que cualquier duda puedes usar nuestro sistema de discusiones. ¡Nunca pares de aprender!

## Introducción a Webpack

Webpack es un empaquetador para Javascript y sus amigos. Convierte módulos con dependencias en archivos estáticos que los navegadores entienden.

Nos permite empaquetar, optimizar los diferentes módulos Javascript y sus dependencia en nuestro proyecto. Es usado en proyectos basados en Javascript como: React, Vue, Angular entre otros.

User Experience

Se logra con una aplicación que:

    Funcione
    Sea rápida
    Cumpla sus necesidades
    Se actualice
    Responda a sus interacciones
    Producto de calidad

Developer Experience

    Escribir aplicaciones de manera eficiente.
    Tener un código limpio.
    Aplicar tecnología para resolver sus problemas.
    Tener un conjunto de reglas y convenciones.
    Entorno de desarrollo optimizado en productividad.

## Configurando un nuevo proyecto de Javascript

Aprende más en el Curso de Webpack en Platzi disponible con tu suscripción en: https://platzi.com/clases/webpack/
Adquiere hoy la suscripción de Platzi en: http://platzi.com/precios

En esta clase el profesor Leonidas Esteban nos guía paso a paso para crear nuestro primer proyecto usando Webpack.

En nuestro proyecto existen dependencias del tipo desarrollo y del tipo core con sus respectivas versiones, por eso usaremos NPM para administrarlas e instalar Webpack que viene a ser una dependencia (de desarrollo) más en nuestro proyecto de Javascript.

## Creando nuestro primer bundle con Webpack

Vamos a instalar otra dependencia llamada webpack-cli, la API que expone webpack en forma de CLI (Command Line Interface) que nos va a permitir interactuar y configurar Webpack desde la terminal.

El comando webpack tiene una bandera llamada --mode que nos permite cambiar entre los modos producción y desarrollo. Recuerda que por defecto nos pone en modo producción si no la especificamos.

## Ejemplo de Webpack

Creamos un proyecto de JavaScript.

$ npm init -y

Ahora instalamos webpack

$ npm install webpack --save-dev

Instalamos el CLI de webpack

$ npm install webpack-cli --save-dev

Para poder saber la versión de webpack utilizamos el siguiente comando

$ npx webpack -v

Para combilar el index.js con webpack podemos utilizar el siguiente comando, esto
solo como base de prueba

$ npx webpack --entry ./index.js --output ./bundle.js --mode development

## Iniciando un webpack.config

Al ir creciendo nuestra configuración de Webpack iremos agregando cada vez más banderas a nuestros comandos y terminará como una línea gigante en la terminal. ¿Cómo hacemos que esa línea sea muy pequeñita, personalizable y escalable? Por medio de un archivo llamado por defecto webpack.config.js.

Este archivo permite importar módulos usando el formato commonJS y recibe por lo menos dos configuraciones básicas, un entry y un output.


- Entry Point: Es la ruta del archivo principal de nuestra aplicación JS a ser procesado por Webpack. Se pueden tener varios Entry Points.
- Output: Es la ruta de salida donde va a generar nuestro bundle con todos nuestros archivos especificados como Entry Points empaquetados en uno sólo.

En el archivo webpack.config.js agregamos la configuración de Webpack para nuestro proyecto, lo que hicimos utilizando la linea de comandos lo vamos hacer configurando el webpack.config.js, esto queda de la siguiente manera:

```javascript 
const path = require('path');

module.exports = {
  entry: path.resolve(__dirname, 'index.js'),
  mode: 'development',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js'
  }
}
```

Para ejecutar webpack con esta configuración lo hacemos simplemente ejecutando el siguiente comando.

$ npx webpack

Podemos agregar nuestro comando de ejecucción de webpack en el package.json asi:

```json

"scripts": {
  "build": "webpack"
},

```

## Cargando configuraciones por defecto y personalizadas

Por medio del uso de la bandera --config podemos especificar un archivo de configuración externo con el nombre que queramos en lugar del nombre por defecto webpack.config.js.

```json

"scripts": {
  "build": "webpack --config ./ubicacion/archivo-config.js"
},

```

## Múltiples puntos de entrada

Al tener multiples puntos de entrada tambien tenemos multiples puntos de salida, la configuracion seria de la siguiente manera.

```javascript
const path = require('path');

module.exports = {
  entry: {
    home: path.resolve(__dirname, 'index.js'),
    menu: path.resolve(__dirname, 'menu.js'),
  },
  mode: 'development',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name].js'
  }
}
```

## Manejo de assets con Loaders

Los Loaders son la funcionalidad que nos da Webpack para interpretar tipos de archivos no soportados de forma nativa por Javascript.

style-loader sirve para inyectar un tag style (el CSS) al DOM de nuestro HTML, mientras que css-loader sólo sirve para interpretar archivos CSS.

Se necesita instalar css-loader y style-loader

    $ npm install --save-dev css-loader

    $ npm install --save-dev style-loader

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          'style-loader',
          'css-loader'
        ]
      }
    ]
  }
}
```

## Introducción al uso de plugins

Los Plugins sirven para extender las capacidades de webpack y dar más poder a los loaders. Vamos a instalar el plugin de mini-css-extract-plugin y html-webpack-plugin, para ello vamos a utilizar el siguiente comando.

$ npm install mini-css-extract-plugin html-webpack-plugin --save-dev

Para instalarlo vamos a utilizar la siguiente configuracion.

```javascript
const path = require('path');
const MiniCSSExtractPlugin = require('mini-css-extract-plugin');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: {
    bundle: path.resolve(__dirname, 'index.js'),
  },
  mode: 'development',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name].js'
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          {
            loader: MiniCSSExtractPlugin.loader
          },
          'css-loader'
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin(),
    new MiniCSSExtractPlugin({
      filename: 'css/[name].css'
    })
  ]
}
```

## Servidor de desarrollo

El servidor de desarrollo nos ayuda a mejorar nuestra experiencia de desarrollo, ya no tenemos que estar recargando la pagina cuando realizamos algun cambio y para ello vamos a instalar el servidor de desarrollo de webpack con el siguiente comando:

$ npm install webpack-dev-server --save-dev

Cambiamos el script del package.json

```json
"scripts": {
  "dev": "webpack-dev-server",
  "build": "webpack"
},
```

## Hot Module Replacement

