## Explorar el estado de docker

Vamos a conocer algunos trucos de nuestra consola para explorar el estado del docker
Para listar todos los contenedores de Docker, utilizamos el comando:

* docker ps -a
  
Podemos inspeccionar un contenedor en específico utilizando:

* docker inspect nombreDelContenedor
  
## Exponiendo contenedores al mundo exterior

Los contenedores están aislados del sistema y a nivel de red, cada contenedor tiene su propia stack de net y sus propios puertos.

Debemos redirigir los puertos del contenedor a los de la computadora y lo podemos hacer al utilizar este comando:

* docker run -d --name server -p 8080:00  nombreDelContenedor
  

# Comandos Basicos de Docker
Este documento muestra un listado de los comandos básicos para la administracion de Docker

# Aprendiendo a utilizar los contenedores

## Iniciar un nuevo contenedor
docker run "nombre_imagen" 

## Verificar el estado de los contenedores
docker ps

## Verificar el estado de todos los contenedores
docker ps -a

## Inspeccionar un contenedor de docker, muestra toda la metadata del mismo
docker inspect "id del contenedor | nombre del contenedor"

## Inspeccionar un docker solicitando un elemento en particular de la metadata con un filtro
docker inspect -f '{{ json.config.env }}' "Nombre del contenedor"

## Para renombrar un contenedor
docker rename "nombre actual" "nombre nuevo"

## Iniciar un contenedor con nombre personalizado
docker run --name "nombre del contenedor" "nombre de la imagen"

## Mostrar el output del contenedor
docker logs "nombre del contenedor | id del contenedor"

## Eliminar un contenedor
docker rm "nombre del contenedor | id del contenedor"

## Listar el id de todos los contenedores
docker ps -aq

## Eliminar varios contenedores
docker rm $(docker ps -aq)

## Instalar un ubuntu linux en docker
docker run ubuntu

## Ejecutar el servicio de ubuntu linux
docker run -it ubuntu

## Ejecutar un contenedor existente
docker exec -it "nombre del contenedor" bash

## Starting a MySQL Server Instance
docker run --name=mysql1 -d mysql/mysql-server
- [x] Referencia:
1. https://dev.mysql.com/doc/mysql-installation-excerpt/5.5/en/docker-mysql-getting-started.html
2. https://docs.bluehosting.cl/tutoriales/servidores/como-crear-un-nuevo-usuario-y-otorgar-permisos-en-mysql.html

## Exponer un contenedor al exterior
docker run -d --name "nombre del contenedor" -p "puerto del sistema operativo":"puerto del contenedor" "nombre de la imagen"

## Starting mongodb
docker run -d -p 27017:27017 --name mongodb mongo

## Ejecutar bash para conectarse al cliente de mongo
docker exec -it mongodb bash

## configurar un directorio externo al contenedor para almacenar los datos de mongo
docker run -b -p 27017:27017 --name mongodb -v "path":/data/db mongo

## Para correr la imagen generada en el curso de Java Spring
docker run -d --name "Nombre del contenedor" --add-host=mysql_server:"ip del servidor de base de datos" -p 8080:8080 "Nombre de la Imagen":latest

## Verificar el log de la ejecucion del programa
docker logs -f "Nombre de la Imagen"

## Ver los Volumenes creados por los contenedores que se han corrido
docker volume ls

## Eliminar los volumenes que no se estan utilizando
docker volume prune

## Crear un volumen
docker volume create "nombre del volumen"

## Ejecuta un contenedor de mongo y almacena el contenido en el volumen creado
docker run -d -p 27017:27017 --name mongodb --mount src="nombre del volumen creado",dst=/data/db mongo
