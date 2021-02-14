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
- **docker inspect \<container-id\>:** Muestra la información del contenedor
- **docker run \<image-name\>:** Crea y corre un contenedor a partir de la imagen
- **docker run --name \<container-id\>:** Corre un contenedor con un nombre especifico
- **docker rename \<nombre-actual\> \<nuevo-nombre\>:** Cambiar el nombre a un contenedor
- **docker rm \<container-id\>:** Eliminar un contenedor
- **docker rm -f \<container-id\>:** Elimina un contenedor auque este corriendo
- **docker container prune:** Eliminar todos los contenedores que estan apagados
- **docker run -it:** Correr un contenedor en modo interactivo 
- **docker exec:** Ejecuta un nuevo comando en un contenedor en ejecución
- **docker run -d:** Ejecuta un contenedor en modo background | detach
- **docker run -p \<puerto-de-anfitrion\>:\<puerto-de-contenedor\>:** Exponer un contenedor
- **docker logs \<container-id\>:** Ver los logs del contenedor
- **docker logs -f \<container-id\>:** Ver los logs del contenedor en tiempo real
- **docker logs --tail 10 -f \<container-id\>:** Ver las ultimas 10 lineas del log
- **docker stop \<container-id\>:** Detiene el main proces de un contenedor
- **docker start \<container-id\>:** Inicia el main proces de un contenedor
- **docker -v \<directorio-anfitrion\>:\<directorio-contenedor\>:** Bind mounts