Como esta permitida la ejecucion remota de comandos podemos hacer una reverse shell mediante bash 
en este caso usamos el generador de reverse shell con la opcion PERL y la terminal BASH
![[Pasted image 20230902142648.png]]

ejecutamos en la consola de nuestra maquina una escucha en el puerto que asignemos en el generador por ejemplo yo uso el puerto 4439 y seguidamente ejecutamos el comando de la reverse shell en el panel de comandos. inmediatamente debe darnos acceso al servidor.
hagamos el tratamiento de la tty
1 script /dev/null  -c bash pulsamos control +z
2  stty raw -echo; fg
3 enter, escribimos reset y nuevamente enter
4 escribimos xterm
5 hacemos export TERM=xterm y export SHELL=bash
listo con esto tratamos la TTY
una vez tratada podemos mirar la flag
vamos a /home/rick y ejecutamos ls -lh
listo encontramos la bandera
![[Pasted image 20230902143759.png]]
la otra bandera esta en la carpeta root  pero no tenemos permisos.
![[Pasted image 20230902143940.png]]
lo que vamos a hacer es ver si hay algún binario del que podemos abusar para escalar privilegios.

si hacemos un whoami somos el usuario www-data por lo que tenemos que escalar luego los privilegios. primero buscamos la bandera.