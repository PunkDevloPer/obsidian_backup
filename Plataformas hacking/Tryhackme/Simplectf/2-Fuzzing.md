a primera vista vemos en el servidor http 	la pantalla de inicio de cuando se instala un servidor apache que nos indica que todo esta funcionando..
![[Pasted image 20230906150229.png]]hagamos algo de fuzzing
obtenemos una ruta 
![[Pasted image 20230906150336.png]]
en este  punto vemos que esa ruta nos redirecciona a un CMS
![[Pasted image 20230906150418.png]]
podemos ver algo de información por ejemplo que el cms es la version 2.2.8, con esta version podemos ver que se puede explotar... tambien esta el servicio ssh y ftp.

