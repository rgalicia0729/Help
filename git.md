# ¿Por qué usar un sistema de control de versiones como Git?
Un sistema de control de versiones como Git nos ayuda a guardar el historial de cambios y crecimiento de los archivos de nuestro proyecto.

En realidad, los cambios y diferencias entre las versiones de nuestros proyecto pueden tener similitudes, algunas veces los cambios pueden ser solo una palabra o una parte específica de un archivo específico. Git está optimizado para guardar todos estos cambios de forma atómica e incremental, o sea, aplicando cambios sobre los últimos cambios, estos sobre los cambios anteriores y así hasta el inicio de nuestro proyecto.

* El comando para iniciar nuestro repositorio, o sea, indicarle a Git que queremos usar su sistema de control de versiones en nuestro proyecto, es git init.
    
* El comando para que nuestro repositorio sepa de la existencia de un archivo o sus últimos cambios es git add. Este comando no almacena las actualizaciones de forma definitiva, solo las guarda en algo que conocemos como “Staging Area” (no te preocupes, lo entenderemos más adelante).
    
* El comando para almacenar definitivamente todos los cambios que por ahora viven en el staging area es git commit. También podemos guardar un mensaje para recordar muy bien qué cambios hicimos en este commit con el argumento -m "Mensaje del commit".
    
* Por último, si queremos mandar nuestros commits a un servidor remoto, un lugar donde todos podamos conectar nuestros proyectos, usamos el comando git push.

# ¿Qué es staging, repositorios y cuál es el ciclo básico de trabajo en GitHub?

Para iniciar un repositorio, o sea, activar el sistema de control de versiones de Git en tu proyecto, solo debes ejecutar el comando git init.

Este comando se encargará de dos cosas: primero, crear una carpeta .git donde se guardará toda la base de datos con cambios atómicos de nuestro proyecto; y segundo, crear un área en la memoria RAM, que conocemos como Staging, que guardará temporalmente nuestros archivos (cuando ejecutemos un comando especial para eso) y nos permitirá, más adelante, guardar estos cambios en el repositorio (también con un comando especial).

Ciclo de vida o estados de los archivos en Git:

Cuando trabajamos con Git, nuestros archivos pueden vivir y moverse entre 4 diferentes estados (cuando trabajamos con repositorios remotos pueden ser más estados pero lo estudiaremos más adelante):

* Archivos Tracked: Son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos git add y git commit.

* Archivos Staged: Son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando git add, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando git commit.

* Archivos Unstaged: Entiendelos como archivos “Tracked pero Unstaged”. Son archivos que viven dentro de Git pero no han sido afectados por el comando git add ni mucho menos por git commit. Git tiene un registro de estos archivos pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.

* Archivos Untracked: Son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por git add, así que Git no tiene registros de su existencia.

Recuerda que hay un caso muy raro donde los archivos tienen dos estados al mismo tiempo: Staged y Untracked. Esto pasa guardas los cambios de un archivo en el área de Staging (con el comando git add) pero, antes de hacer commit para guardar los cambios en el repositorio, haces nuevos cambios que todavía no han sido guardados en el área de Staging (en realidad, todo sigue funcionando igual pero es un poco divertido).

## Comandos para mover archivos entre los estados de Git:

* git status: Nos permite ver el estado de todos nuestros archivos y carpetas.
* git add: Nos ayuda a mover archivos del Untracked o Unstaged al estado Staged. Podemos usar git nombre-del-archivo-o-carpeta para añadir archivos y carpetas individuales o git add -A para mover todos los archivos de nuestro proyecto (tanto Untrackeds como unstageds).
* git reset HEAD: Nos ayuda a sacar archivos del estado Staged para devolverlos a su estado anterior. Si los archivos venían de Unstaged, vuelven allí. Y lo mismo se venían de Untracked.
* git commit: Nos ayuda a mover archivos de Unstaged a Staged. Esta es una ocasión especial, los archivos han sido guardado o actualizados en el repositorio. Git nos pedirá que dejemos un mensaje para recordar los cambios que hicimos y podemos usar el argumento -m para escribirlo (git commit -m "mensaje").
* git rm: Este comando necesita alguno de los siguientes argumentos para poder ejecutarse correctamente:
* git rm --cached: Mueve los archivos que le indiquemos al estado Untracked.
* git rm --force: Elimina los archivos de Git y del disco duro. Git guarda el registro de la existencia de los archivos, por lo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

# ¿Qué es un Branch (rama) y cómo funciona un Merge en Git?

Git es una base de datos muy precisa con todos los cambios y crecimiento que ha tenido nuestro proyecto. Los commits son la única forma de tener un registro de los cambios. Pero las ramas amplifican mucho más el potencial de Git.

Todos los commits se aplican sobre una rama. Por defecto, siempre empezamos en la rama master (pero puedes cambiarle el nombre si no te gusta) y creamos nuevas ramas, a partir de esta, para crear flujos de trabajo independientes.

Crear una nueva rama se trata de copiar un commit (de cualquier rama), pasarlo a otro lado (a otra rama) y continuar el trabajo de una parte específica de nuestro proyecto sin afectar el flujo de trabajo principal (que continúa en la rama master o la rama principal).

Los equipos de desarrollo tienen un estándar: Todo lo que esté en la rama master va a producción, las nuevas features, características y experimentos van en una rama “development” (para unirse a master cuando estén definitivamente listas) y los issues o errores se solucionan en una rama “hotfix” para unirse a master tan pronto como sea posible.

    Crear una nueva rama lo conocemos como Checkout. Unir dos ramas lo conocemos como Merge.

Podemos crear todas las ramas y commits que queramos. De hecho, podemos aprovechar el registro de cambios de Git para crear ramas, traer versiones viejas del código, arreglarlas y combinarlas de nuevo para mejorar el proyecto.

Solo ten en cuenta que combinar estas ramas (sí, hacer “merge”) puede generar conflictos. Algunos archivos pueden ser diferentes en ambas ramas. Git es muy inteligente y puede intentar unir estos cambios automáticamente, pero no siempre funciona. En algunos casos, somos nosotros los que debemos resolver estos conflictos “a mano”.

# Crea un repositorio de Git y haz tu primer commit

Si quieres ver los archivos ocultos de una carpeta puedes habilitar la opción de Vista > Mostrar u ocultar > Elementos ocultos (en Windows) o ejecutar el comando ls -a.

Le indicaremos a Git que queremos crear un nuevo repositorio para utilizar su sistema de control de versiones. Solo debemos posicionarnos en la carpeta raíz de nuestro proyecto y ejecutar el comando git init.

Recuerda que al ejecutar este comando (y de aquí en adelante) vamos a tener una nueva carpeta oculta llamada .git con toda la base de datos con cambios atómicos en nuestro proyecto.

Recuerda que Git está optimizado para trabajar en equipo, por lo tanto, debemos darle un poco de información sobre nosotros. No debemos hacerlo todas las veces que ejecutamos un comando, basta con ejecutar solo una sola vez los siguientes comandos con tu información:

    git config --global user.email "tu@email.com"
    git config --global user.name "Tu Nombre"
    
Existen muchas otras configuraciones de Git que puedes encontrar ejecutando el comando git config --list (o solo git config para ver una explicación más detallada).

# Analizar cambios en los archivos de tu proyecto con Git

El comando git show nos muestra los cambios que han existido sobre un archivo y es muy útil para detectar cuándo se produjeron ciertos cambios, qué se rompió y cómo lo podemos solucionar. Pero podemos ser más detallados.

Si queremos ver la diferencia entre una versión y otra, no necesariamente todos los cambios desde la creación del archivo, podemos usar el comando git diff commitA commitB.

Recuerda que puedes obtener el ID de tus commits con el comando git log.

# Volver en el tiempo en nuestro repositorio utilizando branches y checkout

El comando git checkout + ID del commit nos permite viajar en el tiempo. Podemos volver a cualquier versión anterior de un archivo específico o incluso del proyecto entero. Esta también es la forma de crear ramas y movernos entre ellas.

También hay una forma de hacerlo un poco más “ruda”: usando el comando git reset. En este caso, no solo “volvemos en el tiempo”, sino que borramos los cambios que hicimos después de este commit.

Hay dos formas de usar git reset: con el argumento --hard, borrando toda la información que tengamos en el área de staging (y perdiendo todo para siempre). O, un poco más seguro, con el argumento --soft, que mantiene allí los archivos del área de staging para que podamos aplicar nuestros últimos cambios pero desde un commit anterior.

# Resumen de comandos de Git

## Configuración Básica de Git
* git --version
* git config --global user.name
* git config --global user.email
* git config --global color.ui true

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
* git reset --soft sha1
* git reset --mixed sha1
* git reset --hard sha1

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
