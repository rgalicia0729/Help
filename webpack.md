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

$ npx webpack --entry ./index.js --output ./bundle.js


