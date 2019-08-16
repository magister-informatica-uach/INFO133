## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

### 1. Preguntas (1.5 puntos / ~20 minutos)

1. ¿Cuáles son las ventajas/desventajas de los 3 sistemas siguientes para almacenar datos?

|  | Sistema de Archivos | Base de datos relacional  | Base de datos no relacional |
|---|---|---|---|
| ventajas |   |   |   |
| desventajas |   |   |   |

2. ¿Qué sistema recomendarian utilizar para almacenar los datos de un sistema de reserva de asientos de autobús? ¿Por qué?


### 2. Modelamiento Entidad-Relación y transformación al modelo relacional (2.5 puntos / ~30 minutos)

El Servicio de Salud de Valdivia desarrolla una aplicación de teledermatología que permite poner en relación medicos generalistas y pacientes de la región de Los Riós con medicos especializados en dermatología ubicados en Valdivia. La aplicación es particularmente útil para médicos y pacientes de zona rural.

De los médicos generalistas, necesitamos conocer su nombre y apellido, su RUT, el año de obtención de su diploma, las ciudades/pueblos en los cuales han trabajado y sus periodos de trabajo. 

A través de la aplicación, los medicos generalistas tienen la posibilidad de enviar mensajes a dermatologos a proposito de un paciente que tiene problema dermatologíco. Los pacientes tienen un medico generalista de referencia. De los pacientes, se necesita conocer el nombre, apellido, RUT y edad.

Los mensajes tienen una fecha, un texto que describe el caso y está acompañado por una o varias fotos para ilustrar. Uno o varios dermatologos pueden responder al mensaje dejando un comentario y un diagnóstico. El diagnóstico está asociado a un nivel de peligro entre 1 y 5. En caso de tener un nivel de peligro mayor a 3, el paciente puede fijar una fecha de primera cita con el dermatologo en Valdivia.

**Etapa A:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

**Etapa B:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales.
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL (2 puntos / ~30 minutos)

Escribir las consultas SQL que corresponden a los casos siguientes:

1. Mostrar cuántos médicos generalistas han obtenido su diploma despúes del año 2015.
1. Mostrar cuántos pacientes tienen cada uno de los médicos generalistas
1. Mostrar en qué pueblo el número promedio de pacientes por médico es el máximo
1. Mostrar qué dermatologo nunca ha respondido a al menos 1 mensaje a través de la aplicación
1. Proponer una consulta (descripción + SQL) que necesita el uso de las clausulas GROUP BY y HAVING 
1. Proponer una consulta (descripción + SQL) que se puede resolver con una subconsulta



