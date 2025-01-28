ahora vamos a tomar el servidor 
![[Pasted image 20231003153120.png]]
vamos a buscar permisos SUID
![[Pasted image 20231003154547.png]]
como vemos no hay un binario que nos permita hacer una escalada de privilegios, trate de usar pkexec pero no dio resultado.
si leemos el archivo todo.txt vemos que haba sobre automatizar algun proceso 
![[Pasted image 20231003154711.png]]
si estan automatizando algo entonces deben usar el programador de tareas en este caso en linux seria crontab 



