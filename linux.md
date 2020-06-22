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

    





