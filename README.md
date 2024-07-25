# CheatSheet-SQL
Estos apuntes fueron creados mientras estudiaba y repasaba algunos de los temas después de completar el CFGS. Estoy abierto a cualquier corrección en caso de errores.  

> Algunos datos pueden estar simplificados, por eso siempre recomiendo contrastar con sitios web oficiales.

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

## Ejemplo de Base de Datos con Tablas Relacionadas e Inserción de Datos

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

INSERT INTO students (first_name) VALUES  ('Caleb'), ('Samantha'), ('Raj'), ('Carlos'), ('Lisa');    
INSERT INTO papers (student_id, title, grade ) VALUES (1, 'My First Book Report', 60); 

# Sintaxis  SQL

Diferentes tipos de sentencias y manipulación de datos.

Crea la base de datos.

    CREATE DATABASE <name>; 
Usa la base de datos.

    USE DATABASE <name>;
Selecciona la base de datos

    SELECT DATABASE <name>; 
Borra la base de datos con nombre X.

    DROP DATABASE <name>; 
Crea una tabla SQL

    CREATE TABLE <name> (DATA TYPES);
Muestra las tablas de una base de datos

    SHOW TABLES;
Muestra las columnas de una tabla.

    SHOW COLUMNS FROM <tablename>; 
Borra una tabla de una base de datos.

    DROP TABLE <tablename>;
Insercion de datos a una tabla.

    INSERT INTO <database> (table1, table2,table3) VALUES (valor1,valor2,valor3); 

> IMPORTANTE : Los datos de table1, table2 y table3 tienen que cuadrar con el orden de VALUES. Es decir, si table1 es un INT y la segunda es un VARCHAR, es importante seguir este orden al especificar los valores. Value1 debe ser un INT y value2 debe ser un VARCHAR.

Para seleccionar las columnas de una tabla.

    SELECT <columna> FROM <tablename>;
WHERE -> Condicional que usaremos en algunas sentencias para establecer algunas condiciones.

     select <columna> from <tablename> WHERE;
AS -> Se utiliza para cambiar el nombre en los resultados de una query.

    SELECT <columna> AS <new_name_columna> FROM <tablename>; 
SET UPDATE -> Para actualizar valores de una tabla siguiendo una condicion X.

    UPDATE <columna> SET <condition> WHERE <condition>
> EXAMPLE: UPDATE cats SET breed='British Shorthair' WHERE name='Ringo';
>  
> En este ejemplo, actualizaremos en la tabla cats (gatos) la raza de todos los gatos llamados Ringo a 'British Shorthair'.

DELETE -> Para borrar datos que ya no necesitamos de una tabla.

    DELETE FROM <tablename> WHERE <condition>; 
CONCAT -> Para unir varios strings.

    SELECT CONCAT(columna1, ' ', columna2) FROM <database>;
> Ejemplo : SELECT CONCAT(author_fname, ' ', author_lname) FROM books;
>    
> El resultado seria el nombre completo del autor con un espacio en medio.

    

 


    
