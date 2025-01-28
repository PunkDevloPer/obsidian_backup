
luego corremos un gobuster sobre la ip  y luego sobre la ruta que nos salga
![[14_Imagenes/lazyadmin/gobuster.png]]
por ejemplo aquí primero nos salió la ruta content y luego sobre esa ruta hacemos el otro fuzzing
si verificamos la ruta que dice inc podemos observar varios documentos y archivos, debemos encontrar algo que nos sea de utilidad 
![[sql.png]]
aqui vemos la carpeta MYSQL_backup si entramos a la carpeta debe haber una base de datos  la descargamos y la abrimos haber que encontramos
![[Pasted image 20230911171854.png]]
buscamos un usuario y contraseña 
![[sqlbk.png ]]
procedemos a guardar ambos datos en un txt
![[Pasted image 20230911172203.png ]]
lo que debemos hacer a continuación es validar que tipo de hash es el que se esta usando.
para ello desarrolle mi propia herramienta. pero hay herramientas universales para kali linux.
![[Pasted image 20230911172821.png ]]
en este caso el hash es el MD5
ahora debemos usar john the ripper
![[Pasted image 20230911172821.png ]]
ahora ya tenemos el usuario y la contraseña.
ya podemos entrar a algun panel de login
buscando di con la ruta /content/as

![[Pasted image 20230911174040.png ]]
![[Pasted image 20230911173807.png ]]
aun no tenemos acceso al servidor pero ya tenemos acceso a un panel administrativo. esto es bueno.
