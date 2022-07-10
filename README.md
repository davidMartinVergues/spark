# Apache Spark

Es un framework de desarrollo para procesos de Big Data. Spark se puede implementar con 4 lenguajes d eprogramación:

1. Java
2. Scala
3. Python
4. R

Nativamente Spark corre en Scala y éste a su vez corre en la máquina virtual de Java.

Spark hace hincapié en la velocidad de procesamiento y es por ello que preferentemente usa memoria RAM aunque tb puede usar el Disco Duro. Así los procesos que genera Spark son casi continuos, en tiempo real. 

## Base de datos según el modelo de datos

Un **modelo de base de datos** es aquello capaz de mostrar una estructura lógica de la base de datos entre las relaciones y limitaciones que se tienen para el almacenamiento y lectura de los datos.

### BBDD Relacionales

este tipo de base datos cumple con el modelo relacional y, almacena los datos en tablas organizadas por filas y columnas y que existen las llaves, con las cuales podemos crear relaciones entre tablas, siempre cuidando y asegurando la integridad de los datos.

Entre sus principales características tenemos que:

1. Nos permite almacenar datos en varias tablas, las cuales llamaremos relaciones, dichas relaciones deben de tener un nombre único dentro de la base de datos.
   
2. La forma en que se relacionan las tablas, es a través de llaves primarias y foráneas.
   
3. Interpretar a una llave primaria como la clave principal que gobiernan los registros o filas de una tabla y con la cual aseguramos la integridad de los datos.

4. Con llaves foráneas relacionaremos dos o más tablas, por ejemplo, si tenemos una tabla padre con su clave primaria, nosotros podemos crear una llave foránea la cual colocaremos en una tabla hija y, está llave foránea tendrá exactamente el mismo valor que la llave primaria de la tabla padre, con esto hemos creado una relación entre estas dos tablas.


### BBDD Transaccionales

Las bases de datos transaccionales tienen la característica especial de estar diseñadas para aquellos sistemas en que los datos cambian constantemente (**transacciones**), es decir son capaces de gestionar gran cantidad de transacciones (SELECT, UPDATE, DELETE) con una alta velocidad.  Estas bases de datos no tienen problemas de duplicidad, desnormalización o redundancia en la información. Las bases de datos transaccionales utilizan lenguaje SQL, que permite el acceso y la modificación de los datos dentro de la bases de datos.

Un punto importante es que una transacción generará un proceso atómico que puede conllevar bien operaciones de inserción, modificación o borrado de datos. Este proceso debe ser validado con un **commit** o invalidado con **rollback**; con el primero se ejecuta la operación y con el segundo no se produce, volviendo al estado original.

La base de datos transaccionales funciona de manera asociada a una base de datos relacional. Es decir, la función de la base de datos transaccionales es asegurar que las transacciones dentro de la base de datos relacional se cumplen de manera completa o, en caso de haber un error o fallo en el proceso, se reviertan y por tanto no se completen (un sistema de «todo o nada»).

En cierto sentido, la base de datos relacional nos indica cómo se almacenan los datos y la base de datos transaccional nos dice cómo se modifican esos datos.

El ejemplo clásico de transacción y el uso de este tipo de modelo es en las transferencias bancarias, donde todos los días millones de personas realizan operaciones financieras, las cuales finalmente se transforman en consultas, actualizaciones o eliminación de datos dentro de la DB.

### BBDD Multidimensionales




## Sistemas de manejo de la información


### OLTP (On-line TransacTion Processing)


### OLAP (On-line Analytical Processing )



## Qué no es Spark

Spark **no** es una base de datos 