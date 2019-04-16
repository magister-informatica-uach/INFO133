## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Lenguaje SQL - Consultar, Ordenar, Filtrar, Agrupar

### 1. Instalar la Base de Datos de prueba

En este TP, trabajaremos con una base de datos llamada _classicmodels_. El Modelo Relacional de este base es el siguiente:

1. offices (**officeCode**, city, phone, addressLine1, addressLine2, state, country, postalCode, territory)
1. employees (**employeeNumber**, lastName, firstName, extension, email, jobTitle, #officeCode (offices), #reportsTo (employees))
1. customers (**customerNumber**, customerName, contactLastName, contactFirstName, phone, addressLine1, addressLine2, city, state, postalCode, country, creditLimit, #salesRepEmployeeNumber (employees))
1. payments (#**customerNumber** (customers), **checkNumber**, paymentDate, amount)
1. orders (**orderNumber**, orderDate, requiredDate, shippedDate, status, comments, #customerNumber (customers))
1. productLines (**productLine**, textDescription, htmlDescription, image)
1. products (**productCode**, productName, productScale, productVendor, productDescription, quantityInStock, buyPrice, MSRP, #productLine (productLines))
1. orderdetails (#**orderNumber** (orders), #**productCode** (products), quantityOrdered, priceEach, orderLineNumber)
 
Pueden descargar la Base de Datos [aquí](classicmodels.sql), instalandola en la carpeta _/unidad3_ de su carpeta de trabajo.

Desde el cliente MySQL, instalar la base de datos _classicmodels_ con el comando:

> source classicmodels.sql

Pueden verificar que la instalación se realizó correctamente con los comandos:

> use classicmodels;

> show tables;

> select * from customers;

### 2. SELECT vs. SELECT DISTINCT (para mostrar valores en ciertas columnas)

Ejemplos sin DISTINCT:

```
SELECT * 
FROM employees;
```

``` [sql]
SELECT lastname, firstname, jobtitle 
FROM employees;
```

```
SELECT lastname
FROM employees
ORDER BY lastname;
```

Ejemplos con DISTINCT:

```
SELECT DISTINCT lastname
FROM employees
ORDER BY lastname;
```

```
SELECT DISTINCT lastname, firstname
FROM employees
ORDER BY lastname;
```

** Ejercicios:**
1. Mostrar en qué ciudades viven los clientes.
1. Misma pregunta pero de evitando mostrar varias veces la misma ciudad.

### 3. ORDER BY (para ordenar los valores según una o varias columnas)

Ejemplos:

```
SELECT contactLastname, contactFirstname
FROM customers
ORDER BY contactLastname;
```

```
SELECT contactLastname, contactFirstname
FROM customers
ORDER BY contactLastname DESC;
```

```
SELECT contactLastname, contactFirstname
FROM customers
ORDER BY contactLastname DESC, contactFirstname ASC;
```

```
SELECT
 ordernumber,
 orderlinenumber,
 quantityOrdered * priceEach AS subtotal
FROM
 orderdetails
ORDER BY
 ordernumber,
 orderLineNumber,
 subtotal;
```

NB: Combinar las clausulas ORDER BY y LIMIT permite obtener los valores máximos y minimos

```
SELECT
 customernumber,
 customername,
 creditlimit
FROM
 customers
ORDER BY
 creditlimit DESC
LIMIT 5;
```


**Ejericios:**
1. Mostrar la lista de los productos ordenados por el stock disponible del más grande al más pequeño.
1. Mostrar los 3 últimos pedidos (_orders_)

### 3. WHERE (para filtrar los datos según condiciones)

Ejemplos:

```
SELECT 
    lastname, 
    firstname, 
    jobtitle
FROM
    employees
WHERE
    jobtitle = 'Sales Rep';
```

- AND, OR:

```
SELECT 
    lastname, 
    firstname, 
    jobtitle
FROM
    employees
WHERE
    jobtitle = 'Sales Rep' AND 
    officeCode = 1;
```

- operadores matemáticos: <, >, <>, >=, <=

```
SELECT 
    lastname, 
    firstname, 
    officeCode
FROM
    employees
WHERE 
    officecode > 5;
```

- Combinar condiciones:

```
SELECT    
 customername, 
 country, 
 state, 
 creditlimit
FROM    
 customers
WHERE country = 'USA'
 AND state = 'CA'
 AND creditlimit > 100000;
```

```
SELECT    
 customername, 
 country
FROM    
 customers
WHERE country = 'USA'
 OR country = 'France';
```

```
SELECT   
 customername, 
 country, 
 creditLimit
FROM   
 customers
WHERE(country = 'USA'
 OR country = 'France')
   AND creditlimit > 100000;
```

- IN / NOT IN:

```
SELECT 
    officeCode, 
    city, 
    phone
FROM
    offices
WHERE
    country IN ('USA' , 'France');
```
```
SELECT 
    officeCode, 
    city, 
    phone
FROM
    offices
WHERE
    country NOT IN ('USA' , 'France');
```

- BETWEEN:

```
SELECT 
    productCode, 
    productName, 
    buyPrice
FROM
    products
WHERE
    buyPrice BETWEEN 90 AND 100;
```

- LIKE:

```
SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    firstName LIKE 'a%';
```

```
SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    lastName LIKE '%on';
```

**Ejercicios:**
1. Mostrar los productos que corresponden a una linea de productos que contiene la palabra "Cars" en su nombre.
1. Mostrar los productos que no son de tipo "Planes" y "Motorcycles".


### 4. JOIN (para juntar datos de varias tablas)

- Alias:

```
SELECT
 customername AS `name`
FROM
 customers;
```

```
SELECT
 CONCAT_WS(', ', e.lastName, e.firstname) AS `Full name`
FROM
 employees e;
```

- Join:

```
SELECT 
    productCode, 
    productName, 
    textDescription
FROM
    products t1
        INNER JOIN
    productlines t2 ON t1.productline = t2.productline;
```

```
SELECT 
    productCode, 
    productName, 
    textDescription
FROM
    products
        INNER JOIN
    productlines USING (productline);
```

```
SELECT
 c.customerNumber,
 c.customerName,
 orderNumber,
 o.status
FROM
 customers c
LEFT JOIN orders o ON c.customerNumber = o.customerNumber;
```

**Ejercicios:**
1. Mostrar los nombres y apellidos de las personas que compraron productos de tipo "Planes".
1. Mostrar los nombres y appellidos de las personas que NO compraron productos de tipo "Planes".

### 5. GROUP BY (agrupar datos según valores de una o varias columnas

```
SELECT 
    status
FROM
    orders
GROUP BY status;
```

- función de agregación: COUNT

```
SELECT 
    status, COUNT(*)
FROM
    orders
GROUP BY status;
```

- función de agregación: SUM

```
SELECT 
    status, SUM(quantityOrdered * priceEach) AS amount
FROM
    orders
        INNER JOIN
    orderdetails USING (orderNumber)
GROUP BY status;
```

```
SELECT 
    orderNumber,
    SUM(quantityOrdered * priceEach) AS total
FROM
    orderdetails
GROUP BY orderNumber;
```

- agrupar por fecha:

```
SELECT 
    YEAR(orderDate) AS year,
    SUM(quantityOrdered * priceEach) AS total
FROM
    orders
        INNER JOIN
    orderdetails USING (orderNumber)
WHERE
    status = 'Shipped'
GROUP BY YEAR(orderDate);
```

- funciones de agregación: MAX, MIN, AVG


- Filtrar los resultados después un GROUP BY: HAVING

```
SELECT 
    YEAR(orderDate) AS year,
    SUM(quantityOrdered * priceEach) AS total
FROM
    orders
        INNER JOIN
    orderdetails USING (orderNumber)
WHERE
    status = 'Shipped'
GROUP BY year
HAVING year > 2003;
```

```
SELECT 
    ordernumber,
    SUM(quantityOrdered) AS itemsCount,
    SUM(priceeach*quantityOrdered) AS total
FROM
    orderdetails
GROUP BY ordernumber
HAVING total > 1000;
```

```
SELECT 
    orderYear,
    productLine, 
    SUM(orderValue) totalOrderValue
FROM
    sales
GROUP BY 
    orderYear,
    productline
WITH ROLLUP;
```

**Ejercicios:**
1. Mostrar cuántos productos existen según linea de productos.
1. Mostrar cuáles son los clientes que realizarón más de 3 pedidos (orders)

### 6. Subconsultas

- Utilizando la clausula IN o NOT IN:

```
SELECT 
    lastName, firstName
FROM
    employees
WHERE
    officeCode IN (SELECT 
            officeCode
        FROM
            offices
        WHERE
            country = 'USA');
```

- Utilizando la clausula WHERE:

```
SELECT 
    customerNumber, checkNumber, amount
FROM
    payments
WHERE
    amount = (SELECT 
            MAX(amount)
        FROM
            payments);
```
```
SELECT 
    customerNumber, checkNumber, amount
FROM
    payments
WHERE
    amount > (SELECT 
            AVG(amount)
        FROM
            payments);
```

- Utilizando la clausula FROM:

```
SELECT 
    MAX(items), MIN(items), FLOOR(AVG(items))
FROM
    (SELECT 
        orderNumber, COUNT(orderNumber) AS items
    FROM
        orderdetails
    GROUP BY orderNumber) AS lineitems;
```

**Ejercicios:**

1. Mostrar qué día se vendió el producto más carro del catalogo.
1. Mostrar qué empleado realizó más volumen de negocio que los otros empleados.


###. 7. Consultas adicionales:

1. Mostrar el numeros de empleados por oficinas
1. Mostrar cómo evoluciona el volumen de negocio por mes
1. Mostrar el volumen de negocio agrupado según el producto
1. Mostrar qué productos nunca se vendieron
1. Mostrar los productos que contienen las palabras "red", "blue" y "amarillo" en su descripción.
1. Mostrar el volumen de negocio realizado agrupado por los productos que contienen la palabra "red" y los productos que contienen la palabra "azul". 


