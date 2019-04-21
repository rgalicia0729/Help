# Testing En Java

* ¿Qué es un test?
* ¿Para qué sirve?
* Tipos de test
* Partes de un test
* TDD

## Beneficios de los tests y tipos

Beneficios

    Comprobar los requerimientos de nuestra aplicación.
    Documentación y ejemplos de nuestras clases.
    Mediante Test Driven Development (TDD) nos puede ayudar en el diseño de clases.
    Confianza al desarrollar.
    Confianza para refactorizar nuestro código.
    Es una habilidad que se solicita cada vez más en el mercado.

Existen test automáticos y manuales, los automáticos van a requerir tiempo de desarrollo y algunas veces no serán tan viables, pero de ser posible siempre trata de hacer test automáticos ya que:

    Son más rápidos.
    Son más fiables.
    Son incrementales.

Tipos de test

    Unitario: realizan pruebas a una función o clase muy concreta de nuestro proyecto.
    Integración: prueban cómo se conectan diferentes componentes de nuestro proyecto.
    Funcionales: prueban una funcionalidad de nuestro proyecto, pueden involucrarse varias clases.
    Inicio a fin: prueba todo un proceso del proyecto.
    Estrés: útil para probar si nuestra aplicación puede soportar grandes cantidades de procesos y peticiones a la vez.
    
## Test Unitiario

Para este tipo de Test se puede utilizar la libreria de junit, la mas estable por el momento es la version 4. Encontraras como utilizarla en el siguiente link. https://junit.org/junit4/

Si estas utilizando MAVEN puedes agregar la libreria con la siguiente dependencia.

    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>

Para realizar un Test de un metodo, primero se debe crear una clase en la sección de Test del proyecto. Luego agrupar cada Test en metodos como se muestra a continuacion.

    @Test
    public void repeat_string_one() {
        Assert.assertEquals(espera, recibe);
    }
    
Si el metodo lanza una exception, se puede capturar de la siguiente manera, agregando un parametro en la anotacion.
    
    @Test(expected = IlegalArgumentException.class)

## Test con Mockito

Mockito nos va a servir para simular clases mientras probamos, para añadirlo a nuestro proyecto debemos copiar las siguientes líneas de código:

    <dependency>
        <groupId>org.mockitogroupId>
        <artifactId>mockito-coreartifactId>
        <version>2.23.4version>
        <scope>testscope>
    <dependency>
 
Para instanciar un mock debemos utilizar la función Mockito.mock() e indicarle como parámetro la clase que va a simular.
Las funciones assertFalse y assertTrue tal como su nombre lo indican, sirven para comprobar si un valor es igual a false o true respectivamente.

Ejemplo
    
    Dado dado = Mockito.mock(Dado.class);
    Mockito.when(dado.method()).thenReturn(valor_que_se_desea_esperar);
 
 


