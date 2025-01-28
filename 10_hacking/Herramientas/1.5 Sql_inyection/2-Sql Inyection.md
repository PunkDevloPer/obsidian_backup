los parámetros de SQL inyection son relativamente descriptivos de acuerdo a la función que se quiera realizar

para mas información consultar [[09_SQL/1.0. Temario|1.0. Temario]] sobre SQL 

 --exclude-sysdbs excluye las bases de datos  del sistema
 -H: se usa para incluir cabeceras en la solicitud.
-- dbs: se usa para descubrir las bases de datos
-- tables: se usa para descubrir las tablas  de la base de datos 
-- batch: se utiliza para que la ejecución sea totalmente automatizada.
--level : es el nivel de pruebas a realizar por defecto en 1 
--risk: el riesgo de las pruebas a realizar.
--time-sec : es el tiempo en segundos para retrasar la respuesta del sistema de gestión de bases de datos.
--text-only: compara paginas basadas solo en el contenido textual
-U : es  el parámetro para especificar la URL
-d : es el parámetro para conectarse directamente a la base de datos si ya se sabe el nombre.

la estructura general de sqlmap seria:
```bash
sqlmap -u "direccion ip" -H "cabecera" --dbs --tables --exclude-sysdbs --text-only --threads=10 --batch --level=5
```
solo he puesto algunas flags pues no siempre serán necesarias y otras veces serán necesarias otras opciones dependiendo de lo que se quiera hacer.
