## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Lenguaje SQL - Consultar, Ordenar, Filtrar, Agrupar

### 1. Instalar la Base de Datos de prueba

En este TP, trabajaremos con una base de datos llamada __classicmodels__. El Modelo Relacional de este base es el siguiente:

- offices (**officeCode**, city, phone, addressLine1, addressLine2, state, country, postalCode, territory)

- employees (**employeeNumber**, lastName, firstName, extension, email, jobTitle, #officeCode (offices), #reportsTo (employees))

- customers (**customerNumber**, customerName, contactLastName, contactFirstName, phone, addressLine1, addressLine2, city, state, postalCode, country, creditLimit, #salesRepEmployeeNumber (employees))

- payments (#**customerNumber** (customers), **checkNumber**, paymentDate, amount)

- orders (**orderNumber**, orderDate, requiredDate, shippedDate, status, comments, #customerNumber (customers))

- productLines (**productLine**, textDescription, htmlDescription, image)

- products (**productCode**, productName, productScale, productVendor, productDescription, quantityInStock, buyPrice, MSRP, #productLine (productLines))

- orderdetails (#**orderNumber** (orders), #**productCode** (products), quantityOrdered, priceEach, orderLineNumber)
 

Pueden descargar la Base de Datos [aquí](classicmodels.sql), instalandola en la carpeta __/unidad3__ de su carpeta de trabajo.

Desde el cliente MySQL, instalar la base de datos __classicmodels__ con el comando:

> source classicmodels.sql

Pueden verificar que la instalación se realizó correctamente con los comandos:

> use classicmodels;
> show tables;
> select * from customers;

### 2. SELECT vs. SELECT DISTINCT

Ejemplos:

> SELECT lastname, firstname, jobtitle 
FROM employees;



