vamos a hacer fuzzing con gobuster
![[Pasted image 20230902133813.png]]
efectivamente hay una ruta llamada assets que deberíamos revisar
si nos fijamos a la hora de hacer fuzzing se descubren 3 sitios el primero es assets el segundo es index.html y el tercero es robots.txt 
 ya tenemos el usuario y la contraseña
R1ckRul3s
Wubbalubbadubdub
lo que debemos hacer es por lógica tratar de buscar una pagina de inicio de sesión un "login"
en este caso ponemos login.php
nos mostrara un inicio de sesión y luego cuando ponemos el usuario y la contraseña sale un panel de comandos. o RCE "ejecution remote code"
hay algunos comandos deshabilitados por lo que tenemos que buscar alternativas
el comando CAT no sirve en su lugar usar Less
