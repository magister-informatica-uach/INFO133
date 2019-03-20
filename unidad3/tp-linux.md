## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Introducción al sistema operativo GNU/Linux :yum:

Como todos los sistemas operativos derivados de Unix, GNU/Linux dispone de un intérprete de comandos o terminal (en inglés se utiliza la palabra shell) que hace de interfaz entre el usuario y el propio sistema operativo y cuyo nombre es BASH.

> Desde Ubuntu, abrir un terminal BASH con CTRL-Shift-T

### 1. Sistema de archivos GNU/Linux

#### 1.1 Introducción

En GNU/Linux, todo es un archivo. Los archivos se organizan en directorios (los directorios son tipos particulares de archivos). Todos los archivos y directorios están ordenados en un gran árbol que tiene como raíz «/». 

Cada directorio tiene un nombre que puede contener cualquier letra o símbolo excepto «/». El directorio raíz es una excepción: su nombre es «/» (pronunciado «barra« o «el directorio raíz«) y no puede ser renombrado. 

Cada archivo o directorio es identificado con una **ruta** única. 

El directorio raíz tiene un cierto número de ramificaciones, como «/etc/» y «/usr/». Estos subdirectorios a su vez se ramifican en más subdirectorios, como «/etc/init.d/» y «/usr/local/». El todo, visto colectivamente, es llamado el árbol de directorios.

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
1. **cat hola.txt**: mostrar el contenido del archivo hola.txt

#### 1.3 Ejercicio

> Crear un repositorio "INFO133" en su carpeta de usuario (/home/REEMPLAZAR_CON_SU_NOMBRE_DE_USUARIO) con el comando **mkdir**
> Crear un archivo texto vacio llamado mis_comandos.txt con el comando **touch**
> Escribir "Hola" en el archivo mis_comandos.txt
> Utilizar el comando **cat** para mostrar el contenido de mis_comandos.txt

### 2. Gestión de permisos en el sistema de archivos

#### 2.1 Introducción

Los permisos en el sistema de archivos en los sistemas tipo Unix se definen basandose en tres categorías o tipos de usuarios:
- el usuario que es dueño del archivo (**u**);
- los usuarios que pertenecen al mismo grupo al que pertenece el archivo (**h**);
- el resto de usuarios (**o**) también denominado «universo» o «todos».

Para cada archivo, cada permiso permite las siguientes acciones:
- el permiso de lectura (**r**) permite al dueño examinar el contenido del archivo;
- el permiso de escritura (**w**) permite al dueño modificar el archivo;
- el permiso de ejecución (**x**) permite al dueño ejecutar el archivo como una orden.

Para los directorios, cada permiso permite las siguientes acciones:
- el permiso de lectura (**r**) permite al dueño obtener una relación del contenido del directorio;
- el permiso de escritura (**w**) permite al dueño añadir o borrar archivos al directorio;
- el permiso de ejecución (**x**) permite al dueño acceder a los archivos del directorio.

El permiso de ejecución de un directorio no solo indican que se puede leer los archivos que contiene, sí no también permite ver sus atributos, como el tamaño y la fecha de modificación.

El comando **ls** se usa para mostrar los permisos (y más detalles) de archivos o directorios. Cuando se ejecuta con el parámetro «-l», muestra la información siguiente ordenada por campos:

- tipo de fichero (primer carácter: -, d, l, etc.),
- permisos del archivo (nueve caracteres, tres para el usuario, tres para el grupo y los tres últimos para el resto, en este orden),
- número de enlaces duros al archivo,
- nombre del usuario que es dueño del archivo,
- nombre del grupo al que pertenece,
- tamaño del archivo expresado en caracteres (bytes),
- fecha y hora del archivo (mtime),
- nombre del archivo.

Para cambiar el dueño de un archivo, el superusuario utiliza la orden **chown**. Para alterar el grupo de un archivo, su dueño utiliza la orden **chgrp**. Para modificar los permisos del acceso al archivo o directorio, su dueño o el superusuario utilizan la orden chmod**. La sintaxis para operar sobre un archivo _foo_ es la que se muestra.

```bash
# chown <nuevo_dueño> foo
# chgrp <nuevo_grupo> foo
# chmod  [ugoa][+-=][rwxXst][,...] foo
```

Por ejemplo, se puede asignar a un árbol de directorios como dueño al usuario _foo_ y como grupo _bar_ como se muestra.
```bash
# cd /ruta/a/un/lugar/
# chown -R foo:bar .
# chmod -R ug+rwX,o=rX .
```
Nota bene: en estos ejemplos, el símbolo # significa que están utilizando el terminal como superusuario (**root**) del sistema. En práctica, es una mala práctica trabajar siempre desde este usuario.

#### 2.2 La cuenta de superusuario (root) y el comando sudo

La cuenta de root también es conocida como superusuario o usuario privilegiado. Con esta cuenta podrá llevar a cabo las siguientes tareas administrativas:

- leer, escribir y borrar cualquier archivo del sistema independientemente de los permisos de dicho archivo;

- cambiar la propiedad y los permisos de cualquier archivo del sistema;

- cambiar la contraseña de cualquier usuario sin privilegios del sistema;

- entrar en la cuenta de cualquier usuario sin usar su contraseña.

El poder ilimitado de la cuenta de superusuario necesita de un uso basado en la consideración y la responsabilidad.

El comando **sudo** permite ejecutar un comando con los derechos del superusuario. Por ejemplo:

```bash
$ sudo chown <nuevo_dueño> foo
```

#### 2.3 Crear usuarios

Los sistemas GNU/Linux son multi-usuarios, es decir que pueden ser utilizados por varios usuarios y que ellos pueden tener derechos distintos.

1. el comando **adduser [nombre_del_usuario]** permite crear un usuario.
1. el comando **passwd [nombre_del_usuario]** permite dar un password al usuario.
1. el comando **userdel [nombre_del_usuario]** permite suprimir un usuario.
1. los comandos **addgroup** y **groupdel** son similares para crear y suprimir grupos.
1. Para listar los usuarios y grupos del sistema, se puede mostrar el contenido de los archivos `/etc/passwd` (usuarios) y `/etc/group` (grupos)
1. Para añadir o suprimir un usuario a un grupo, se utiliza el comando **gpasswd**. Ejemplo: `gpasswd -a aUser aGroup`

#### 2.4 Ejercicio

1. Crear un usuario llamado `juan` y darle como password `juan2019`.
1. En su carpeta de trabajo 'INFO133', crear un archivo llamado `test.txt` que el usuario `juan` podrá leer pero no modificar.
1. Logearse al sistema como `juan` con el comando `su juan` y tratar de leer el archivo con el comando **cat**.
1. Crear un grupo llamado `amigos` y añadir `juan` y su usuario habitual en este grupo.
1. Cambiar el grupo dueño del archivo `test.txt` con el comando **chgrp** para que los miembros del grupos pueden leer y modificar el archivo.
1. Logearse al sistema como `juan` con el comando `su juan` y tratar de leer el archivo con el comando **cat**.


### 3. Algunos otros comandos útiles y script BASH

#### 3.1 Algunos comandos útiles

1. El comando **wget** permite descargar un recurso disponible a través de la Web. Ejemplo: `wget http://www.uach.cl`
1. El comando **egrep** permite buscar ciertos patrones en el contenido de un archivo, utilizando expresiones regulares. Ejemplo: `egrep -o "(http(s)?://){1}[^'\"]+" index.html` busca las direcciones en un documento HTML
1. El símbolo > ("superior") permite redireccionar la salida de un comando para escribir en un archivo. Ejemplo `cat index.html > mi_archivo` creará un archivo mi_archivo con el output del comando anterior.
1. El símbolo | ("pipe" en inglés) permite combinar varios comandos para que la salida de un primer comando sea la entrada de otro comando. Por ejemplo: `cat mi_archivo | egrep -o "(http(s)?://){1}[^'\"]+"`

#### 3.2 Script BASH

En cualquier sistema GNU/Linux, se puede combinar comandos BASH en un script. Es muy como para automatizar ciertas tareas.

Veamos un primer ejemplo "hello world":

```
#!/bin/bash
# Este es nuestro primer progrma
echo "Hola Mundo"
```

### 4. Gestion de paquetes e instalación de nuevos programas

<por completar>



