# Apache Spark

Es un framework de desarrollo para procesos de Big Data. Spark se puede implementar con 4 lenguajes de programación:

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

La definición de bases de datos multidimensionales viene marcada por la forma en la que guardan y procesan la información. Al igual que las bases de datos relacionales, almacenan la información en tablas. Sin embargo, la diferencia radica en la estructura que forman estas tablas, ya que en las bases multidimensionales los datos se ven como «cubos de información«.

Estos cubos de información añaden una nueva dimensión a las tradicionales bases de datos formadas por tablas. Los cubos están formados por dos componentes:

* Tabla de dimensiones: aquí se almacenan datos como ítems (nombre del producto, marca, etc) o fechas
* Tabla de hechos: almacena las medidas y las claves que la relaciona con las tablas de dimensiones. Por ejemplo, tamaño en centímetros o valor en euros.


Las bases de datos multidimensionales o MDB son ampliamente utilizadas en el entorno de los Data Warehouse y para aplicaciones encargadas de realizar análisis de procesos en línea. También es habitual que este tipo de bases de datos se empleen usando la información ya contenida en otras bases de datos relacionales.

Por otro lado, lo sistemas de gestión de bases de datos multidimensionales (MDDBMS) son capaces de procesar la información a gran velocidad, lo que las convierte en una herramienta muy útil para entornos o aplicaciones que requieren obtener respuestas a las consultas inmediatas o en tiempo real.


## Sistemas de manejo de la información


### OLTP (On-line TransacTion Processing)


### OLAP (On-line Analytical Processing )

Una bbdd tradicional con muchas transaciones(entradas salidas de datos, actualizaciones, etc...) en tiempo real

## WAREHOUSE

## DATA-LAKE


## Qué no es Spark

Spark **no** es una base de datos, spark lo q hace es utilizar datasets q pueden provenir de un bbdd. Por ejemplo si ponemos spark a funcionar con un set de datos del tipo OLAP, con muchas transacciones, Spark funcionará muy deficientemente. Lo ideal es q spark esté conectado a teclologías tipo datawarehouse o data-lake para poder usar correctamente spark.

Podríamos decir q spark es el hermano mayor de Hadoop, es decir hereda muchas de sus características, hadoop presenta una sistema de almacenamiento de gran cantidad de datos, gracias a q es un sistema distribuido y clusterizado pero no está enfocado a dar una respuesta rápida ya que opera a nivel de disco duro. Spark en cambio tiene la info en RAM por lo q es más rápido aunq dependiendo del caso podemos pasarlo a duscoduro.

Spark posee:
- módulos nativos de Machine Learning, streaming y grafos
- no depende de un sistema de archivos (podemos consumir datos desde archivos planos, a archivos con extensión 
 .hdfs hadoodFileSystem, ... )

## Que son los RDDs y DataFrames

Las dos Principales estructuras que soporta Spark son los `RDD` (es el componente mínimo con el cual podemos comunicarnos con SPark) y los `DataFames`. 

La diferencia entre ambos reside es la estructura que poseen

### RDDs

Son la principal abstracción de datos, es la unidad básica de datos. Estos datos son distribuidos a lo largo de todos los clusters(de maquinas conectadas). 

- CREACIÓN DE UN RDD
  
Son muy simples de crear, ya que no tienen una estructura de datos como tal, simplemente son conjuntos de datos por ejemplo listas o tuplas. **SON INMUTABLES** una vez creados no los podemos modificar.Tienen lo q se llama `ejecución perezosa` podemos ir escribiendo código, por ejemplo leer un archivo, y si éste no funciona o tine errores no obtendremos ningún mensaje de error hasta q no realicemos una acción, es decir hasta q no le digamos a spark por ejemplo muestrame los datos o hazme un contaje de los mismos, etc... 

Así las transformaciones de los datos (orderBy, groupBy,filter, select, join,...) no supondrán un problema hasta q no realicemos las acciones (show,take,count,collect,save)

### DATAFRAME

Son una capa superior sobre los RDDs, la principal diferencia es q contiene estructura en forma de tabla, los datos se organizan en filas y columnas. Están más optimizados que los RDDs. Los podemos crear a partr de una bbdd, un archivo externo,..etc

Preferiblemnete utilizar DATAFRAMES, aunq podemos usar los RDDs para:

- Cuando te interesa controlar el flujo de Spark, ya que al trabajar con DATAFARMES el optimizador interno de SPARK realiza pequeñas modificaciones que no realiza cuando trabajamos con RDDs

- Si trabajamos con python podemos convertir un RDD a un conjunto de datos de python

- Si trabajamos con versión 1 de Spark (en esta versión no existe los dataframes) 


Cuando usar DATAFRAMES

- Cuando tengamos operaciones complicadas
- cuando vamos a realizar operaciones de alto nivel como filtros, mapeos, agregaciones,..
- Podemos aplicar sentencias SQL a los datframe

LOS RDDs POSEEN 3 CARACTERÍSTICAS BASE:

* SON DISTRIBUIDOS
* SON INMUTABLES
* SON PEREZOSOS (hasta q no ejecutemos una acción el código no corre realmente)


