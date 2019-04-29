# Comandos para trabajar con Git y GitHub

## Configuración Básica de Git
git --version
git config --global user.name
git config --global user.email
git config --global color.ui true

## Iniciar un repositorio
git init nombre_repositorio

## Borrar un repositorio
rm -rf .git

## Evaluar estado de archivos
git status

## Agregar archivos al stange
git add nombre_archivo

## Agregar todos los archivos modificados o nuevos al stange
git add -A

## Eliminar un archivo de stange
git rm --cached nombre_archivo

## Eliminar un archivo de git
git rm -f nombre_archivo

## Hacer un commit
git commit -m comentario

## Agregar archivo a un commit que ya se realizo
git commit --amend

## Agregar etiquetas para versionar el proyecto
git tag 0.5 -m comentario_etiqueta

## Agregar etiqueta a una version en concreto
git tag 0.5 sha1_commit

## Borrar una etiqueta
git tag -d 0.5

## Renombrar una etiqueta
git tag -f -a 0.5 -m comentario_etiqueta sha1_commit

## Ver el log de commit
git log

## Ver el log de forma resumida
git log --oneline

## Ver el grafico del log
git log --oneline --graph

## Ver diferencia entre versiones
git diff sha1 vos sha2

## Resetear commit 
git reset --soft sha1
git reset --mixed sha1
git reset --hard sha1

## Configurar un editor de texto
git config --global core.editor nombre_editor

## Creacion de ramas para tener un mejor control del proyecto al trabajar en equipo
## Crear rama en el proyecto
git branch nombre_rama

## Listar las ramas creadas
git branch -l

## Borrar una rama
git branch -d nombre_rama

## Forzar el borrado de la rama
git branch -D nombre_rama

## Renombrar una rama creada
git branch -m nombre_actual nuevo_nombre

## Cambiar de rama
git checkout nombre_rama

## Cambiar a un commit
git checkout sha1_commit

## Crear rama y navegar directamente a ella
git checkout -b nombre_rama

## Para hacer un merge, primero posicionarse en la rama master
git merge nombre_de_rama

## Para no afectar el flujo del proyecto
git rebase nombre_de_rama

## Guardar un estado del proyecto cuando no se quiere hacer un commit
git stash

## Ver lista de stash
git stash list

## Para eliminar un stash
git stash drop id_stash

## Restablecer los cambios en la rama
git stash apply id_stash

## Resetear cambios en un archivo
git checkout -- nombre_archivo

## Elegir un commit para moverlo de rama
git cherry-pick sha1

* A partir de aqui son anotaciones de github
* Plataforma para compartir proyectos
* Crear una cuenta en esta plataforma

## Agregar repositorio remoto al repositorio local
git remote add origin url_repositorio

## Revisar el repositorio remoto
git remote -v

## Eliminar repositorio remoto
git remote remove origin

## Para traer archivos del remoto al local
git fetch origin master

## Hacer el merge del remoto con el local
git merge origin/master --allow-unrelated-histories

## Traer archivos y hacer el merge
git pull origin master

## Enviar cambios al repositorio remoto
git push origin master

## Enviar los tags al repositorio remoto
git push origin master --tags

## Enviar ramas al repositorio remoto
git push origin nombre_rama
