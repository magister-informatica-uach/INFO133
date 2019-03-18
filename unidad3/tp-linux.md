## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Introducción al sistema operativo GNU/Linux

Como todos los sistemas operativos derivados de Unix, GNU/Linux dispone de un intérprete de comandos o terminal (en inglés se utiliza la palabra shell) que hace de interfaz entre el usuario y el propio sistema operativo y cuyo nombre es BASH.

> Desde Ubuntu, abrir un terminal BASH con CTRL-Alt-T

### 1. Sistema de archivos GNU/Linux

En GNU/Linux, todo es un archivo. Los archivos se organizan en directorios (los directorios son tipos particulares de archivos). Todos los archivos y directorios están ordenados en un gran árbol que tiene como raíz «/». 

- Cada directorio tiene un nombre que puede contener cualquier letra o símbolo excepto «/». El directorio raíz es una excepción: su nombre es «/» (pronunciado «barra« o «el directorio raíz«) y no puede ser renombrado. 

- Cada archivo o directorio es identificado con una **ruta** única. 

- El directorio raíz tiene un cierto número de ramificaciones, como «/etc/» y «/usr/». Estos subdirectorios a su vez se ramifican en más subdirectorios, como «/etc/init.d/» y «/usr/local/». El todo, visto colectivamente, es llamado el árbol de directorios.

	- **/etc/**: archivos principales para la configuración del sistema
	- **/var/log/**: archivos de registro del sistema
	- **/home/**: todos los archivos personales de los usuarios


#### 1.1 Comandos útiles para gestionar archivos

1. **cd /home**: entrar en el directorio "home"
1. **cd ..**: retroceder un nivel
1. **cd ../..**: retroceder dos niveles
1. **cd**: ir al directorio del usuario corriente
1. **pwd**: mostrar la ruta del directorio actual 
1. **ls**: ver los archivos del directorio
1. **ls -l**: mostrar los detalles de archivos y carpetas de un directorio
1. **ls -a**: mostrar los archivos ocultos
1. **mkdir INFO133**: crear una carpeta con mombre "INFO133" 





