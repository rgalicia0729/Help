# Profecional de VueJS

## Acerca de VueJS:

1. Tiene complejidad inherente y complejidad instrumental.
2. La complejidad inherente es la que se hereda del proyecto y no se puede modificar.
3. La complejidad instrumental es la que nosotros podemos controlar. Es el precio que pagamos para resolver la complejidad inherente (herramientas).
-** VueJS** puede ser definido como el Framework Web Progresivo porque nos permite progresivamente ir escalando nuestra aplicación a medida que lo vamos necesitando.

## Características del Framework:

1. Está orientado a la vista.
2. Es reactivo. Se puede enlazar el código con la vista. Se puede actualizar desde cualquiera de los dos y se sincroniza todo en un círculo virtuoso.
3. Está basado en Core, es una librería pequeña, resuelve algo específico y concreto. Sin embargo es escalable y extendible.

## Instalar Node.js

Elegir la version segun el sistema operativo

https://nodejs.org/es/

## Instalar Vue devtools

Es una instalacion de chrome

https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd/related?hl=es

## Instalar el CLI de Vue.js

Utilizando npm se instalara el CLI para el manejo de las interfaces de vue

sudo npm install -g vue-cli

## Iniciando el proyecto del curso

Utilizando el CLI y el template de webpack-simple

1. vue init webpack-simple 'nombre del proyecto'
2. cd my-project
3. npm install
4. npm run dev

Referencia:
https://github.com/vuejs-templates/webpack-simple

## Webpack

Tiene el propósito de trabajar con diferentes archivos en nuestro desarrollo local, pero generando un único archivo, 
aunque podemos configurarlo para que sea uno, dos o tres archivos, eso depende de cómo lo necesitemos.

también nos permite agregar archivos de CSS, archivos .svg, imágenes, urls y contenidos. 
Esto quiere decir que se puede compilar archivos de JavaScript y archivos estáticos.

## Babel

Babel es un transpilador de código. Una herramienta que transforma y compila nuestro código. Esto quiere decir que nos permite escribir en un código compatible con cualquier navegador.

## Instalar Eslint

Para garantizar que todos los desarrolladores cumplan con las reglas de escritura de codigo

npm i -D eslint

npm install --save-dev eslint-config-standard eslint-plugin-standard eslint-plugin-promise eslint-plugin-import eslint-plugin-node

https://github.com/standard/eslint-config-standard

## Configurar Eslint en webpack

npm i -D eslint-loader

Agregar al archivo webpack.config.js dentro del atributo rules el siguiente codigo

  {
    test: /\.(js|vue)$/,
    loader: 'eslint-loader',
    enforce: 'pre',
    include: [path.resolve(__dirname, './src')]
  }

Agregar el plugin para html de Eslint

npm i -D eslint-plugin-html

Agregar en el archivo .eslintrc el siguiente codigo

"plugins": ["html"]

## Como configurar SASS Y BULMA

npm i -S bulma

## Instalar PUG

Una manera para agilizar el desarrollo, es un procesador de HTML

npm i -D pug pug-loader

## Expresiones

Las expresiones son esos parámetros que ponemos entre llaves dentro de nuestro HTML y nos permiten representar en pantalla valores de nuestro Vue Model.

## Directivas

Las Directivas son pequeños marcadores o atributos que podemos agregar a nuestros elementos HTML que nos sirven para aplicar transformaciones en esos mismos elementos.

## Computed properties

Computed Properties son son propiedades que se calculan a partir de los valores de otras propiedades, esto quiere decir que podemos crear propiedades dinámicas que van a ser regeneradas cada vez que otras propiedades cambien su valor.

## Eventos

Los Eventos tanto como los inputs son la manera que el usuario tiene para interactuar con nuestra aplicación.

## Servicios

Para consumir servicios Rest utilizando axios

npm i -S axios

## vue-router

Referencia:
https://github.com/vuejs/vue-router

npm i -S vue-router

## Vuex

npm i -S vuex

1. Crear un archivo llamado store.js
- [x] import Vue from 'vue'
- [x] import Vuex from 'vuex'

- [x] Vue.use(Vuex)

## Instalar Serve en la app

npm i -S serve
