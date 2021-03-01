# Docker

Problemas del desarrollo de software profesional (Los tres grandes problemas).

- Construir
- Distribuir
- Ejecutar

Containerización:

El empleo de contenedores para construir, distribuir y desplegar software.

Los contenedores son:

- Flexibles
- Livianos
- Portables
- Bajo acoplamiento
- Escalables
- Seguros

## Comandos de docker

- **docker --version:** Ver la versión de docker
- **docker info:** Ver información sobre docker
- **docker ps:** Muestra los contenedores que estan corriendo
- **docker ps -a:** Muestra todos los contenedores
- **docker ps -aq:** Muestra todos los contenedores solo sus ids
- **docker stats:** Muestra lo que se esta ejecutando en docker
- **docker inspect \<container-id\>:** Muestra la información del contenedor
- **docker logs \<container-id\>:** Ver los logs del contenedor
- **docker logs -f \<container-id\>:** Ver los logs del contenedor en tiempo real
- **docker logs --tail 10 -f \<container-id\>:** Ver las ultimas 10 lineas del log
- **docker stop \<container-id\>:** Detiene el main proces de un contenedor
- **docker kill \<container-id\>:** Mata el proceso de docker
- **docker start \<container-id\>:** Inicia el main proces de un contenedor
- **docker rename \<nombre-actual\> \<nuevo-nombre\>:** Cambiar el nombre a un contenedor
- **docker run \<image-name\>:** Crea y corre un contenedor a partir de la imagen
- **docker run --name \<container-id\>:** Corre un contenedor con un nombre especifico
- **docker run -it:** Correr un contenedor en modo interactivo 
- **docker run -d:** Ejecuta un contenedor en modo background | detach
- **docker run -p \<puerto-de-anfitrion\>:\<puerto-de-contenedor\>:** Exponer un contenedor
- **docker run -v \<directorio-anfitrion\>:\<directorio-contenedor\>:** Bind mounts
- **docker run --mount src=\<volume-name\>,dst=\<path-container\>:** Montar un volumen a un contenedor
- **docker run --env \<ENV_NAME\>=\<env-value\>:** Agregar una variable de entorno al contenedor
- **docker run --memory 1g:** Limita al contenedor a utilizar solo un 1G de memoria
- **docker volume ls:** Lista todos los volumenes
- **docker volume create \<volume-id\>:** Crear un volumen personalizado
- **docker volume rm \<volume-id\>:** Eliminar un volumen
- **docker exec:** Ejecuta un nuevo comando en un contenedor en ejecución
- **docker rm \<container-id\>:** Eliminar un contenedor
- **docker rm -f \<container-id\>:** Elimina un contenedor auque este corriendo
- **docker container prune:** Eliminar todos los contenedores que estan apagados
- **docker rm -f $(docker ps -aq):** Elimina todos los contenedores
- **docker system prune:** Limpia en la medida posible todo el ambiente de docker
- **docker cp \<file-name\> \<container-name\>:\<path-file\>:** Copiar un archivo al contenedor
- **docker cp \<container-name\>:\<path-file\> \<file-name\>:** Copiar un archivo del contenedor
- **docker images:** Mostrar el listado de imagenes
- **docker tag \<current-name\>:\<image-version\> \<new-name\>:\<new-version\>:** Cambiar el tag de una imagen
- **docker pull \<image-name\>:\<image-version\>:** Descargar una imagen del repositorio
- **docker push \<image-name\>:\<image-version\>:** Subir una imagen a docker hub
- **docker build -t \<image-name\>:\<version\> \<build-context\>:** Construir una imagen
- **docker history \<image-name\>:\<version\ >** Ver el historial de capas de construcción de una imagen
- **docker network ls:** Muestra el listado de redes de docker
- **docker network create --attachable \<network-name\>:** Crear una nueva red en docker
- **docker network inspect \<network-name\>:** Inspeccionar los atributos de una red
- **docker network connect \<network-name\> \<container-name\>:** Conectar un contenedor a un red
- **docker network rm \<network-name\>:** Eliminar una red de docker
- **docker-compose up -d:** Ejecutar un servicio compose
- **docker-compose ps:** Listar los contenedores creados con servicios compose
- **docker-compose logs:** Mostrar los logs de todos los servicio compose
- **docker-compose logs \<service-name\>:** Muestra los logs de un servicio compose
- **docker-compose logs -f \<service-name\>:** Muestra los logs de un servicio compose en tiempo real
- **docker-compose exec \<service-name\> \<comando\>:** Ejecutar un comando en un servicio compose
- **docker-compose down:** Elimina servicios compose
- **docker-compose build:** Construye una imagen de un servicios especificado como build
- **docker-compose up -d --scale \<service-name\>=\<cantidad\>:** Escalar un servicio a n cantidades

# Docker Swarm

## Preparando tus aplicaciones para Docker Swarm: los 12 factores

- **Codebase :** el código debe estar en un repositorio
- **Dependencies :** deben estar declaradas en un archivo de formato versionable, suele ser un archivo de código
- **Configuration :** debe formar parte de la aplicación cuando esté corriendo, puede ser dentro de un archivo
- **Backing services :** debe estar conectada a tu aplicación sin que esté dentro, se debe tratar como algo externo
- **Build, release, run :** deben estar separadas entre sí.
- **Processes :** todos los procesos los puede hacer como una unidad atómica
- **Port binding :** tu aplicación debe poder exponerse a sí misma sin necesidad de algo intermediario
- **Concurrency :** que pueda correr con múltiples instancias en paralelo
- **Disposabilty :** debe estar diseñada para que sea fácilmente destruible
- **Dev/Prod parity :** lograr que tu aplicación sea lo más parecido a lo que estará en producción
- **Logs :** todos los logs deben tratarse como flujos de bytes
- **Admin processes :** la aplicación tiene que poder ser ejecutable como procesos independientes de la aplicación

## Comandos de docker swarm

- **docker swarm init:** Iniciar docker en modo swarm
- **docker node ls:** Lista los nodos en docker swarm
- **docker node inspect \<node-id\>:** Muestra la información de un nodo de swarm
- **docker swarm leave:** Abandonar swarm
- **docker swarm leave -f:** Abandonar swarm desde un manager
- **docker swarm leave --force:** Abandonar swarm desde un manager
- **docker service create:** Crear un nuevo servicio
- **docker service ls:** Listar todos los servicios

