## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Introducción al sistema operativo GNU/Linux

Como todos los sistemas operativos derivados de Unix, GNU/Linux dispone de un intérprete de comandos o terminal (en inglés se utiliza la palabra shell) que hace de interfaz entre el usuario y el propio sistema operativo y cuyo nombre es BASH.

> Desde Ubuntu, abrir un terminal BASH con CTRL-Shift-T

### 1. Sistema de archivos GNU/Linux

#### 1.1 Introducción

En GNU/Linux, todo es un archivo. Los archivos se organizan en directorios (los directorios son tipos particulares de archivos). Todos los archivos y directorios están ordenados en un gran árbol que tiene como raíz «/». 

- Cada directorio tiene un nombre que puede contener cualquier letra o símbolo excepto «/». El directorio raíz es una excepción: su nombre es «/» (pronunciado «barra« o «el directorio raíz«) y no puede ser renombrado. 

- Cada archivo o directorio es identificado con una **ruta** única. 

- El directorio raíz tiene un cierto número de ramificaciones, como «/etc/» y «/usr/». Estos subdirectorios a su vez se ramifican en más subdirectorios, como «/etc/init.d/» y «/usr/local/». El todo, visto colectivamente, es llamado el árbol de directorios.

	- **/etc/**: archivos principales para la configuración del sistema
	- **/var/log/**: archivos de registro del sistema
	- **/home/**: todos los archivos personales de los usuarios


#### 1.2 Comandos útiles para gestionar archivos

1. **cd /home**: entrar en el directorio "home"
1. **cd ..**: retroceder un nivel
1. **cd ../..**: retroceder dos niveles
1. **cd**: ir al directorio del usuario corriente
1. **pwd**: mostrar la ruta del directorio actual 
1. **ls**: ver los archivos del directorio
1. **ls -l**: mostrar los detalles de archivos y carpetas de un directorio
1. **ls -a**: mostrar los archivos ocultos
1. **mkdir INFO133**: crear una carpeta con mombre "INFO133"
1. **rm -R INFO133**: suprimir la carpeta "INFO133"
1. **touch hola.txt**: crear el archivo texto "hola.txt"
1. **mv hola.txt /home/INFO133**: desplaza el archivo hola.txt en la carpeta /home/INFO133
1. **find /home -name hola.txt**: buscar dónde se encuentra el archivo "hola.txt" a partir del directorio /home
1. **cp hola.txt ../hola2.txt**: duplicar el archivo en otra ruta
1. **ln -s hola2.txt hola3**: crear un enlace simbólico al archivo hola2.txt

#### 1.3 Ejercicio

1. Crear un repositorio "INFO133" en su carpeta de usuario (/home/REEMPLAZAR_CON_SU_NOMBRE_DE_USUARIO) con el comando **mkdir**
1. Crear un archivo texto vacio llamado mis_comandos.txt con el comando **touch**


### 2. Gestión de permisos en el sistema de archivos

#### 2.1 Introducción

Los permisos en el sistema de archivos en los sistemas tipo Unix se definen basandose en tres categorías o tipos de usuarios:
- el usuario que es dueño del archivo (**u**);
- los usuarios que pertenecen al mismo grupo al que pertenece el archivo (**h**);
- el resto de usuarios (**o**) también denominado «universo» o «todos».

Para cada archivo, cada permiso permite las siguientes acciones:
- el permiso de lectura (r) permite al dueño examinar el contenido del archivo;
- el permiso de escritura (w) permite al dueño modificar el archivo;
- el permiso de ejecución (x) permite al dueño ejecutar el archivo como una orden.

Para los directorios, cada permiso permite las siguientes acciones:
- el permiso de lectura (r) permite al dueño obtener una relación del contenido del directorio;
- el permiso de escritura (w) permite al dueño añadir o borrar archivos al directorio;
- el permiso de ejecución (x) permite al dueño acceder a los archivos del directorio.

El permiso de ejecución de un directorio no solo indican que se puede leer los archivos que contiene, sí no también permite ver sus atributos, como el tamaño y la fecha de modificación.

El comando **ls** se usa para mostrar los permisos (y más detalles) de archivos o directorios. Cuando se ejecuta con el parámetro «-l», muestra la información siguiente ordenada por campos:

- tipo de fichero (primer carácter: -, d, l, etc.),
- permisos del archivo (nueve caracteres, tres para el usuario, tres para el grupo y los tres últimos para el resto, en este orden),
-  número de enlaces duros al archivo,
-  nombre del usuario que es dueño del archivo,
- nombre del grupo al que pertenece,
- tamaño del archivo expresado en caracteres (bytes),
- fecha y hora del archivo (mtime),
- nombre del archivo.






