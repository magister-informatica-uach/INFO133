## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Introducción al lenguaje SQL

SQL (Structured Query Language) es un lenguaje de programación diseñado para almacenar, manipular y recuperar datos almacenados en **bases de datos relacionales**. La primera encarnación de SQL apareció en 1974, cuando un grupo de IBM desarrolló el primer prototipo de una base de datos relacional. Relational Software (luego se convirtió en Oracle) lanzó la primera base de datos relacional comercial. 

En la actualidad, se utilizan principalmente 4 SGBDs relacionales: Oracle, MySQL, Microsoft SQL Server, PostgreSQL (fuente: [[db-engines.com]](https://db-engines.com/en/ranking)). Cada uno de estos productos proveen una implementación del lenguaje SQL. Aunque compartan mismos estándares, existen algunas pequeñas diferencias en el SQL de cada producto.

En nuestros trabajos prácticos, trabajaremos con el producto MySQL, desarrollado por Oracle bajo licencia open-source [[GPL 2]](https://es.wikipedia.org/wiki/GNU_General_Public_License).

### 1. Primeros pasos con las herramientas de MySQL

#### 1.1 El servidor (__mysqld__), el cliente por linea de comando (__mysql__) y el cliente gráfico (__mysql-workbench__)

El producto MySQL viene con una serie de softwares, entre los cuales podemos destacar 3 principales:
- **mysqld**: es el servicio principal del SGBD que escucha en continua, recibe y procesa las consultas.
- **mysql**: es un cliente de tipo CLI (Command Line Interface), es decir un software que permite interacturar con el SGBD a través de comandos en un terminal.
- **mysql-workbench**: es un cliente de tipo GUI (Graphical User Interface), un software que permite interactuar con el SGBD a través de una interfaz gráfica.

En un terminal, el comando siguiente permite ver si el servicio principal de MySQL está ejecutándose:

> ps -aux | grep mysqld

Si __mysqld__ está funcionando, podemos abrir un cliente. Empezaremos con el CLI __mysql__, conectandonos como el usuario __root__:

> mysql -u root -p



