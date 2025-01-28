el path traversal también denominado ataque de recorrido de ruta es una vulnerabilidad que tiene como objetivo acceder a archivos y directorios fuera de la carpeta web. al manipular archivos con secuencias ./ ./ ./ y sus variaciones o mediante el uso de rutas de archivo absolutas es posible acceder a archivos y directorios de forma arbitraria incluso el código fuente de la aplicación o configuraciones criticas del sistema.
otros nombres para este ataque son : recorrido de directorio, escalada de directorio.

algunos de los Bypass mas comunes para este ataque son :


    %2e%2e%2f representa ../
    %2e%2e/ representa ../
    ..%2f representa ../
    %2e%2e%5c representa ..\
    %2e%2e\ representa ..\
    ..%5c representa ..\
    %252e%252e%255c representa ..\
    ..%255c representa ..\
para tener un ejemplo de este ataque puede considerarse la siguiente URL
	http://10.0.2.11/football/index.php?view=../../../../../../../etc/passwd
	![[Pasted image 20240521223406.png]]
	
en donde esta dando acceso a la carpeta passwd donde se almacenan los usuarios. aquí otro ejemplo de la gravedad
 http://10.0.2.11/football/index.php?view=../../../../../../../home/manolo/.ssh/id_rsa
 ![[Pasted image 20240521223540.png]]
 con esta vulnerabilidad se puede tener acceso a archivos sensibles de configuración, bases de datos o configuración y archivos del sistema 
si esta vulnerabilidad existe es posible encontrarse con [[18-Local File Inclusión]] 