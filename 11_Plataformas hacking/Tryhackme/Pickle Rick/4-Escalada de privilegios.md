lo primero que vamos a hacer es una búsqueda de permisos SUID con el siguiente comando.
find / -perm -4000 -ls 2>/dev/null 
o este 
find / -user root -perm -4000 -print 2>/dev/null
si nos fijamos bien debe existir algun archivo dentro de la carpeta /bin/ del que se pueda abusar para escalar privilegios
![[Pasted image 20230902144540.png]]

podemos consultar https://gtfobins.github.io/
en este caso el binario es pkexec tan facil como ejecutar sudo pkexec /bin/bash y ya somos root
![[Pasted image 20230902144711.png]]
allí esta la tercera bandera 
![[Pasted image 20230902144827.png]]
eso es todo!
