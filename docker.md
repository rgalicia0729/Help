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

- **docker --version** Ver la versión de docker
- **docker info** Ver información sobre docker
- **docker ps** Muestra los contenedores que estan corriendo
- **docker ps -a** Muestra todos los contenedores
- **docker inspect <container-id>** Muestra la información del contenedor
- **docker run <nombre-imagen>** Crea y corre un contenedor a partir de la imagen
- **docker run --name <nombre-contenedor>** Corre un contenedor con un nombre especifico
- **docker rename <nombre-actual> <nuevo-nombre>** Cambiar el nombre a un contenedor
- **docker rm <nombre-contenedor>** Eliminar un contenedor
- **docker container prune** Eliminar todos los contenedores que estan apagados

