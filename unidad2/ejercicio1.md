## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

### 1. Modelamiento Entidad-Relación

Un equipo de investigación desarrolló varios scripts capaces de recopilar informaciones sobre los distintos medios de prensa de varios paises de America Latina.

Por cada medio de prensa se conoce su nombre, el url de su sitio web en el cual publica noticias y una categoria que indica si se trata de medio nacional, regional o local. Cada medio lo posee uno o varios dueños identificados por un nombre. Los dueños pueden ser personas reales o personas jurídicas.

Cada medio puede poseer distintos canales sociales dónde publica regularmente enlaces hacia sus noticias. Un canal social está identificado por el id de la cuenta y el nombre de la red social (por ejemplo Facebook, Twitter, etc.). Cada canal social tiene una audiencia que corresponde al número de _followers_ que sigue este canal. El equipo de investigación indica que esta audiencia puede cambiar en el tiempo y que le interesa conservar la información histórica.

Los medios de prensa publican noticias que se caracterizan por un titulo, un texto, una fecha de publicación y opcionalmente una imagen de ilustración. El equipo de investigación considera que una noticia proviene de uno solo medio.

Finalmente, el equipo de investigación quiere poder contabilizar cuántas veces aparecen ciertas palabras en las noticias. Se desea distinguir las palabras simples (ej. "escuela", "proyecto", etc.) y las palabras compuestas ("tráfico de armas", "River Plate", etc.). También se desea representar la categoría gramatical de las palabras ("adjetivos", "sustantivos", etc.).


**Ejercicio:**

Representar los datos del caso a través de un modelo Entidad-Relación. Utilizarán símbolos utilizados en clase para describir las Entidades, Relaciones, atributos y cardinalidades. 
No indicarán las claves primarias y foraneas en su modelo. Su modelo no podrá incluir atributos multivaluados.

### 2. Modelamiento Relacional

**Ejercicio:**

A partir del modelo Entidad-Relación obtenido, realizar las transformaciones relevantes para obtener un modelo Relacional normalizado.

Se entenderá por Modelo Relacional normalizado, un modelo relacional que respeta al menos las 3 primeras formas normales.
Su Modelo Relacional deberá indicar explicitamente las claves primarias y foraneas. No es necesario especificar el tipo de datos asociado a cada atributo.

### 3. Consultas SQL

Escribir las consultas SQL que corresponden a los casos siguientes:

1. Mostrar el número de medios que poseen (totalmente o parcialmente) cada dueño, ordenado del dueño que posee más medios al dueño que posee menos medios.
2. Mostrar el número de noticias por medio entre dos fechas al formato YYYY-MM-DD, mostrando los 10 principales medios.
3. Mostrar la lista de adjetivos y sustantivos más utilizados en las noticias que utilizan la palabra "mujer", mostrando solamente los que aparecen al menos 50 veces.
4. Mostrar los medios que no utilizaron la palabra compuesta "justicia social" en sus noticias del mes pasado.
5. Mostrar el número de noticias promedio por día por cada medio.
6. Mostrar el dueño que más utiliza palabras simples o compuestas que contienen la palabra "libertad" en sus medios, mostrando los que no la utilizan al menos 10 veces.
7. Mostrar cómo evoluciona la frecuencia de aparición de la palabra "democracia" cada año.
