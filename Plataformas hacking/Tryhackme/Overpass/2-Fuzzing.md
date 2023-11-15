en este caso hare el fuzzing con gobuster, primero voy a crear una variable llamada dic en donde voy a meter la ruta del diccionario 
![[Pasted image 20231003144101.png]]
listo ahora lanzamos un gobuster 

![[Pasted image 20231003144140.png]]
como podemos observar nos da unas rutas interesantes la que mas nos importa es /admin/
ahora lo que haremos sera ir a esa ruta
![[Pasted image 20231003144317.png]]
primero inspeccionemos la web como buena practica para ver que podemos encontrar.
si nos vamos al head del html vemos que hay varios scripts
![[Pasted image 20231003144416.png]]
en el script llamado login.js vemos una parte del codigo que hace referencia a una cookie 
![[Pasted image 20231003144602.png]]
la cookie se llama SessionToken y e valor en path es /
![[Pasted image 20231003145135.png]]
aqui estan los pasos 
<li> en opciones de desarrollador vamos a Almacenamiento luego a cookies luego en añadir luego cambiamos el nombre de la cookie y el path
</li>
recargamos la pagina
ya tenemos acceso a un RSA para conexión ssh 
![[Pasted image 20231003145337.png]]
lo copiamos y ahora vamos a usar ssh2john

ya tenemos el RSA en formato legible para john 
![[Pasted image 20231003145953.png]]
ahora vamos a crackearla usando john y el diccionario rockyou
![[Pasted image 20231003150405.png]]
una vez obtenido el usuario vamos a proceder a darle permisos a la llave rsa con chmod 600 Rsakey
