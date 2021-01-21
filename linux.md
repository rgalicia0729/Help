# Comandos para sistemas GNU/Linux

Fuente: https://blog.desdelinux.net/mas-de-400-comandos-para-gnulinux-que-deberias-conocer

## Información del sistema
---

- **arch:** mostrar la arquitectura de la máquina (1).
- **uname -m:** mostrar la arquitectura de la máquina (2).
- **uname -r:** mostrar la versión del kernel usado.
- **dmidecode -q:** mostrar los componentes (hardware) del sistema.
- **hdparm -i /dev/hda:** mostrar las características de un disco duro.
- **hdparm -tT /dev/sda:** realizar prueba de lectura en un disco duro.
- **cat /proc/cpuinfo:** mostrar información de la CPU.
- **cat /proc/interrupts:** mostrar las interrupciones.
- **cat /proc/meminfo:** verificar el uso de memoria.
- **cat /proc/swaps:** mostrar ficheros swap.
- **cat /proc/version:** mostrar la versión del kernel.
- **cat /proc/net/dev:** mostrar adaptadores de red y estadísticas.
- **cat /proc/mounts:** mostrar el sistema de ficheros montado.
- **lspci -tv:** mostrar los dispositivos PCI.
- **lsusb -tv:** mostrar los dispositivos USB.
- **date:** mostrar la fecha del sistema.
- **cal 2011:** mostrar el almanaque de 2011.
- **cal 07 2011:** mostrar el almanaque para el mes julio de 2011.
- **date 041217002011.00:** colocar (declarar, ajustar) fecha y hora.
- **clock -w:** guardar los cambios de fecha en la BIOS.

## Apagar (Reiniciar Sistema o Cerrar Sesión)
---

- **shutdown -h now:** apagar el sistema.
- **init 0:** apagar el sistema.
- **telinit 0:** apagar el sistema.
- **halt:** apagar el sistema.
- **shutdown -h hours:minutes &:** apagado planificado del sistema.
- **shutdown -c:** cancelar un apagado planificado del sistema.
- **shutdown -r now:** reiniciar.
- **reboot:** reiniciar.
- **logout:** cerrar sesión.

## Archivos y Directorios
---

- **cd /home:** entrar en el directorio “home”.
- **cd ..:** retroceder un nivel.
- **cd ../..:** retroceder 2 niveles.
- **cd:** ir al directorio raíz.
- **cd ~user1:** ir al directorio user1.
- **cd –:** ir (regresar) al directorio anterior.
- **pwd:** mostrar el camino del directorio de trabajo.
- **ls:** ver los ficheros de un directorio.
- **ls -F:** ver los ficheros de un directorio.
- **ls -l:** mostrar los detalles de ficheros y carpetas de un directorio.
- **ls -a:** mostrar los ficheros ocultos.
- **ls \*[0-9]\*:** mostrar los ficheros y carpetas que contienen números.
- **tree:** mostrar los ficheros y carpetas en forma de árbol comenzando por la raíz.
- **lstree:** mostrar los ficheros y carpetas en forma de árbol comenzando por la raíz.
- **mkdir dir1:** crear una carpeta o directorio con nombre ‘dir1’.
- **mkdir dir1 dir2:** crear dos carpetas o directorios simultáneamente (Crear dos directorios a la vez).
- **mkdir -p /tmp/dir1/dir2:** crear un árbol de directorios.
- **rm -f file1:** borrar el fichero llamado ‘file1’.
- **rmdir dir1:** borrar la carpeta llamada ‘dir1’.
- **rm -rf dir1:** eliminar una carpeta llamada ‘dir1’ con su contenido de forma recursiva. (Si lo borro recursivo estoy diciendo que es con su contenido).
- **rm -rf dir1 dir2:** borrar dos carpetas (directorios) con su contenido de forma recursiva.
- **mv dir1 new_dir:** renombrar o mover un fichero o carpeta (directorio).
- **cp file1:** copiar un fichero.
- **cp file1 file2:** copiar dos ficheros al unísono.
- **cp dir /* .:** copiar todos los ficheros de un directorio dentro del directorio de trabajo actual.
- **cp -a /tmp/dir1 .:** copiar un directorio dentro del directorio actual de trabajo.
- **cp -a dir1:** copiar un directorio.
- **cp -a dir1 dir2:** copiar dos directorio al unísono.
- **ln -s file1 lnk1:** crear un enlace simbólico al fichero o directorio.
- **ln file1 lnk1:** crear un enlace físico al fichero o directorio.
- **touch -t 0712250000 file1:** modificar el tiempo real (tiempo de creación) de un fichero o directorio.
- **file file1:** salida (volcado en pantalla) del tipo mime de un fichero texto.
- **iconv -l:** listas de cifrados conocidos.
- **iconv -f fromEncoding -t toEncoding inputFile > outputFile:** crea una nueva forma del fichero de entrada asumiendo que está codificado en fromEncoding y convirtiéndolo a ToEncoding.
- **find . -maxdepth 1 -name *.jpg -print -exec convert ”{}” -resize 80×60 “thumbs/{}” \;:** agrupar ficheros redimensionados en el directorio actual y enviarlos a directorios en vistas de miniaturas (requiere convertir desde ImagemagicK).

## Encontrar archivos
---

- **find / -name file1:** buscar fichero y directorio a partir de la raíz del sistema.
- **find / -user user1:** buscar ficheros y directorios pertenecientes al usuario ‘user1’.
- **find /home/user1 -name \\*.bin:** buscar ficheros con extensión ‘. bin’ dentro del directorio ‘/ home/user1’.
- **find /usr/bin -type f -atime +100:** buscar ficheros binarios no usados en los últimos 100 días.
- **find /usr/bin -type f -mtime -10:** buscar ficheros creados o cambiados dentro de los últimos 10 días.
- **find / -name \\*.rpm -exec chmod 755 ‘{}’ \;:** buscar ficheros con extensión ‘.rpm’ y modificar permisos.
- **find / -xdev -name \\*.rpm:** Buscar ficheros con extensión ‘.rpm’ ignorando los dispositivos removibles como cdrom, pen-drive, etc.…
- **locate \\*.ps:** encuentra ficheros con extensión ‘.ps’ ejecutados primeramente con el command ‘updatedb’.
- **whereis halt:** mostrar la ubicación de un fichero binario, de ayuda o fuente. En este caso pregunta dónde está el comando ‘halt’.
- **which halt:** mostrar la senda completa (el camino completo) a un binario / ejecutable.

