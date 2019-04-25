## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

### 1. Preguntas (1.5 puntos / ~15 minutos)

1. ¿Qué problemas tratan de resolver los SGBDs relacionales en comparación con otros sistemas de almacenamiento de datos? 

1. ¿Cuáles son los 3 conceptos pilares de los SGBDs relacionales? Describir muy brevemente en qué consisten (1 frase por cada concepto).

1. ¿Qué limitaciones de los SGBDs relacionales aparecieron con el crecimiento de las aplicaciones Web, a partir de los años 2000?


### 2. Modelamiento Entidad-Relación (2 puntos / ~20 minutos)

Una cadena de restaurantes ha relevado información acerca de los clientes y sus preferencias. De cada persona, identificada por su cédula de identidad, se conoce su nombre, los restaurantes que frecuentan más, las comidas que consuma, en qué fechas y qué precio pagó por cada comida.

De cada restaurante, identificado por su nombre, se conoce las comidas que preparan. De cada comida se conoce su nombre, que la identifica, el tiempo de preparación y los ingredientes principales. Varios restaurantes pueden preparar la misma comida.

**Ejercicio:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

### 2. Modelamiento Relacional (0.5 punto / ~10 minutos)

**Ejercicio:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales.
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL (2 puntos / ~30 minutos)

Escribir las consultas SQL que corresponden a los casos siguientes:

1. Mostrar el volumen de negocio realizado agrupado por clientes, mostrando los clientes en orden descendente.
1. Mostrar las comidas que contienen "leche" como ingrediente.
1. Mostrar qué día de la semana se realizó más volumen de negocio en 2018.
1. Mostrar las comidas que nunca se pidieron entre dos fechas.
1. Mostrar los restaurantes que realizaron al menos 10MM$ de volumen de negocio en 2018.



