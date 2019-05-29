## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Lenguaje SQL

### 1. Instalar la Base de Datos de prueba

En este TP, trabajaremos con una base de datos llamada _sakila_. 
 
Pueden instalar la Base de Datos a través del comando <code>SOURCE</code> y dos archivos .sql que contienen instrucciones para instalar el [esquema de la base de datos](sakila-schema.sql) y los [datos](sakila-data.sql). 

Pueden encontrar una visualización del modelo relacional de la base [aqui](sakila_modelo.png)

### 2. Consultas

1. Mostrar el 'firstname' y 'lastname' de los clientes activos
 (_active_).
1. Contar el número de clientes activos por paises
1. Mostrar los paises dónde hay al menos 10 clientes activos, ordenados del número más grande al más pequeño.
1. Mostrar los titulos y descripción de peliculas que contienen la palabra "dog" en du descripción.
1. Mostrar los titulos y descripción de peliculas que más fueron arrendadas, ordenadas de del número más grande al más pequeño.
1. Mostrar las peliculas que nunca fueron arrendadas entre dos fechas.
1. Mostrar el volumen de negocio (ver tabla Payment) asociado a cada pelicula entre dos fechas, ordenado del volumen de negocio más grande al más pequeño.
1. Mostrar título de la pelicula que generó más volumen de negocio.
1. Mostrar los títulos de pelicula que generaron más de cierto valor de volumen de negocio.
1. Contar cuántos Staff distintos han arrendados la pelicula que generó más volumen de negocio.
1. Mostrar la pelicula más arrendada (titulo) por un Staff particular.
1. Mostrar la pelicula más arrendada (titulo) por cada uno de los miembros del Staff.
1. Mostrar la evolución del volumen de negocio mensual de una tienda dada
1. ¿Cuáles son los actores que más generan volumen de negocio?
1. ¿Cuáles son los actores que jugaron más en pelicula de tipo "Sci-Fi"?
1. ¿Cuáles son los actores que nunca jugaron en pelicula de tipo "Sci-Fi"?
1. ¿Cuáles son los actores que jugaron en peliculas con 'Russell Close'?
1. Contar el número de peliculas promedio por actores
1. Mostrar la pelicula más larga (_length_)
1. Mostrar las tres categorias de pelicula favoritas de un cliente dado
1. Mostrar la categoría de pelicula favorita de cada cliente (firstname y lastname).
1. Mostrar cuál categoría de pelicula no es la favorita de nadie.
1. Mostrar cuál categoría genera al menos 3 arriendos por semana en promedio.


