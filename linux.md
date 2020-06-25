# Sistema Operativo Linux

## comandos básicos

Mostrar la fecha del sistema operativo

    $ date

Imprimir algo en la terminal

    $ echo "Lo que queremos imprimir"

Mostrar la información sobre un comando

    $ man ls

Muestra los comandos que se han ejecutado ultimamente

    # history

Para ejecutar un comando especifico que este en la salida de history, con el signo de admiración y el id del comando.

    $ !433

## Comandos para trabajar desde nuestra ubicación

Lista los archivos que se encuentran en el directorio sobre el que estamos trabajando:

    $ ls

Lista todos los archivos incluyendo aquellos que se han definido como ocultos:

    $ ls -a

Todos los directorios contienen los archivos . y .., estos son punteros a directorios.

    .. --> directorio padre
    . --> directorio actual

Otros parámetros que puedes usar con el comando ls:

Ordena los archivos por fecha de modificación:

    $ ls -t

Ordena elementos primero por nombre y después por extensión:

    $ ls -x

Ordena los elementos primero por extensión y luego por nombre:

    $ ls -X

Muestra toda la información: usuario, grupo, permisos, tamaño, fecha y hora de creación.

    $ ls -l

Muestra la misma información que ls -l pero con las unidades de tamaño en KB, MB:

    $ ls -lh

Muestra el contenido de todos los subdirectorios de forma recursiva:

    $ ls -R

Ordena los resultados por tamaño de archivo:

    $ ls -S

## Comandos para cambiar de ubicación

Print Working Directory: se usa para mostrar el directorio actual en el que nos encontramos trabajando.

    $ pwd

cd: se utiliza para cambiar de directorio. Luego del comando se debe especificar la ruta del directorio al que nos queremos mover. Por ejemplo:

    $ cd /home/mi_usuario

## Comandos para mover, copiar o borrar

cp: copiar un archivo hacia un directorio.

    $ cp [archivo que se va a copiar] [directorio hacia el que se va a mover]

rm: eliminar un archivo.

    $ rm archivo.txt

`mv``: mover un archivo, cambiar su ubicación. La sintaxis es así:

    $ mv [ruta del archivo] [directorio hacia el que se va a mover]

rmdir: eliminar un directorio. En este caso es importante resaltar que, para que el directorio pueda ser eliminado, no puede contener archivos u otros directorios en su interior.

    $ rmdir [ruta / nombre del directorio a eliminar]

## Utilidades batch (procesamiento por lotes)

Muestra el contenido completo de un archivo

    $ cat 'nombre del archivo'

Muestra las primeras lineas de un archivo de texto

    $ head 'nombre del archivo'

    $ head -n 5 'nombre del archivo' -> Para ver las primeras 5 lineas de un archivo.

Muestra las ultimas lineas de un archivo de texto

    $ tail 'nombre del archivo'

    $ tail -n 10 'nombre del archivo' -> Para ver las ultimas 10 lineas de un archivo.

## Utilidades batch avanzadas

Busqueda por expresiones regulares

    $ grep 'regexp' 'nombre del archivo'

    $ grep -i 'regexp' 'nombre del archivo' -> No toma en cuenta si esta en mayusculas o minusculas

Tratamiento de flujo de caracteres

    $ sed 's/antigua/nueva/g' 'nombre del archivo' -> Remplaza la palabra antigua por nueva

    $ sed '$d' 'nombre del archivo' -> Elimina la ultima linea

Tratamiento de texto delimitado

    $ awk -F ',' '{ print $1 }' 'nombre del archivo' -> Imprime la primera columna de un archivo delimitado por comas.

    $ awk -F ',' 'NR > 1 && $3 > 0 { print $1, $3 * 4 }' 'nombre del archivo' -> Imprime si sucede una condicion y puede calcular entre columnas.

## Comunicación entre procesos: Qué son y cómo se utilizan los flujos estándar

Si lo que deseamos es ejecutar un programa y enviarle información que se encuentra en un arhivo para que sea ejecutado con las instrucciones del archivo. Por ejemplo ejecutamos mysql y le enviamos instrucciones que se encuentran en un archivo llamado backup.sql lo hacemos de la siguiente manera.

    $ mysql -h 127.0.0.1 -u root -p123 < backup.sql

Ahora si lo que deseamos es ejecutar un programa y escribir los resultados en un archivo para luego analizarlos, lo hacemos de la siguiente manera.

    $ ls -l > data.txt

Con la instrucción anterior si el archivo existe se remplaza por uno nuevo, si lo que queremos es enviar el resultado al final del archivo hacemos lo siguiente.

    $ ls -la >> data.txt

En muchas ocaciones lo que vamos a necesitar es encadenar procesos, esto lo podemos hacer mas facil utilizando los pipe. A continuación se muestra un ejemplos de conteo de lineas sobre un archivo.

    $ cat data.txt | wc -l

## Administración de procesos en background y foreground

Si deseas ejecutar procesos en segundo plano se coloca el signo & al final del comando

    $ mysql -h 127.0.0.1 -u root -p123 < dump.sql &

Para ver los procesos que se estan ejecutando

    $ ps

Si queremos ver todos los procesos que se estan ejecutando en el sistema

    $ ps ax

Ver los procesos en tiempo real

    $ top

Como detener un proceso inmediatamente

    $ kill -9 'PID'

La Administración de Servidores está a cargo de muchas tareas: instalar herramientas, mantener el sistema operativo actualizado, gestionar usuarios y permisos, monitorear los servicios y puertos abiertos del sistema, identificar amenazas y vulnerabilidades, entre muchas otras.

En esta ocasión vamos a estudiar cómo funcionan los usuarios y permisos de nuestros servidores y computadoras personales con Linux o Mac.

### Permisos para Usuarios, Grupos y Super Usuarios

Nuestro trabajo consiste en limitar las acciones que pueden realizar los usuarios de nuestros sistemas. Debemos encargarnos de que los usuarios no tengan más permisos de los que deberían tener.

Los grupos de usuarios nos permiten darles los mismos permisos a diferentes usuarios. Todos los usuarios que pertenezcan al mismo grupo tendrán los mismos permisos. Así evitamos tener que darle los mismos permisos a cada usuario individualmente, uno por uno. Con solo cambiar los permisos del grupo cambiamos el permiso de todos los usuarios.

También están los super usuarios, la parte más alta de la pirámide, los que pueden hacer cualquier cosa. Lo ideal no es trabajar con este tipo de usuarios, ya que podrá activar procesos o realizar tareas que afecten nuestro servidor o generar vulnerabilidades. Más bien, debemos crear usuarios para cada tarea en específico que realizamos en nuestros servidores.

### Cómo funcionan los permisos

Cuando ejecutamos el comando ls podemos ver la lista de archivos y subcarpetas de la ruta donde nos encontramos. Si usamos este comando con la opción -lh podemos ver un poco más de información: fecha de modificación, peso, usuario propietario, grupo al que es miembro este archivo y los permisos.

Concentrémonos en la primera parte, la de los permisos:

    drwxrw-r-- usuario grupo
    drwx------ usuario grupo
    -rwxr-xr-x usuario grupo
    -rwx------ usuario grupo

La primera letra puede ser una d para indicar que hablamos de una subcarpeta o un guion (-) cuando evaluamos archivos.

Las siguientes 9 letras debemos dividirlas en grupos de 3. El primer grupo son los permisos del usuario propietario del archivo. El segundo son los permisos del grupo al que pertenece el archivo. Y el tercero son los permisos para cualquier otro usuario del sistema operativo.

Cada grupo de 3 puede comenzar con la letra r, refiriéndose a los permisos de lectura., continuar con w para referirse a los permisos de escritura y terminar con una x para indicar los permisos de ejecución.

Si en vez de estas letras encuentras un guion (-) significa que no ese usuario o grupo de usuarios no tienen ese tipo de permisos.

Veámoslo más claro con un ejemplo:

Estos son los permisos: -rwxr-xr-- juandc estudiantes-platzi.

- Estamos trabajando con un archivo.

- El usuario propietario es juandc.

- Este archivo pertenece al grupo de estudiantes-platzi.

- El usuario propietario (juandc) tiene permiso para todo: leer, escribir y ejecutar el archivo.

- El grupo al que pertenece el archivo solo tiene permisos para leer y ejecutar el archivo, no para editarlo.

- El resto de usuarios de sistema operativo solo tienen permisos para leer el archivo, no para escribirlo ni ejecutarlo.

### Actualización de permisos y propietarios

Bueno, ya sabemos leer los permisos, pero nos hace falta poder cambiarlos. Y para esto vamos a usar los comandos chmod y chown.

Cuando nos refiramos al usuario propietario debemos usar la letra u. Si cambiamos los permisos del grupo una g. Si queremos cambiar los permisos de cualquier otro usuario usamos la o. Y si queremos cambiar los permisos de TODOS usamos la a.

    # Añadir permisos de escritura al grupo:
    $ chmod g+w archivo.txt

    # Eliminar permisos de lectura a los usuarios no propietarios
    # ni miembros del grupo al que pertenece el archivo:
    $ chmod o-r

    # Añadir permisos de ejecución a todos (cualquier usuario):
    $ chmod a+x archivo.txt

Pero no solo podemos representar los permisos usando letras, también podemos hacerlo en formato numérico, con 3 números del 0 al 7:

    - = 0
    x = 1
    w = 2
    r = 4

Debemos sumar las 3 letras de cada permiso para obtener el “número definitivo”. Así que, continuando con el ejemplo anterior:

- Permisos del usuario propietario: r (4) + w (2) + x (1) = 7.
- Permisos del grupo al que pertenece el archivo: r (4) + x (1) = 5.
- Permisos del grupo al que pertenece el archivo: r (4) = 4.

Todo esto para un conseguir un resultado de 754. Así que, si queremos eliminar los permisos de ejecución para el grupo, podemos usar el comando chmod con el número 744.

    chmod 744 archivo.txt

Ahora digamos que queremos cambiar el usuario propietario de nuestro archivo. Para esto usaremos el comando chown seguido del nuevo usuario o grupo propietario del archivo.

    # Cambiar el usuario propietario:
    $ sudo chown nuevo-usuario archivo.txt

    # Cambiar el grupo propietario:
    $ sudo chown :nuevo-grupo archivo.txt

    # Cambiar el usuario y grupo propietario:
    $ sudo chown nuevo-usuario:nuevo-grupo archivo.txt

## Compresión de archivos

Hay ocaciones que lo que queremos es comprimir un archivo de modo que su tamaño sea reducido, para esto podemos hacer uso de gzip.

    $ gzip 'nombre del archivo'

Para descomprimir el archivo y volver al archivo original.

    $ gzip -d 'nombre del archivo comprimido'

Para agrupar un conjunto de archivos utilizamos la herramienta de tar

    $ tar cf 'nombre-de-archivo-resultado.tar' 'nombres de los archivos para agrupar'

Para ver el contenido de loa archivos agrupados con .tar

    $ tar tf 'nombre del archivo'.tar

Para desagrupar los archivos de .tar

    $ tar xf 'nombre del archivo'.tar

Para agrupar los archivos y comprimir

    $ tar czf 'nombre-de-resultado.tgz' 'nombre de los archivos para agrupar y comprimir'

## Herramientas de búsqueda de archivos

Hacer una busqueda en todo el sistema de archivos solo con el nombre.

    $ sudo updatedb

    $ locate 'Nombre del archivo a buscar'

Para buscar archivos binarios.

    $ whereis 'nombre del comando'

Podemos hacer una busqueda con criterios

    $ find / -user idt -perm 400 -type f -mime +7

## Herramientas para interactuar a través de HTTP

    $ curl 'Dominio'

    $ curl -v 'Dominio'

    $ wget 'Dominio del archivo a descargar'

