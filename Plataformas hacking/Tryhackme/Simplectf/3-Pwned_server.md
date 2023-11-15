encontramos un script 
![[Pasted image 20230906150712.png]]
vemos según la descripcion del script que es vulnerable a sqli
tenemos que ver si el de xploit db funciona en caso contrario podemos buscar por el CVE que nos proporciona exploitdb y tratar de encontrar otro script para realizar el proceso.
en mi caso estoy usando 
https://github.com/e-renna/CVE-2019-9053

entonces escribimos :
![[Pasted image 20230906161851.png]]
y esperamos a que nos de el resultado.
![[Pasted image 20230906161909.png]]
ahora lo que debemos hacer es usar hashcat
para crackear la contraseña.
![[Pasted image 20230906162432.png]]
ahora esperamos
y si todo sale bien deberia darnos el password del hash que pusimos 
![[Pasted image 20230906162910.png]]
ahora ya tenemos un usuario y una contraseña no?
pues ahora vamos al ssh 
recuerden que el servicio ssh esta en el puerto 2222
![[Pasted image 20230906163346.png]]
ya estamos dentro de la maquina
aqui esta la primera bandera
![[Pasted image 20230906163442.png]]
ahora vamos a escalar privilegios 
