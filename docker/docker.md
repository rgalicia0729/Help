# Docker de cero a experto

## Problemáticas del desarrollo de software profesional

A la hora de hacer aplicaciones y proyectos de software nos podemos encontrar con varios problemas, estos problemas los podemos agrupar en tres categorías:

- Construir
- Distribuir
- Ejecutar.

Docker promete ser la solución a todo nuestros problemas de una manera simple y sencilla.

Docker nos permite construir, distribuir y ejecutar cualquier aplicación en cualquier lado.

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

## Comandos de docker

    Ver la versión de docker
    $ docker --version

    Ver la información de configuración de docker
    $ docker info

    Ver los contenedores que estan corriendo
    $ docker ps

    Ver todos los contenedores
    $ docker ps -a

    Ver la información de un contenedor
    $ docker inspect <CONTAINER ID || NAME>

    Renombrar un contenedor
    $ docker rename <NOMBRE_ACTUAL> <NUEVO_NOMBRE>

    Eliminar un contenedor
    $ docker rm <CONTAINER ID || NAME>

    Eliminar un contenedor que este corriendo
    $ docker rm -f <CONTAINER ID || NAME>

    Eliminar todos los contenedores que estan parados
    $ docker container prune

    Ejecutar un contenedor
    $ docker run <IMAGE NAME>
        --name <nombre de la imagen>
        -p <puerto de la maquina>:<puerto del contenedor>
        -it 'Ejecutar un contenedor en modo interactivo'
        --detach || -d ejecuta el contenedor en background
        -v bind mounts <directorio de la maquina>:<directorio del contenedor>
        --mount src=<Nombre del volumen>,dst=<directorio del contenedor>
        --env <ENVIRONMENT VARIABLE> = <VALUE>

    Ejecutar el bash de un contenedor que este corriendo con linux 
    $ docker exec -it <NAME> bash

    Obtener el process id del main process que se ejecuta en un contenedor
    $ docker inspect --format '{{.State.Pid}}' <NAME>

    Si se ejecuta docker en un sistema operativo linux se puede matar el proceso 
    $ kill -9 <PROCESS ID>

    Detener un contenedor
    $ docker stop <CONTAINER ID || NAME>

    Ver los logs de un contenedor
    $ docker logs <CONTAINER ID || NAME>

    Ver los logs a medida que se esten generando
    $ docker logs -f <CONTAINER ID || NAME>

    Ver las ultimas N lineas de logs
    $ docker logs --tail N -f <CONTAINER ID || NAME>

    Listar volumenes
    $ docker volume ls

    Crear un nuevo volumen
    $ docker volume create <Nombre del volumen>

    Eliminar un volumen
    $ docker volume rm <NAME>

    Eliminar todos los volumenes que ya no se estan utilizando
    $ docker volume prune

    Copiar un archivo dentro de un contenedor
    $ docker cp <Fichero a copiar> <Nombre del contenedor>:<Directorio del contenedor>

    Extraer un archivo que está dentro del contenedor, al sistema operativo de la maquina.
    $ docker cp <Nombre del contenedor>:<Nombre del archivo a extraer> <ruta de la maquina>

    Listar las imagenes
    $ docker image ls || docker images

    Descargar una imagen de un servidor (docker hub)
    $ docker pull <nombre de la imagen>:<version de la imagen>

    Cambiar el tag de una imagen
    $ docker tag <nombre actual> <nuevo nombre>

    Subir imagenes a docker hub
    $ docker login
    $ docker push <nombre de la imagen>

    Listar las redes de docker
    $ docker network ls

    Crear una nueva red que permita que otros contenedores se conecten a ella
    $ docker network create --attachable <Nombre de la red>

    Ver la configuracion de una red
    $ docker network inspect <Nombre de la red>

    Conectar un contenedor a una red
    $ docker network connect <nombre de la red> <nombre del contenedor>

## Comandos de docker compose

    Ejecutar docker compose
    $ docker-compose up || docker-compose up -d

    Ver los contenedores que se estan ejecutando con docker compose
    $ docker-compose ps

    Ver los logs de los servicios de docker compose
    $ docker-compose logs

    Ver los logs de un servicio de docker compose
    $ docker-compose logs <Nombre del servicio>

    Ver los logs de dos o mas servicios de docker compose
    $ docker-compose logs <Nombre del servicio 1> <Nombre del servicio 2>

    Ver las ultimas lineas de logs de los servicios docker compose
    $ docker-compose logs -f <Nombre del servicio>

    Correr un comando en un contenedor de docker compose
    $ docker-compose exec <Nombre del servicio>

    Destruir todo el ambiente de docker compose
    $ docker-compose down

    Build de los servicios de docker compose
    $ docker-compose build

    Hacer build de un servicio de docker compose
    $ docker-compose build <Nombre del servicio>

## Crear imagenes propias

### Dockerfile

Para crear imagenes de docker las instrucciones se escriben en un archivo que por lo general lleva como nombre Dockerfile. A continuación un ejemplo del uso de las intrucciones del archivo Dockerfile.

```
FROM 'sistema operativo | imagen base'

LABEL 'agregar etiquetas a la imagen, metadata de la imagen'

RUN 'instrucciones de linea de comandos que se desean ejecutar al momento de crear'

ENV 'clave' 'valor'

WORKDIR 'path base del contenedor'

COPY 'archivos de nuestro ordenador' 'ruta del contenedor'

ADD 'dirección del archivo' 'ruta del contenedor'

EXPOSE 'puerto que se desea exponer'

USER 'el usuario que ejecute la tarea'

CMD 'ejecuta un proceso en primer plano | puede ser un script'
```

Luego de crear el archivo Dockerfile con las instrucciones necesarias para crear una imagen personalizada, ejecutamos el siguiente comando para construir la imagen.

    $ docker build --tag <nombre imagen> .

    $ docker build -t <nombre imagen>:<version> .

Podemos ver el historial de la imagen como fue creada con el siguiente comando.

    $ docker history -H 'nombre-imagen'

