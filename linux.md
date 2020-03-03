# Sistema Operativo Linux

# Introducción a la terminal y linea de comandos

La siguiente es una lista de comandos que nos pueden ayudar con las tareas que realizamos desde la terminal.

    # Comando para ver la fecha actual
    $ date

    # Comando para imprimir algo en la pantalla
    $ echo "Lo que se desea imprimir"

    # Este comando es muy util ya que muestra la información de un comando especifico
    $ man date

    # Muestra un listado de los comandos que se han ejecutado con un identificador
    $ history

    # Si deseo ejecutar un comando que aparece en la lista luego de hacer history, con el simbolo ! y el id del comando lo puedo volver a ejecutar.
    $ !234

## Gestión del árbol de directorios

Nos muestra nuestra ubicación actual en el árbol de directorios (Print Working Directory).

    $ pwd

Nos muestra el contenido de las carpetas de nuestro sistema operativo. Podemos especificar alguna ruta o, por defecto, listar el contenido de la carpeta donde estamos trabajando.

    $ ls
    $ ls /home/user/documentos

Lista todos los archivos incluyendo aquellos que se han definido como ocultos

    $ ls -a

Ordena los archivos por fecha de modificación:

    $ ls -t

Ordena los archivos por extensión:

    $ ls -x

Muestra toda la información: usuario, grupo, permisos, tamaño, fecha y hora de creación.

    $ ls -l

Muestra la misma información que ls -l pero con las unidades de tamaño en KB, MB:

    $ ls -lh

Muestra el contenido de todos los subdirectorios de forma recursiva:

    $ ls -R

Ordena los resultados por tamaño de archivo:

    ls -S

Cambiar nuestra ubicación en el árbol de directorios (Change Directory). Usamos dos puntos (..) para referirnos al directorio padre y solo uno (.) para referirnos a nuestro directorio actual.

    $ cd ~/.ssh
    $ cd ..

Nos ayuda a crear archivos desde la terminal.

    $ touch filename.txt

Nos ayuda a crear carpetas desde la terminal.

    $ mkdir mydir

Nos permite duplicar archivos y carpetas.

    $ cp [archivo que se va a copiar] [directorio hacia el que se va a mover]

Mover un archivo, cambiar su ubicación. La sintaxis es así:

    $ mv [ruta del archivo] [directorio hacia el que se va a mover]

Nos ayuda a eliminar un archivo.

    $ rm myfile

eliminar un directorio. En este caso es importante resaltar que, para que el directorio pueda ser eliminado, no puede contener archivos u otros directorios en su interior.

    $ rmdir [ruta / nombre del directorio a eliminar]

Recuerda que la terminal de Linux es sensible a la diferencia entre mayúsculas o minúsculas.

# Administración de Servidores Linux

## Distribuciones más utilizadas de Linux

Vamos a usar dos distribuciones de Linux: Ubuntu Server en su versión 18.04 y CentOS Server versión 7.

Recuerda que puedes usar cualquier versión para hacer pruebas y estudiar, pero al trabajar con servidores debemos instalar las versiones LTS, ya que incluyen soporte de largo plazo (actualizaciones de software por al menos 5 años).

Recuerda que puedes probar estas distribuciones con una máquina virtual o el proveedor de nube que prefieras (Google, Amazon, Digital Ocean, entre otros).

## Diferencias entre LESS, CAT, HEAD y TAIL para lectura de archivos

cat: nos permite leer archivos en su totalidad.

less: nos ayuda a leer el contenido de nuestros archivos por páginas. Nos movemos con las flechas del teclado o la tecla de espacio. Salimos de la lectura del archivo con la letra q. Buscamos palabras específicas escribiendo /palabra.

tail: nos muestra las últimas 10 líneas de nuestros archivos.

head: nos muestra las primeras 10 líneas de nuestros archivos.

## Interacción con archivos y permisos

Con el comando ls -l podemos observar la lista de archivos de nuestro directorio actual con información un poco más detallada. El primer campo nos indica los diferentes permisos para cada archivo o directorio. Por ejemplo: -rwxrw-r--.

El primer carácter nos indica si tenemos un archivo (-), enlace simbólico (l) o directorio (d).

Los siguientes caracteres se dividen en grupos de 3: lectura (r), escritura (w) y ejecución (x). El primer grupo son los permisos del usuario que creó ese archivo, el segundo para el grupo al que pertenece este usuario y el tercero para cualquier otro usuario de tu sistema operativo.

Los grupos nos ayudan a darle los mismos permisos a diferentes usuarios sin necesidad de asignarlos a cada uno individualmente. Todos los usuarios que pertenezcan al grupo tendrán los mismos permisos.

Si en vez de estas letras encuentras un guion significa que ese usuario o grupo de usuarios no tiene permiso para esa acción en particular.

Por ejemplo: -rwxrw-r-- nos indica que trabajamos con un archivo. Todos los usuarios del sistema tienen permisos de lectura. El usuario creador y su grupo tienen permiso de escritura. Y solo el usuario creador puede ejecutar el archivo.

También podemos encontrar estos permisos como 3 números del 1 al 7. Estos números son la suma de los 3 caracteres de permisos para cada usuario o grupo.

    - = 0
    x = 1
    w = 2
    r = 4

Por lo tanto, los permisos de nuestro archivo de ejemplo serían: 7 (1+2+4) 6 (0+2+4) 4 (0+0+4).

Para cambiar los permisos de un archivo o directorio podemos usar el comando chmod + a quién queremos añadir o quitar los permisos:


    El usuario propietario: u.
    El grupo, g.
    El resto de usuarios, o.
    Para todos, a.

Por ejemplo, para añadir permisos de ejecución a nuestro usuario propietario usamos:

    $ chmod u+x nombre-del-archivo

También podemos cambiar al usuario propietario del archivo con el comando chown.

    $ sudo chown nuevo-usuario:grupo-usuarios nombre-del-archivo
  
## Conociendo las terminales en linux

Las distribuciones de Linux para servidores no incluyen interfaz gráfica, ya que consumen muchos recursos. Esto significa que siempre vamos a trabajar desde la terminal.

Tendremos disponibles 6 terminales virtuales a las que podemos entrar o salir con las teclas Ctrl + Alt + Fx. También podemos usar el comando chvt. La séptima terminal es la interfaz gráfica, así que en este caso no disponemos de ella.

Cada usuario activo en nuestro sistema operativo crea una nueva conexión. Podemos ver todas estas conexiones con los comandos who y w (este último nos da un poco más de información).

Para ver todos los procesos que corren en el sistema podemos usar el comando ps. Para filtrar los procesos y ver únicamente las conexiones de los usuarios usamos ps -ft tty.

Este comando nos muestra el identificador de cada proceso. Para terminarlo podemos usar el comando kill -9 PID.

## Manejo y monitoreo de procesos y recursos del sistema

Para ver todos los procesos que corren en el sistema podemos usar el comando ps. Recuerda que puedes ver la documentación de este comando con el comando man ps.

El comando grep nos ayuda a filtrar el resultado de un comando o archivo dependiendo de las palabras de cada línea. Para esto también vamos a usar el pipe (|), un símbolo que nos ayuda a enviar el resultado de un comando a un segundo comando.

Por ejemplo, el comando ps aux | grep platzi imprime los procesos activos del sistema y, con ayuda del pipe, envía la lista al comando grep para filtrar el resultado, mostrando únicamente las líneas con la palabra platzi.

## Monitoreo de recursos del sistema

El comando top nos permite interactuar con una interfaz gráfica que nos muestra información específica del sistema operativo: cantidad de usuarios, tareas corriendo o “durmiendo”, identificadores de los procesos, entre otras.

Para ver la información de la CPU podemos usar el comando cat /proc/cpuinfo | grep "processor". Recuerda que Linux hace diferencia entra mayúsculas y minúsculas, pero puedes usar el comando grep -i para filtrar sin estas diferencias.

Para ver la información de la memoria podemos usar el comando free o, para que la información sea más fácil de leer, free -h. Y para ver el uso del disco duro está el comando du o du -hsc.

Si quieres verificar cuales son los 5 procesos que mas estan consumiendo CPU puedes utilizar el siguiente comando.

    $ sudo ps auxf | sort -nr -k 3 | head -5

Si lo que quieres es verificar que servicios son los que estan consumiendo mas ram puedes hacer uso del siguiente comando.

    $ $ sudo ps auxf | sort -nr -k 4 | head -5

## Análisis de los parámetros de red

Una IP es un identificador único para los equipos que están conectados a una red.

Las IPs Privadas se utilizan para identificar los dispositivos dentro de una red local. Por ejemplo: los dispositivos conectados en tu casa u oficina.

Las IPs Públicas son la que se asignan a cualquier dispositivo conectado a Internet. Por ejemplo: los servidores que alojan tus sitios web, el router que te da acceso a internet, entre otros.

Si tu dispositivo tiene una IP pública significa que puede conectarse a otro que también tenga una. Por esto mismo, no puede haber dos dispositivos con la misma IP pública.

Para encontrar la dirección IP de nuestros dispositivos podemos usar los comandos ifconfig en Linux y Mac o ipconfig en Windows. También podemos usar el comando ip a.

Para ver el nombre/identificador de nuestro equipo en todas las redes podemos usar el comando hostname. También podemos ver qué dispositivo nos permite acceso a Internet con el comando route -n.

Para identificar las IPs de diferentes dominios podemos usar el comando nslookup nombredominio.ext. También podemos usar el comando curl para realizar consultas a algún servidor y tambien puedes utilizar wget.

## Administración de paquetes acorde a la distribución

Cada distribución de Linux maneja su software de maneras diferentes.
Red Hat / CentOS / Fedora

Su gestor de paquetes es .rpm (Red hat Package Manager). La base de datos de este gestor está localizada en /var/lib/rpm.

El comando rpm -qa nos permite listar todos los rpms instalados en la máquina. Con rpm -i nombre-del-paquete.rpm instalamos los paquetes y con rpm -e nombre-del-paquete.rpm los removemos el sistema.

Los paquetes se pueden instalar desde un repositorio sin tener que conocer la ruta del archivo o las dependencias con el comando yum install nombre-del-paquete.

También podemos buscar paquetes más específicos con el comando yum search posible-nombre-del-paquete .
Debian / Ubuntu

Su administración de paquetes es .deb. Podemos realizar las instalaciones con dpkg -i nombre-del-paquete.deb o repositorios apt.

Su base de datos está localizada en /var/lib/dpkg. Con el comando dpkg -l listamos todos los debs instalados en la máquina. Instalamos los paquetes con dpkg -i nombre-del-paquete y los removemos del sistema con dpkg -r nombre-del-paquete.

Si ya tenemos software configurado podemos usar el comando dpkg-reconfigure nombre-paquete para volver a ejecutar el asistente de configuración (si está disponible).

También podemos realizar las instalaciones con el comando apt install nombre-paquete y búsquedas de paquetes con apt search posible-nombre-paquete.

## Manejo de paquetes en sistemas basados en Debian

Antes de actualizar el software de nuestro sistema debemos ejecutar el comando sudo apt update para saber qué paquetes pueden actualizarse y desde dónde se realizará la descarga. Luego de esto podremos actualizar todas las herramientas del sistema usando el comando sudo apt upgrade.

Recuerda que todo lo que tenga que ver con actualizaciones o modificaciones del sistema operativo necesitará permisos con sudo. También necesitarás conexión a Internet.

## Nagios: Desempaquetado, descompresión, compilación e instalación de paquetes

No todo el software que necesitamos se encuentra en los repositorios. Debido a esto, algunas veces debemos descargar el software, realizar un proceso de descompresión y desempaquetado para finalmente instalar la herramienta.

Instalación de algunas herramientas para manejar una base de datos MySQL (recuerda que instalaremos y trabaremos con MySQL en una próxima clase):

    $ sudo apt install build-essential libgd-dev openssl libssl-dev unzip apache2 php gcc libdbi-perl libdbd-mysql-perl

Instalación de Nagios:

    $ wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.4.tar.gz -O nagioscore.tar.gz

Descomprimir y desempaquetar archivos con tar:

    $ tar xvzf nagioscore.tar.gz

Este comando creará una carpeta nagios-4.4.4. El nombre de la carpeta puede variar dependiendo de la versión que descargaste. Entrando a esta carpeta podemos ejecutar diferentes archivos y comandos para configurar el software y realizar la instalación.


    $ sudo ./configure --with-https-conf=/etc/apache2/sites-enabled

    $ sudo make all

    $ sudo make install

    $ sudo make install-init

    $ sudo make install-commandmode

    $ sudo make install-config

    $ sudo make install-webconf

Por último, para administrar el servicio de nagios podemos usar el comando sudo systemctl (status, start, restart, reload, stop, enable, disable, list-dependencies) nagios.

## Los usuarios, una tarea vital en el proceso de administración del sistema operativo

El comando id nos muestra el identificador único (uid) de cada usuario en nuestro sistema operativo. El ID 0 está reservado para el usuario root.

Con el comando whoami podemos ver con qué usuario estamos trabajando en este momento. Podemos ver todos los usuarios del sistema leyendo el archivo /etc/passwd.

Las contraseñas de los usuarios están almacenadas en el archivo etc/shadow, pero están cifradas. Y solo el usuario root tiene permisos de lectura/escritura.

Para cambiar la contraseña de nuestros usuarios usamos el comando passwd.

## Creando y manejando cuentas de usuario en el sistema operativo

Comandos para administrar cuentas de usuarios:

- sudo useradd nombre-usuario: crea un usuario sin asignarle inmediatamente alguna contraseña ni consultar más información. Debemos terminar de configurar esta cuenta a mano posteriormente.

- sudo adduser nombre-usuario: crea un nuevo usuario con contraseña y algo más de información. También creará una nueva carpeta en la carpeta /home/.

- userdel nombre-usuario: eliminar cuentas de usuarios.

- usermod: modificar la información de alguna cuenta.

Nunca modifiques a mano el archivo /etc/passwd. Para administrar los usuarios debemos usar los comandos que estudiamos en clase.

## Entendiendo la membresía de los grupos

Los grupos nos ayudan a darle los mismos permisos a diferentes usuarios al mismo tiempo, sin necesidad de asignar el mismo permiso a cada usuario individualmente. Todos los usuarios que pertenezcan al mismo grupo tendrán los mismos permisos.

Para cambiar de usuario sin necesidad de reiniciar el sistema podemos usar el comando su - nombre-usuario. También podemos cambiar de usuario sin necesidad de saber su contraseña usando el comando sudo su - nombre-usuario.

Para ver a qué grupos pertenecen nuestros usuarios usamos el comando groups nombre-usuario. Para agregar usuarios a un nuevo grupo usamos el comando sudo gpasswd -a nombre-usuario nombre-grupo. Los eliminamos de la misma forma con gpasswd -d.

Para esto también podemos usar el comando sudo usermod -aG nombre-grupo nombre-usuario. Recuerda que en este caso el orden en que escribimos el grupo y el ususario se invierte.

Para listar los permisos de nuestros usuarios ejecutamos el comando sudo -l.


## Usando PAM para el control de acceso de usuarios

PAM es un mecanismo para administrar a los usuarios de nuestro sistema operativo. Nos permite autenticar usuarios, controlar la cantidad de procesos que ejecutan cada uno, verificar la fortaleza de sus contraseñas, ver la hora a la que se conectan por SSH, entre otras.

Con el comando pwscore podemos probar qué tan fuertes son nuestras contraseñas. Recuerda que para usar este comando en sistemas basados en Ubuntu debemos instalar el paquete libpwquality-tools.

El comando ulimit nos ayuda a listar los permisos de nuestros usuarios. Para limitar el número de procesos que nuestros usuarios pueden realizar ejecutamos ulimit -u max-numero-procesos.


