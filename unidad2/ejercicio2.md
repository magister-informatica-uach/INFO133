## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

### 1. Modelamiento Entidad-Relación

La empresa de transporte TURIBUS quiere iniciar una campaña de viajes turísticos aprovechando el periodo estival. Para ello selecciona las rutas turísticas que considera más atractivas, y decide ofertar durante todo el periodo de la campaña un servicio diario regular por dichas rutas. Es decir, cada uno de estos servicios diarios realiza el recorrido de una ruta con el mismo horario todos los días en
que está programado (algunos sólo funcionan en días festivos). Evidentemente, algunas rutas con mayor demanda tienen varios servicios diarios. En los folletos editados figura la lista de servicios diarios
ofertados (hora y ruta), junto con la descripción de los días en que están programados.

Cada pasajero que contrata un viaje recibe un billete en el que figuran el nombre de la ruta, la fecha y hora de salida, el importe (fijo para cada ruta), y la hora de llegada prevista. También recibe un listado que describe, por orden cronológico, los lugares más relevantes del recorrido. La descripción consiste en el nombre del lugar, la hora prevista de llegada (el tiempo entre dos lugares concretos es fijo para cada ruta) y además, en algunos casos, la actividad a realizar (comida, visita, etc.) y el tiempo de parada previsto. En el momento de la compra, y únicamente para efectos promocionales (sorteos, etc.), el viajero debe comunicar su RUT, apellidos-nombre y teléfono al empleado de la empresa.

Para cada uno de los viajes, la empresa asigna un autobús y un conductor concreto. Con objeto de simplificar la gestión, esta asignación se realiza para cada uno de los servicios diarios. Es decir, cada
conductor realiza todos los días los mismos recorridos y, en cada uno de ellos, conduce el mismo autobús (depende sólo de la ruta y la hora). De cada autobús, identificado por su matrícula, se tiene información del modelo, fabricante, número de plazas y un texto con sus características básicas. De los conductores, su RUT, apellidos-nombre, teléfono, y dirección.
La normativa de seguridad exige guardar la información de las revisiones efectuadas a cada vehículo: fecha de revisión, diagnóstico (un simple comentario) y, si procede, la lista de reparaciones
efectuadas en dicha revisión (código del tipo de reparación, tiempo empleado y, a veces, un pequeño comentario).

Con el fin de mejorar la calidad del servicio, la compañía desea poder conocer en cada momento la media de viajeros de cada ruta y de cada servicio diario, así como los km. diarios realizados por cada
autobús y cada conductor. Además, para premiar a los mejores usuarios, también desea conocer el total de horas de viaje realizados por cada usuario.

**Ejercicio:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

### 2. Modelamiento Relacional

**Ejercicio:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales (ver: https://es.wikipedia.org/wiki/Forma_normal_(base_de_datos)).
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL

Proponer escenarios de consulta sobre la base de datos obtenida:
1. 2 consultas necesitarán el uso del operador INNER JOIN
1. 1 consulta necesitará el uso del operador LEFT OUTER JOIN
1. 2 consultas necesitarán el uso del operador GROUP BY
1. 1 consulta necesitará el uso del operador HAVING
1. 2 consultas necesitarán el uso de una subconsulta
1. 1 consulta combinará una subconsulta con el uso de un operador GROUP BY

----------------------

### 1. Modelamiento Entidad-Relación

Una guardería desea controlar los gastos que cada uno de los niños realiza a través de su asistencia y de las comidas que consume.
De cada niño se desea conocer los datos propios de su matrícula en el centro educativo, es decir, el número de matrícula, el nombre, la fecha de nacimiento y la fecha de ingreso en la guardería. Para aquellos niños que se hayan dado de baja, también se desea conocer la fecha de la baja.

Los niños sólo pueden ser recogidos en la guardería por un conjunto de personas que suelen ser un familiar del niño o un conocido de sus familiares De éstos se desea conocer el DNI, el nombre, la dirección y al menos un número de teléfono de contacto. Además, debe de quedar constancia de cuál es la relación entre la persona autorizada y el niño.
El coste mensual del niño en la guardería es abonado por una persona, de la que se desea conocer el DNI, el nombre, la dirección, el teléfono, y el número de la cuenta corriente en la que se realizará el cargo.
Estas personas también pueden estar autorizadas para recoger al niño. En la guardería aparece un conjunto de menús, compuesto por una serie de platos concretos, cada uno de los cuales presentan unos ingredientes determinados. Cada menú se identifica por un número, mientras que los platos y los ingredientes se caracterizan por su nombre. Un niño puede ser alérgico a diferentes
ingredientes, y por tanto no puede consumir los platos en los que aparece este ingrediente. Estas alergias deben de ser controladas para evitar posibles intoxicaciones en los niños. El cargo mensual de un niño se calcula como la suma de un coste fijo mensual y el coste de las comidas realizadas. Este último se obtiene a partir del número de días que el niño ha comido en la guardería, por lo que resulta necesario controlar dicho número. Además, se desea saber el menú que ha consumido cada niño cada día.

**Ejercicio:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

### 2. Modelamiento Relacional

**Ejercicio:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales (ver: https://es.wikipedia.org/wiki/Forma_normal_(base_de_datos)).
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL

Proponer escenarios de consulta sobre la base de datos obtenida:
1. 2 consultas necesitarán el uso del operador INNER JOIN
1. 1 consulta necesitará el uso del operador LEFT OUTER JOIN
1. 2 consultas necesitarán el uso del operador GROUP BY
1. 1 consulta necesitará el uso del operador HAVING
1. 2 consultas necesitarán el uso de una subconsulta
1. 1 consulta combinará una subconsulta con el uso de un operador GROUP BY

----------------------

### 1. Modelamiento Entidad-Relación

Un parque zoológico quiere construir una BD para organizar las especies que posee y los distintos itinerarios para visitar el parque. La información se estructura de la siguiente forma. De las especies, se desea conocer su nombre común y su nombre científico, así como una descripción general y una fotografía. Cada especie puede vivir en distintos hábitats naturales, definidos por su nombre, clima y vegetación predominante. Cada especie tiene asociado un índice de vulnerabilidad dentro de cada hábitat, que mide el riesgo de extinción de la especie en el dicho hábitat. Para organizar las visitas, y en función de los hábitats que desee recorrer un visitante, el parque le ofrece una serie de recorridos por los hábitats, que se identifican por su código y se caracterizan por su duración estimada, longitud y número máximo de visitantes permitidos. Un hábitat sólo puede formar parte de un itinerario.

**Ejercicio:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

### 2. Modelamiento Relacional

**Ejercicio:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales (ver: https://es.wikipedia.org/wiki/Forma_normal_(base_de_datos)).
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL

Proponer escenarios de consulta sobre la base de datos obtenida:
1. 2 consultas necesitarán el uso del operador INNER JOIN
1. 1 consulta necesitará el uso del operador LEFT OUTER JOIN
1. 2 consultas necesitarán el uso del operador GROUP BY
1. 1 consulta necesitará el uso del operador HAVING
1. 2 consultas necesitarán el uso de una subconsulta
1. 1 consulta combinará una subconsulta con el uso de un operador GROUP BY

----------------------

### 1. Modelamiento Entidad-Relación

Una organización no gubernamental se encarga de enviar ayuda material (medicamentos y alimentos) y ayuda humanitaria (personal sanitario) a campos de refugiados. Esta organización obtiene sus ingresos de
las cuotas de los socios, de los que se desea conocer los datos personales, la cuenta bancaria en donde se realizan los cargos anuales, la fecha de pago y el tipo de cuota. En la actualidad hay tres tipos de cuotas, pudiendo variar en el futuro: mínima (10 euros anuales), media (20 euros anuales) o máxima (30 euros anuales).

Cada socio pertenece a una de las sedes de la organización, cada una de ellas ubicada en una ciudad distinta. De las sedes se desea conocer el domicilio y el nombre de su director.
La organización cuenta con dos tipos de voluntarios: los que realizan labores humanitarias (personal sanitario) y los que realizan labores administrativas (personal administrativo). De los primeros se desea conocer su profesión (médico, ATS, etc.), su disponibilidad actual (sí/no) y el número de trabajos en los que ha participado. De todos los voluntarios se desea conocer los datos personales y la sede en la que se inscribieron.

Cada envío tiene un destino y una fecha de salida. Para identificar los envíos, se les asigna un código único. Además, cada envío es organizado por una o varias sedes. Los envíos de ayuda material pueden ser de alimentos, debiéndose conocer el número de toneladas de cada alimento que se manda; o pueden ser de medicamentos, debiéndose conocer el número de unidades de cada medicamento. De los envíos de ayuda
humanitaria se debe conocer el número de voluntarios que se mandan de cada profesión (por ejemplo: 10 médicos, 20 ATS) y quienes son cada uno de ellos.

**Ejercicio:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

### 2. Modelamiento Relacional

**Ejercicio:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales (ver: https://es.wikipedia.org/wiki/Forma_normal_(base_de_datos)).
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL

Proponer escenarios de consulta sobre la base de datos obtenida:
1. 2 consultas necesitarán el uso del operador INNER JOIN
1. 1 consulta necesitará el uso del operador LEFT OUTER JOIN
1. 2 consultas necesitarán el uso del operador GROUP BY
1. 1 consulta necesitará el uso del operador HAVING
1. 2 consultas necesitarán el uso de una subconsulta
1. 1 consulta combinará una subconsulta con el uso de un operador GROUP BY
