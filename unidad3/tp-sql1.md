## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Introducción al lenguaje SQL

### 1. ¿Qué es SQL?

SQL es un lenguaje para operar bases de datos; incluye creación de bases de datos, manipulación de filas, modificación de filas, etc. SQL es un lenguaje estándar ANSI (American National Standards Institute), pero hay muchas versiones diferentes del lenguaje SQL. La primera encarnación de SQL apareció en 1974, cuando un grupo de IBM desarrolló el primer prototipo de una base de datos relacional. Relational Software (luego se convirtió en Oracle) lanzó la primera base de datos relacional comercial. 

En la actualidad, se utilizan principalmente 4 SGBDs relacionales: Oracle, MySQL, Microsoft SQL Server, PostgreSQL (fuente: [[db-engines.com]](https://db-engines.com/en/ranking)). Cada uno de estos productos proveen una implementación del lenguaje SQL. Aunque compartan mismos estándares, existen algunas pequeñas diferencias en el SQL de cada producto.

En nuestros trabajos prácticos, trabajaremos con el producto MySQL, desarrollado por Oracle bajo licencia open-source [[GPL 2]](https://es.wikipedia.org/wiki/GNU_General_Public_License).

El SQL es muy popular porque ofrece las siguientes ventajas. Permite:
- acceder a los datos de los sistemas de gestión de bases de datos relacionales.
- definir los datos en una base de datos y manipularlos.
- integrarse con otros lenguajes de programación.
- definir vistas, procedimientos almacenados y funciones que facilitan la gestión de la base de datos.
- definir usuarios y privilegios de acceso sobre tablas, vistas y procedimientos.

### 2. Comandos SQL

El lenguaje SQL consiste en una serie de comandos que podemos ordenar en 3 grupos:

1. Los comandos que sirven para definir y modificar las tablas:
2.
3.



### 3. Primeros pasos con las herramientas de MySQL

#### 3.1 El servidor (__mysqld__), el cliente por linea de comando (__mysql__) y el cliente gráfico (__mysql-workbench__)

El producto MySQL viene con una serie de softwares, entre los cuales podemos destacar 3 principales:
- **mysqld**: es el servicio principal del SGBD que escucha en continua, recibe y procesa las consultas.
- **mysql**: es un cliente de tipo CLI (Command Line Interface), es decir un software que permite interacturar con el SGBD a través de comandos en un terminal.
- **mysql-workbench**: es un cliente de tipo GUI (Graphical User Interface), un software que permite interactuar con el SGBD a través de una interfaz gráfica.

En un terminal, el comando siguiente permite ver si el servicio principal de MySQL está ejecutándose:

> ps -aux | grep mysqld

Si __mysqld__ está funcionando, podemos abrir un cliente. Empezaremos con el CLI __mysql__, conectandonos como el usuario __root__:

> mysql -u root -p

Si se conectaron exitosamente, deberián ver que el prompt de su terminal indica ahora **mysql>**


### 3.2 Comandos útiles con el CLI __mysql__

1. **show databases;**: permite listar las bases de datos actualmente disponibles en el SGBD.
1. **help**: permite ver los comandos específicos del cliente. No son comandos del lenguaje SQL.
1. **use**: permite indicar al SGBD con qué base de datos queremos trabajar.
1. **source**: permite ejecutar una serie de instrucciones SQL a través de un archivo.
1. **exit**: permite salir del cliente.


### 4. Creación de una Base de Datos ejemplo




### 5. Consultas de lectura y escritura simple




