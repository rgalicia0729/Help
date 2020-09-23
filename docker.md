# Docker de cero a experto

## Problemáticas del desarrollo de software profesional

A la hora de hacer aplicaciones y proyectos de software nos podemos encontrar con varios problemas, estos problemas los podemos agrupar en tres categorías:

- Construir
- Distribuir
- Ejecutar.

Docker promete ser la solución a todo nuestros problemas de una manera simple y sencilla.

## Instalación de Docker

Vamos a ver cómo podemos instalar Docker en diferentes sistemas operativos, tendrás el enlace en los archivos de esta clase.

    Para usuarios Mac o Windows pueden utilizar este enlace:
    https://www.docker.com/

    Puedes comprobar que todo está funcionando, ingresa el comando ““docker”” en la terminal.

    Para usuarios Linux, este es el enlace:
    https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce

    Comando para que el usuario de ubuntu pueda usar docker.

    $ sudo usermod -aG docker nombre_usuario

## Contenedores

Los contenedores son el concepto fundamentalal hablar de docker. Un contenedor es una entidad lógica, una agrupación de procesos que se ejecutan de forma nativa como cualquier otra aplicación en la máquina host.

Un contenedor ejecuta sus procesos de forma nativa

## Crear imagenes propias

### Dockerfile

Para crear imagenes de docker las instrucciones se escriben en un archivo que por lo general lleva como nombre dockerfile. A continuación un ejemplo de las instrucciones basicas que contiene un archivo dockerfile para crear una imagen personalizada.

```
FROM centos

RUN yum install httpd -y

CMD apachectl -DFOREGROUND

```

- FROM -> Es el sistema operativo que va a ejecutar el contenedor

- RUN -> Instrucción para instalar el software al sistema operativo

- CMD -> Instrucción para ejecutar el software en primer plano

Luego de crear el archivo dockerfile con las instrucciones necesarias para crear una imagen personalizada, ejecutamos el siguiente comando para construir la imagen.

    $ docker build --tag 'nombre-imagen' .

    $ docker build -t 'nombre-imagen':'version' .

Podemos ver el historial de la imagen como fue creada con el siguiente comando.

    $ docker history -H 'nombre-imagen'




