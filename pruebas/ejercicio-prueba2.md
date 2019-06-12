## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

### 1. Preguntas (1.5 puntos / ~20 minutos)

1. ¿Qué problemas tratan de resolver los SGBDs relacionales en comparación con el almacenamiento de datos en archivos? Responder de manera sintética indicando un máximo de 5 conceptos claves.

1. ¿Qué problemas tratan de resolver los SGBDs no relacionales, tipo Mongo, en comparación con SGBD relacionales? ¿Cuáles son sus principales limitaciones? Responder de manera sintética indicando un máximo de 5 conceptos claves.

1. Supongamos que una colección Mongo contiene datos estructurados con el modelo de datos JSON siguiente:

```json
{
    "nombre":"Juan",
    "edad": 20,
    "carrera": {
        "nombre": "informática",
        "campus": "miraflores"
    },
    "posts_en_slack": [
        {texto:"Hoy a las 20:30 luego del workshop informática vs contru b , esperamos su apoyo ,gracias.", fecha:2019-05-01},
        {texto:"que paso con el paro?", fecha:2019-04-25},
        {texto:"alguna info ? resolucion o algo  ?", fecha:2019-04-20}
    ]
}
```

- ¿Cómo podriamos transformar este modelo de datos para tener un modelo de datos en tercera forma normal?


### 2. Modelamiento Entidad-Relación y transformación al modelo relacional (2.5 puntos / ~30 minutos)

Una organización no gubernamental se encarga de enviar ayuda material (medicamentos y alimentos) y ayuda humanitaria (personal sanitario) a campos de refugiados. Esta organización obtiene sus ingresos de
las cuotas de los socios, de los que se desea conocer los datos personales, la cuenta bancaria en donde se realizan los cargos anuales, la fecha de pago y el tipo de cuota. En la actualidad hay tres tipos de cuotas, pudiendo variar en el futuro: mínima (10 euros anuales), media (20 euros anuales) o máxima (30 euros anuales).

Cada socio pertenece a una de las sedes de la organización, cada una de ellas ubicada en una ciudad distinta, y en un país. De las sedes se desea conocer el domicilio y el nombre de su director.
La organización cuenta con dos tipos de voluntarios: los que realizan labores humanitarias (personal sanitario) y los que realizan labores administrativas (personal administrativo). De los primeros se desea conocer su profesión (médico, ATS, etc.), su disponibilidad actual (sí/no) y el número de trabajos en los que ha participado. De todos los voluntarios se desea conocer los datos personales y la sede en la que se inscribieron.

Cada envío tiene un destino y una fecha de salida. Para identificar los envíos, se les asigna un código único. Además, cada envío es organizado por una o varias sedes. Los envíos de ayuda material pueden ser de alimentos, debiéndose conocer el número de toneladas de cada alimento que se manda; o pueden ser de medicamentos, debiéndose conocer el número de unidades de cada medicamento. De los envíos de ayuda
humanitaria se debe conocer el número de voluntarios que se mandan de cada profesión (por ejemplo: 10 médicos, 20 ATS) y quienes son cada uno de ellos.

**Etapa A:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

**Etapa B:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales.
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL (2 puntos / ~30 minutos)

Escribir las consultas SQL que corresponden a los casos siguientes:

1. Mostrar cuántas unidades de medicamento se envian __en promedio__ en cada envio.
1. Mostrar los voluntarios de tipo medicos que nunca fueron mandados durante un envio.
1. Mostrar la cantidad total de toneladas de alimentos enviados por cada sede en Chile, ordenada según la cantidad.
1. Mostrar los mejores socios, es decir los que han pagado un monto total superior al monto promedio por socio.
1. Proponer una consulta SQL que contiene una subconsulta, describiendo lo que hace.
1. Proponer una consulta que utiliza las clausulas GROUP BY y HAVING, describiendo lo que hace. 




