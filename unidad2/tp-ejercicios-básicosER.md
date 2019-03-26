## Universidad Austral de Chile

# INFO133: Base de Datos

### Responsable: Matthieu Vernier, mvernier@inf.uach.cl

## TP: Ejercicios básicos de modelación ER

En cada uno de los casos siguientes, se pide diseñar un modelo Entidad-Relación utilizando la simbología de Chen. Indicaran las entidades con un Sustantivo al singular, las relaciones con un Verbo al infinitivo, sin olvidar las cardinalidades y las claves primarias.

### 1. Sistema de gestión de permisos de circulación en la ciudad de Valdivia

La municipalidad de Valdivia quiere desarrollar un sistema para gestionar la entrega de los permisos de circulación. El sistema debe permitir gestionar información sobre los ciudadanos, como su nombre, fecha de nacimiento, fecha de primera obtención de la licencia, RUT, dirección. Tambien implica almacenar información sobre los vehiculos, como la patente, la marca, el color, el tipo de vehiculo. La municipalidad quiere poder conservar datos a lo largo del tiempo en su base de datos sin perder información pasada.

### 2. Sistema de gestión de una empresa de transportes

Una empresa de transportes reparte paquetes por todo Chile. Los encargados de llevar los paquetes son los camioneros, de los que se quiere guardar el RUT, nombre, teléfono, dirección, salario y población en la que vive. De los paquetes transportados interesa conocer el código de paquete, su descripción, desintario y dirección del destinario. Un camionero distribuye muchos paquetes, y un paquete sólo puede ser distribuido por un camionero.

De las ciudades a las que llegan los paquetes interesa guardar el código de la ciudad y el nombre. Un paquete sólo puede llegar a una ciudad. Sin embargo, a una ciudad pueden llegar varios paquetes.

De los camiones que llevan los camioneres, interesa conocer la matricula, modelo, tipo y potencia. Un camionero puede conducir diferentes camiones en fechas diferentes, y un camión puede ser conducido por varios camioneros.

### 3. Sistema de información Carreteras

Diseñar un diagrama entidad-relación que recoja la organización de una base de datos para contener
la información sobre todas las carreteras del paı́s, sabiendo que se deben cumplir las siguientes
especificaciones:

• Las carreteras están divididas en varias categorı́as (locales, comerciales, regionales, nacionales,
autovı́as, etc).

• Las carreteras se dividen en tramos. Un tramo siempre pertenece a una única carretera y no
puede cambiar de carretera.

• Un tramo puede pasar por varias comunas, interesando conocer el Km de la carretera y la
comuna donde empieza el tramo y en donde termina.

• Para los tramos que suponen principio o final de carretera, interesa saber si es que la carretera
concluye fı́sicamente o es que confluye en otra carretera. En este caso, interesa conocer con
qué carretera confluye y en qué kilómetro, tramo y comuna.

### 4. Sistema de gestión de un hospital

Proponemos modelar la base de datos de un hospital. El análisis del sistema existente reveló la siguiente información:
- El hospital tiene un conjunto de empleados que son médicos y enfermeros. Cada empleado tiene un número de empleado, apellido, nombre, dirección y número de un teléfono.
- El hospital está compuesto por varios departamentos, cuyo código, nombre, número de teléfono y número de fax son conocidos, y el director, que en realidad es médico.
- Cada departamento contiene varias habitaciones. Una sala está representada por un número, un
y el número de camas que tiene. El número de habitación es local para un departamento
(es decir, cada departamento tiene una sala número 1). Un supervisor es un/a enfermero/a.
- Un/a enfermero/a está asignada a un departamento y sólo a un departamento.
- Los médicos no están asignados a un departamento en particular, pero conocemos su especialidad.
- También conocemos la rotación y el salario de cada enfermero.
- Los pacientes del hospital están representados por un número, un apellido, un nombre, un apellido, un nombre, un dirección y número de teléfono.
- Un paciente es hospitalizado en una habitación con un número de cama y un diagnóstico. Él es tratado por un médico. En caso de complicaciones, se puede transferir a un otro servicio con otra habitación.

### 5. Artı́culos y encargos

Una base de datos para una pequeña empresa debe contener información acerca de clientes, artı́culos
y pedidos. Hasta el momento se registran los siguientes datos en documentos varios:
- Para cada cliente: Número de cliente (único), Direcciones de envı́o (varias por cliente), Saldo,
Lı́mite de crédito (depende del cliente, pero en ningún caso debe superar los $30.000.000),
Descuento.
- Para cada artı́culo: Número de artı́culo (único), Fábricas que lo distribuyen, Existencias de
ese artı́culo en cada fábrica, Descripción del artı́culo.
- Para cada pedido: Cada pedido tiene una cabecera y el cuerpo del pedido. La cabecera está
formada por el número de cliente, dirección de envı́o y fecha del pedido. El cuerpo del pedido son varias lı́neas, en cada lı́nea se especifican el número del artı́culo pedido y la cantidad. Además, se ha determinado que se debe almacenar la información de las fábricas. Sin embargo, dado el uso de distribuidores, se usará: Número de la fábrica (único) y Teléfono de contacto. Y se desean ver cuántos artı́culos (en total) provee la fábrica. También, por información estratégica, se podrı́a incluir información de fábricas alternativas respecto de las que ya fabrican artı́culos para esta empresa.
