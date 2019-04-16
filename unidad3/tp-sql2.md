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

**Ejericios:**
1.
1.

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

```
SELECT
 customernumber,
 customername,
 creditlimit
FROM
 customers
LIMIT 10;
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

**Ejercicios:**
1.
1.
1.
1.
1.

### 4. JOIN (para juntar datos de varias tablas)


