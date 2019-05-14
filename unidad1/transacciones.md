## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Transacciones y Propiedades ACID

Este TP se centra sobre el concepto de Transacción en los SGBD relacionales y sus propiedades ACID. Las Transacciones son uno de los 3 conceptos pilares de todos los SGBD relacionales (el modelo relacional y el lenguaje SQL son los 2 otros conceptos pilares).

Para ilustrar el concepto de Transacción trabajaremos con una instancia de MySQL que se encuentra en un servidor remoto.

Se puede configurar MySQL para que usuarios remotos puedan conectarse a través de una red. En nuestro caso, utilizaremos una instancia de MySQL que se encuentra en un computador de la red local de la UACh con la dirección IP local siguiente: <code>146.83.216.219</code>

Desde un terminal, se puede acceder al MySQL remoto con el comando siguiente:
<code>mysql -h 146.83.216.219 -P 3001 -u _username_ -p</code>

__-h__: IP de la máquina que aloja MySQL
__-P__: puerto que utiliza MySQL para comunicar con programas externos
__-u__: usuario autorizado
__-p__: password del usuario


###. Caso de estudio: Creación de una moneda alternativa por los estudiantes de Informática de la UACh

Supongamos que los estudiantes de Informática-UACh deciden crear su propia moneda: el _Pudu_.
Esta moneda sirve para facilitar pequeñas transacciones entre los miembros de la comunidad "Pudu", dentro del campus Miraflores.

Por el momento, el volumen de __Pudu__ en circulación no puede variar, está fijado en 5.000 PUDU.

Al momento de su creación, 1 PUDU era igual a 1.000 pesos. 5 estudiantes decidieron ser parte de esta comunidad comprando cada uno 100 PUDU.

<code> USE pudu;</code>

<code> SELECT * FROM cuentas;</code>


### ¿Qué es una transacción A.C.I.D?

Supongamos ahora que algunos estudiantes quieren empezar a utilizar sus PUDU:
- el estudiante 1 quiere transferir 2 PUDU al estudiante 2 para reembolsar la compra de un sandwich.
- el estudiante 3 quiere transferir 50 PUDU al estudiante 4 quien lo ayudó en un proyecto.
- el estudiante 3 quiere transferir 75 PUDU al estudiante 5 quien lo ayudó en un proyecto.

Cada transferencia corresponde a una transacción distinta.

Cada transacción implica al menos 2 operaciones:
- actualizar la cuenta del estudiante que envia los PUDU
- actualizar la cuenta del estudiante que recibe los PUDU

__Atomicidad__ (A): Una transacción se realiza completamente o no se realiza.

<code>START TRANSACTION;</code>

<code>UPDATE cuentas SET valor=valor-2 WHERE ID=1;</code>

<code>UPDATE cuentas SET valor=valor+2 WHERE ID=2;</code>

<code>commit;</code>

---

<code>START TRANSACTION;</code>

<code>UPDATE cuentas SET valor=valor-2 WHERE ID=1;</code>

<code>UPDATE cuentas SET valor=valor+2 WHERE ID=2;</code>

<code>rollback;</code>

__aIslamiento__ (I): Una transacción se realiza completamente aislada de otras transacciones.

<code>START TRANSACTION;</code>

<code>UPDATE cuentas SET valor=valor-50 WHERE ID=3;</code>

<code>UPDATE cuentas SET valor=valor+50 WHERE ID=4;</code>

<code>commit;</code>

----

<code>START TRANSACTION;</code>

<code>UPDATE cuentas SET valor=valor-75 WHERE ID=3;</code>

<code>UPDATE cuentas SET valor=valor+75 WHERE ID=5;</code>

<code>commit;</code>

__Consistencia__ (C): Una transacción debe respetar las restricciones establecidas, sino se anula la transacción. Se terminan las transacciones que no van a romper las reglas y directrices de Integridad de la base de datos. La propiedad de consistencia sostiene que cualquier transacción llevará a la base de datos desde un estado válido a otro también válido.

Ver lista de restricciones en MySQL: https://www.w3resource.com/mysql/creating-table-advance/constraint.php

MySQL no soporta totalmente la restricción CHECK: http://www.mysqltutorial.org/mysql-check-constraint/

Sin embargo se puede simular la restricción CHECK que necesitamos utilizando el concepto de __Procedura almacenada__ y __Trigger__.


Procedura: check_cuentas
~~~~
DELIMITER $

CREATE PROCEDURE `check_cuentas`(IN valor INT)
BEGIN
    IF valor < 0 THEN
        SIGNAL SQLSTATE '45000'
           SET MESSAGE_TEXT = 'cuenta con valor negativo';
    END IF;
END$
DELIMITER ;
~~~~

Trigger: comandos que se activan solos cuando pasa cierto evento. Por ejemplo cuando se insert o actualiza cierta tabla.

~~~~
-- before insert
DELIMITER $
CREATE TRIGGER `cuentas_before_insert` BEFORE INSERT ON `cuentas`
FOR EACH ROW
BEGIN
    CALL check_cuentas(new.valor);
END$
DELIMITER ; 
-- before update
DELIMITER $
CREATE TRIGGER `cuentas_before_update` BEFORE UPDATE ON `cuentas`
FOR EACH ROW
BEGIN
    CALL check_cuentas(new.valor);
END$
DELIMITER ;
~~~~

__DURABILIDAD__ (C): Cuando una transacción fue confirmada por "commit", el sistema asegura que el resultado de la transacción está registrado.

Prueba con 'Exit'.


### Ejercicio
1. Agregar una restricción que permite asegurarse que hay siempre 5.000 PUDU en el sistema.
1. Agregar una restricción que permite evitar transacciones de más de 50 PUDU.






