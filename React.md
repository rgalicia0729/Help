# Guia de React.js

## Requisitos para trabajar con React.js

* Tener un navegador instalado, especialmente Chrome
* Instalar la herramienta de React Developer Tools
* Un editor de texto, recomendado Visual Studio Code (Agregar plugin de prettier)

## Create-react-app

Create-react-app es una aplicación moderna que se usa desde una línea de comando. Antes de ella se configuraba todo el entorno manualmente lo cual tomaba mucho tiempo.

Pasos para obtenerlo:
Se debe instalar desde la línea de comando usando
* npm install -g create-react-app

Una vez instalado se crea la carpeta del proyecto con
* create-react-app -nombre del proyecto-

En este punto se estará instalando React y otras herramientas, también se configurará el entorno usando Webpack.

Una vez se instala todo entra a la carpeta src donde estará todo el código fuente de la aplicación, siendo el más importante index.js que es el punto de entrada a la aplicación.

Finalmente para correr la aplicación se usa el comando
* npm run start

## ReactDOM.render

    React y ReactDOM trabajarán en conjunto.
        React como análogo a createElement
        ReactDOM a appendChild

    ReactDOM.render() toma dos argumentos: Qué queremos renderizar y dónde lo queremos renderizar.

    Siempre que escribas JSX es requisito importar React.

## JSX

JSX es una extensión de JavaScript creada por Facebook para el uso con la biblioteca React. Sirve de preprocesador (como Sass o Stylus a CSS) y transforma el código generado con React a JavaScript.

JSX tiene su alternativa que es React.createElement pero es preferible JSX porque es mucho más legible y expresivo. Ambos tienen el mismo poder y la misma capacidad.

React.createElement recibe 3 argumentos:

    1. El tipo de elemento que estamos creando
    2. sus atributos o props
    3. y el children que es el contenido.

Ejemplo:
React.createElement(‘a’, { href: ‘https://platzi.com’ }, ‘Ir a Platzi’);

En JSX se utilizan las llaves para introducir variables o expresiones de Javascript. Lo que sea que esté adentro se va a evaluar y su resultado se mostrará en pantalla.

Las expresiones pueden ser llamadas a otras funciones, cálculos matemáticos, etc. Si las expresiones son false, 0, null, undefined, entre otros, no se verán.

## ¿Qué es un componente?

Los componentes en React son bloques de construcción.
Las aplicaciones hechas con React son como figuras de Lego. Junta varias piezas (componentes) y puedes construir un website tan pequeño o tan grande como quieras.
Los componentes serán barras de búsquedas, enlaces, encabezados, el header, etc.

”Componente” vs “elemento
Un elemento es a un objeto como un componente es a una clase. Si el elemento fuera una casa, el componente serían los planos para hacer esa casa.

Identificación de componentes
Para identificarlos debes hacerte las siguientes preguntas:

* ¿Qué elementos se repiten? Estos son los elementos en una lista o los que comparten aspecto visual y su funcionalidad
* ¿Qué elementos cumplen una función muy específica? Estos sirven para encapsular la lógica y permiten juntar muchos comportamientos y aspectos visuales en un solo lugar.

Identificar componentes es una habilidad esencial para poder desarrollar aplicaciones de React.

* Es una buena práctica que los componentes vivan en su propio archivo y para ello se les crea una carpeta.
* Todos los componentes requieren por lo menos el método render que define cuál será el resultado que aparecerá en pantalla.
* El source de las imágenes en React puede contener direcciones en la web o se le puede hacer una referencia directa importándola. Si se importa deben usarse llaves para que sea evaluado.

## Cómo aplicar estilos

* Para los estilos crearemos una carpeta llamada Styles y allí vivirán todos los archivos de estilos que tienen que ver con los componentes.
* Para usar los estilos es necesario importarlos con import
* React funciona ligeramente diferente y para los atributos de clases no se utiliza class sino className
* Es posible utilizar Bootstrap con React, sólo debe ser instalado con npm install bootstrap y debe ser importado en el index.js
* Existen estilos que son usados de manera global o en varios componentes, así que deben ser importados en el index.js

## Props

Los props que es la forma corta de properties son argumentos de una función y en este caso serán los atributos de nuestro componente como class, src, etc.

Estos props salen de una variable de la clase que se llama this.props y los valores son asignados directamente en el ReactDOM.render().

Las páginas en React son componentes conseguir distinguirlas nos servirá para saber que es un componente que adentro lleva otros componentes.

Al escribir los props no importa el orden en el que lo hagas, únicamente importa el nombre.

## Eventos

React dispone de eventos. Cada vez que se recibe información en un input se obtiene un evento onChange y se maneja con un método de la clase this.handleChange

Los elementos button también tienen un evento que es onClick.

Cuando hay un botón dentro de un formulario, este automáticamente será de tipo submit. Si no queremos que pase así hay dos maneras de evitarlo: especificando que su valor es de tipo button o manejándolo desde el formulario cuando ocurre el evento onSubmit.

## Manejo De Estado

Hasta esta clase todos los componentes han obtenido su información a través de props que vienen desde afuera (otros componentes) pero hay otra manera en la que los componentes pueden producir su propia información y guardarla para ser consumida o pasada a otros componentes a través de sus props. La clave está en que la información del state a otros componentes pasará en una sola dirección y podrá ser consumida pero no modificada.

Para guardar la información en el estado se usa una función de la clase component llamada setState a la cual se le debe pasar un objeto con la información que se quiere guardar.

Aunque no se ve, la información está siendo guardada en dos sitios. Cada input guarda su propio valor y al tiempo la está guardando en setState, lo cual no es ideal. Para solucionarlo hay que modificar los inputs de un estado de no controlados a controlados.

## Manejo de estado

Hasta esta clase todos los componentes han obtenido su información a través de props que vienen desde afuera (otros componentes) pero hay otra manera en la que los componentes pueden producir su propia información y guardarla para ser consumida o pasada a otros componentes a través de sus props. La clave está en que la información del state a otros componentes pasará en una sola dirección y podrá ser consumida pero no modificada.

Para guardar la información en el estado se usa una función de la clase component llamada setState a la cual se le debe pasar un objeto con la información que se quiere guardar.

Aunque no se ve, la información está siendo guardada en dos sitios. Cada input guarda su propio valor y al tiempo la está guardando en setState, lo cual no es ideal. Para solucionarlo hay que modificar los inputs de un estado de no controlados a controlados.

Levantar el estado es una técnica de React que pone el estado en una localización donde se le pueda pasar como props a los componentes. Lo ideal es poner el estado en el lugar más cercano a todos los componentes que quieren compartir esa información.

Algo interesante que le da el nombre a React es su parte de “reactivo” ya que cada vez que hay un cambio en el estado o en los props que recibe un componente se vuelve a renderizar todo el componente y todos sus descendientes.

## Introducción React Router

Las aplicaciones que se trabajan en React son llamadas single page apps. Esto es posible gracias a React Router que es una librería Open Source****.

Multi Page Apps: Cada página implica una petición al servidor. La respuesta usualmente tiene todo el contenido de la página.

Single Page Apps (SPA): Aplicaciones que cargan una sola página de HTML y cualquier actualización la hacen re-escribiendo el HTML que ya tenían.

React Router (v4): Nos da las herramientas para poder hacer SPA fácilmente. Usaremos 4 componentes:

    * BrowserRouter: es un componente que debe estar siempre lo más arriba de la aplicación. Todo lo que esté adentro funcionará como una SPA.
    * Route: Cuando hay un match con el +path+, se hace render del +component+. El component va a recibir tres props: match, history, location.
    * Switch: Dentro de Switch solamente van elementos de Route. Switch se asegura que solamente un Route se renderize.
    * Link: Toma el lugar del elemento <a>, evita que se recargue la página completamente y actualiza la URL.
    
 ## División de la aplicación en rutas
 
Para instalar React Router lo hacemos desde la terminal con npm install react-router-dom. Como es importante usar exactamente la misma versión, del package.json en “dependencies” se quita lo que está delante del 4.

* Link internamente tiene un elemento pero va a interceptar el clic para navegar de manera interna sin refrescar toda la página.

## Mejorando la User Interface con un Layout

* React.Fragment es la herramienta que te ayudará a renderizar varios componentes y/o elementos sin necesidad de colocar un div o cualquier otro elemento de HTML para renderizar sus hijos. Al usar esta característica de React podremos renderizar un código más limpio y legible, ya que ``React.Fragment` no se renderiza en el navegador.

* El 404 es la ruta que se renderizará cuando ninguna otra coincida con la dirección ingresada.

Otra forma de hacer que todas tus URL’s que no existan sean redirigidas a tu componente de 404 sería de la siguiente forma:

    import { Redirect, Route } from "react-router-dom";

Como podemos observar llamamos a nuestro componente 404 y luego utilizamos Redirect, el cual es un componente de React Router para hacer redirecciones; en este caso hacemos que todas las URL’s que no correspondan a alguna que hayamos declarado, sean redirigidas a MiComponente404.

## Introducción del ciclo de vida de un componente

Cuando React renderiza los componentes decimos que entran en escena, cuando su estado cambia o recibe unos props diferentes se actualizan y cuando cambiamos de página se dice que se desmontan.

### Montaje:

* Representa el momento donde se inserta el código del componente en el DOM.
* Se llaman tres métodos: constructor, render, componentDidMount.

### Actualización:

* Ocurre cuando los props o el estado del componente cambian.
* Se llaman dos métodos: render, componentDidUpdate.

### Desmontaje:

* Nos da la oportunidad de hacer limpieza de nuestro componente.
* Se llama un método: componentWillUnmount.

### Metodos del ciclo de vida

    constructor (props) { super(props) }
    render () {}
    componentDidMount () {}

## Introducción llamadas a un API

Las llamadas a una API siguen un patrón similar siempre que las hacemos, cada llamada consta de tres estados:
* Loading: cuando la petición se envía y estamos esperando.
* Error: se debe dejar un mensaje para el usuario para arreglar el error o volver a intentarlo.
* Data: los datos nos pueden llegar de dos formas, o en error o con los datos requeridos.

## React.js: Cómo traer datos de un API en React

Una llamada a una API es un proceso asíncrono, es decir que lo comenzamos pero no sabemos cuándo acabará. Por lo mismo la función a escribir debe ser asíncrona.
La llamada se hará usando fetch que es una función de React que al pasarle una dirección de internet, hará una petición GET y lo que sea que exista ahí será devuelto.






