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

1. Los comandos que sirven para definir la estructura de las tablas de un base de datos: **CREATE**:  **ALTER**, **DROP**
2. Los comandos que sirven para manipular los datos (leer o escribir): **SELECT**, **INSERT**, **UPDATE**, **DELETE**
3. Los comandos que sirven para gestionar los derechos/privilegios de uso: **GRANT**, **REVOKE**

Para una presentación exhaustiva de los comandos del lenguaje SQL, se recomienda la [[documentación]](https://www.w3schools.com/SQl/sql_syntax.asp) de w3schools.com por ejemplo.

A continuación presentaremos ejemplos de uso de estos comandos.

### 3. SGBD-Relacional (o _RDBMS__: Relacional DataBase Management System)

Un sistema de gestión de base de datos relacional, es un software basado 1) en el modelo relacional presentado por Edgar Codd, 2) en el lenguaje de consultas SQL, 3) en el uso de transacciones ACID (que conversaremos en otra clase).

Los conceptos centrales de los SGBD-R son: las **tablas**, las **tuplas** (filas) y las **claves primarias** y **foraneas**.

Además, los SGBD-R siguen [[reglas de normalización]](https://es.wikipedia.org/wiki/Normalizaci%C3%B3n_de_bases_de_datos) que apuntan a organizar de manera eficientes los datos. En particular:
- eliminar la redundancia (el hecho de almacenar la misma información en distintas partes),
- asegurar la relevancia de las dependencias entre datos

### 4. Primeros pasos con las herramientas de MySQL

#### 4.1 El servidor (__mysqld__), el cliente por linea de comando (__mysql__) y el cliente gráfico (__mysql-workbench__)

El producto MySQL viene con una serie de softwares, entre los cuales podemos destacar 3 principales:
- **mysqld**: es el servicio principal del SGBD que escucha en continua, recibe y procesa las consultas.
- **mysql**: es un cliente de tipo CLI (Command Line Interface), es decir un software que permite interacturar con el SGBD a través de comandos en un terminal.
- **mysql-workbench**: es un cliente de tipo GUI (Graphical User Interface), un software que permite interactuar con el SGBD a través de una interfaz gráfica.

En un terminal, el comando siguiente permite ver si el servicio principal de MySQL está ejecutándose:

> ps -aux | grep mysqld

Si __mysqld__ está funcionando, podemos abrir un cliente. Empezaremos con el CLI __mysql__, conectandonos como el usuario __root__:

> mysql -u root -p

Si se conectaron exitosamente, deberián ver que el prompt de su terminal indica ahora **mysql>**


### 4.2 Comandos útiles con el CLI __mysql__

1. **show databases;**: permite listar las bases de datos actualmente disponibles en el SGBD.
1. **help**: permite ver los comandos específicos del cliente. No son comandos del lenguaje SQL.
1. **use**: permite indicar al SGBD con qué base de datos queremos trabajar.
1. **source**: permite ejecutar una serie de instrucciones SQL a través de un archivo.
1. **exit**: permite salir del cliente.

### 5. Creación de una Base de Datos ejemplo: __Escuela de Informática__

A continuación crearemos una base de datos básica que representa las relaciones entre las entidades de tipo Estudiante y Asignatura.

La instrucción SQL **CREATE DATABASE** se utiliza para crear una nueva base de datos SQL.

> CREATE DATABASE escuela;

Una vez creada la base de datos, puede verificar que aparece en la lista de bases de datos existentes en el SGBD.

> SHOW DATABASES;

Y finalmente conectarse a la base con:

> USE escuela;

Para suprimir una base de datos existente, se utiliza el comando **DROP DATABASE**. Por ejemplo:

> CREATE DATABASE test;

> DROP DATABASE test;


#### 5.1 Creación del esquema de la base de datos

La creación de una tabla básica implica nombrar la tabla y definir sus columnas y el tipo de datos de cada columna.

La instrucción SQL **CREATE TABLE** se utiliza para crear una nueva tabla. Por ejemplo:

``
CREATE TABLE ESTUDIANTE(
ID INT NOT NULL, 
NOMBRE VARCHAR (20) NOT NULL, ANO_INGRESO  INT NOT NULL,
PRIMARY KEY (ID)
);
``



#### 5.2 Llenar las tablas con datos de ejemplo


### 6. Consultas de lectura y escritura simple




