# Docker

Install Docker for mac using homebrew

    brew install --cask docker

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

### Docker Deamon
- **docker version:** Ver la versión de docker
- **docker info:** Ver información sobre docker
- **docker ps:** Lista todos los contenedores que estan corriendo
- **docker ps --all:** Lista todos los contenedores
- **docker ps -a:** Lista todos los contenedores
- **docker ps -aq:** Muestra todos los ids de todos los contenedores
- **docker stats:** Muestra lo que se esta ejecutando en docker
- **docker system prune:** Limpia en la medida posible todo el ambiente de docker

### Docker Container
- **docker create \<image-name\>:** Crea un contenedor de docker pero no lo ejecuta
- **docker start \<container-id\>:** Ejecuta un contenedor de docker
- **docker stop \<container-id\>:** Detiene el main proces de un contenedor
- **docker kill \<container-id\>:** Mata el proceso principal del contenedor
- **docker run \<image-name\>:** Crea y ejecuta un contenedor
- **docker run \<image-name\> \<command\>:** Ejecuta un contenedor y anula el comando predeterminado
- **docker run --name \<docker-name\> \<image-name\>:** Agrega un nombre al contenedor
- **docker run -it \<image-name\> \<command\>:** Correr un contenedor en modo interactivo 
- **docker run -d \<image-name\>:** Ejecuta un contenedor en modo background | detach
- **docker run -p \<puerto-de-anfitrion\>:\<puerto-de-contenedor\> \<image-name\>:** Exponer un contenedor
- **docker run -v \<directorio-anfitrion\>:\<directorio-contenedor\> \<image-name\>:** Bind mounts
- **docker run --mount src=\<volume-name\>,dst=\<path-container\> \<image-name\>:** Montar un volumen a un contenedor
- **docker run --env \<ENV_NAME\>=\<env-value\>:** Agregar una variable de entorno al contenedor
- **docker run --memory 1g:** Limita al contenedor a utilizar solo un 1G de memoria
- **docker inspect \<container-id\>:** Muestra la información del contenedor
- **docker logs \<container-id\>:** Ver los logs del contenedor
- **docker logs -f \<container-id\>:** Ver los logs del contenedor en tiempo real
- **docker logs --tail 10 -f \<container-id\>:** Ver las ultimas 10 lineas del log
- **docker rename \<nombre-actual\> \<nuevo-nombre\>:** Cambiar el nombre a un contenedor
- **docker exec -it \<container-id\> \<command\>:** Ejecuta un nuevo comando en un contenedor en ejecución
- **docker rm \<container-id\>:** Eliminar un contenedor
- **docker rm -f \<container-id\>:** Elimina un contenedor auque este corriendo
- **docker container prune:** Eliminar todos los contenedores que estan apagados
- **docker rm -f $(docker ps -aq):** Elimina todos los contenedores
- **docker cp \<file-name\> \<container-name\>:\<path-file\>:** Copiar un archivo al contenedor
- **docker cp \<container-name\>:\<path-file\> \<file-name\>:** Copiar un archivo del contenedor

### Docker volumes
- **docker volume ls:** Lista todos los volumenes
- **docker volume create \<volume-id\>:** Crear un nuevo volumen
- **docker volume rm \<volume-id\>:** Eliminar un volumen

### Docker images
- **docker images:** Mostrar el listado de imagenes
- **docker tag \<current-name\>:\<image-version\> \<new-name\>:\<new-version\>:** Cambiar el tag de una imagen
- **docker pull \<image-name\>:\<image-version\>:** Descargar una imagen del repositorio
- **docker push \<image-name\>:\<image-version\>:** Subir una imagen a docker hub
- **docker build -t \<image-name\>:\<version\> \<build-context\>:** Construir una imagen
- **docker history \<image-name\>:\<version\ >** Ver el historial de capas de construcción de una imagen

### Docker network
- **docker network ls:** Muestra el listado de redes de docker
- **docker network create --attachable \<network-name\>:** Crear una nueva red en docker
- **docker network inspect \<network-name\>:** Inspeccionar los atributos de una red
- **docker network connect \<network-name\> \<container-name\>:** Conectar un contenedor a un red
- **docker network rm \<network-name\>:** Eliminar una red de docker

### Docker compose
- **docker-compose up -d:** Ejecutar un servicio compose
- **docker-compose ps:** Listar los contenedores creados con servicios compose
- **docker-compose logs:** Mostrar los logs de todos los servicio compose
- **docker-compose logs \<service-name\>:** Muestra los logs de un servicio compose
- **docker-compose logs -f \<service-name\>:** Muestra los logs de un servicio compose en tiempo real
- **docker-compose exec \<service-name\> \<comando\>:** Ejecutar un comando en un servicio compose
- **docker-compose down:** Elimina servicios compose
- **docker-compose build:** Construye una imagen de un servicios especificado como build
- **docker-compose up -d --scale \<service-name\>=\<cantidad\>:** Escalar un servicio a n cantidades

# Kubernetes

- **kubectl get pods:** Print out information about all the running pods
- **kybectl exec -it \[pod_name\]\[cmd\]:** Execute the given command in a running pod
- **kubectl logs \[pod_name\]:** Print out logs from the given pod
- **kubectl delete pod \[pod_name\]:** Deletes the given pod
- **kubectl apply -f \[config_file_name\]:** Tells cubernetes to process the config
- **kubectl describe pod \[pod_name\]:** Print out some information about the running pod
- **kubectl create secret generic jwt-secret --from-literal=JWT_KEY=\<hash_secret\>:** Generar un JWT_SECRET generico

### Deployment Commands

- **kubectl get deployments:** List all the running deployments
- **kubectl describe deployment \[deployment_name\]:** Print out details about a specific deployment
- **kubectl apply -f \[config_file_name\]:** Create a deployment out of a config file
- **kubectl delete deployment \[deployment_name\]:** Delete a deployment
- **kubectl rollout restart deployment \[deployment_name\]:** Updating the image used by a deployment
