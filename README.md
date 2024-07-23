# CS-SQL
Estos apuntes fueron creados mientras estudiaba y repasaba algunos de los temas después de completar el CFGS. Estoy abierto a cualquier corrección en caso de errores.

## <strong>Que son las bases de datos ?</strong>
  
Una base de datos es una colección organizada de datos que permite su almacenamiento, acceso y manipulación de manera eficiente. Está diseñada para gestionar grandes volúmenes de información y proporcionar las herramientas necesarias para que los usuarios puedan consultar, actualizar y administrar los datos según sus necesidades específicas.

## <strong>Que diferencia hay entre bases de datos relacionales y las no relacionales ?</strong>
Las bases de datos relacionales consisten en una colección de datos organizados en tablas. SQL se utiliza como lenguaje para la manipulación de estas tablas, enfocándose en la organización de los datos en partes interrelacionadas mediante identificadores. En contraste, las bases de datos no relacionales se centran en modelos de datos específicos con esquemas más flexibles. Su principal característica diferenciadora respecto a las bases de datos relacionales es la ausencia de identificadores que establezcan relaciones entre conjuntos de datos.

## <strong>Que diferencia existe entre Mysql y SQL ? </strong>
  
SQL (Structured Query Language) es el lenguaje estándar utilizado para establecer comunicación con nuestras bases de datos, permitiendo realizar consultas, actualizaciones, inserciones y eliminaciones de datos, así como la gestión de la estructura de la base de datos.
  
| Ejemplo | Descripción |
| --- | --- |
| SELECT * FROM cats_name | Todos los nombres que tengamos de gatos en nuestra base de datos.

Por otro lado, MySQL es uno de los posibles sistemas de gestión de bases de datos que utiliza SQL para manipular los datos.   
  
Existen varios gestores de bases de datos diferentes, como <strong>MySQL, SQLite, PostgreSQL y Oracle, entre otros.</strong>

## Tipos de datos

Al crear una tabla mediante SQL, es fundamental especificar el tipo de datos que se van a introducir. A continuación, presento una tabla con los formatos de datos más utilizados. Cabe mencionar que existen muchos más tipos de datos.
  
Si deseas consultarlos, puedes visitar el sitio web de [W3schools](https://www.w3schools.com/sql/sql_datatypes.asp)

| String Data | Description |     
| --- | --- |                      
| CHAR| Cadena de longitud fija que puede contener letras, números y caracteres especiales, con una longitud de 1 a 255 caracteres. De modo predeterminado, su valor es 1. |              
| VARCHAR | Cadena de longitud fija que puede contener letras, números y caracteres especiales, con una longitud de 1 a 65535 caracteres.|

| Numeric Data | Description |
| --- | --- |
| INT|  Un integer de rango medio. El rango alcanza desde -2147483648 a 2147483647.|
| DECIMAL | Valor utilizado para las expresiones con decimales. |

| Numeric Data | Description |
| --- | --- |
| TIME| Formato para hh:mm:ss |
| DATE | Formato para YYYY-MM-DD |
| YEAR | Formato de 4 digitos numericos. |

## Claves primarias y Claves Foraneas

La clave primaria (primary key) es una columna o un conjunto de columnas en una tabla cuyas valores son únicos entre sí, con el objetivo de diferenciar de manera inequívoca cada fila de la tabla. Es decir, cada valor de la clave primaria debe ser único y no nulo.

Si tenemos una tabla de  

| user_id | Nombre | Email |        
| --- | --- | --- |                        
| 1|  Anna|  anna@example.com|             
| 2|  Pedro|  pedro@example.com|
| 3|  Marta|  marta@example.com|
 

En este caso, user_id es la clave primaria porque cada valor es único y permite identificar de forma exclusiva cada registro de la tabla.

> Para hacer un uso más óptimo de una clave primaria, podemos utilizar el atributo AUTO_INCREMENT, ya que nos asignará valores de forma incremental a la columna especificada en la tabla.

Por otro lado las claves foráneas (foreign keys) son columnas en una tabla que establecen una relación con la clave primaria de otra tabla. Su principal función es asegurar la integridad referencial de los datos, lo que significa que solo pueden contener valores presentes en la clave primaria de la tabla a la que hacen referencia.

## Inserción de datos
En las bases de datos aparte de tener la posibilidad de modificar estas recoger informacion y etc tambien tenemos la posibilidad de añadir nuevos datos a las tablas en caso de que sea necesario es por esto que podemos dar uso del :   

    INSERT INTO "DATABASE" (TABLE-1, TABLE-2, TABLE-3) VALUES (DATA-1, DATA-2, DATA-3)

# Ejemplo de Base de Datos con Tablas Relacionadas e Inserción de Datos

CREATE DATABASE school; 
    
CREATE TABLE students    
(     
book_id INT AUTO_INCREMENT,   
first_name VARCHAR(100),    
PRIMARY KEY(book_id)    
);     

create table papers     
(    
title varchar(50),   
grade INT,    
student_id INT,    
FOREIGN KEY (student_id) REFERENCES students(book_id)    
);     
