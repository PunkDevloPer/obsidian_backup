Aquí  encontramos la ruta que nos permite subir archivos.
![[Pasted image 20230830164300.png]]
ahora lo que tenemos que hacer es con la versión del servicio buscar en la web algún script para poder tomar acceso al servidor.
la versión del servicio http es la 2.4.18 

en esta web hay bastantes recursos para Reverseshell
https://www.revshells.com/
yo estoy usando la que dice php pentestMonkey
Me he saltado la parte del burpsuite por que ya sabia que la extensión es phtml 

Retomando lo anterior ahora nos vamos a la ruta 
![[Pasted image 20230830170448.png]]
y allí debe estar el archivo que subimos.
![[Pasted image 20230830170513.png]]

ahora lo que debemos hacer es montar un puerto en escucha con la terminal.
si usaron la pagina que les dije debe ser algo como esto 
![[Pasted image 20230830170617.png]]

cuando lo ejecutemos se pondrá en escucha
![[Pasted image 20230830170724.png]]
y ahora debemos "abrir " el que esta en el servidor para que se conecte a nuestra terminal.
una vez que abrimos el archivo la pagina se queda cargando pero si revisamos la shell 
bumm ya tenemos acceso al servidor.
![[Pasted image 20230830171836.png]]ahora debemos hacer el tratamiento de la TTY
primero ponemos el comando
*script /dev/null -c bash
luego ctrl + Z y ejecutamos 
stty raw -echo; fg damos enter y ponemos 
reset  y luego xterm
luego hacemos 
xport TERM=xterm y un
Xport SHELL=Bash

![[Pasted image 20230830173129.png]]
![[Pasted image 20230830173208.png]]
aqui ya hemos tomado la maquina pero estamos como un usuario invitado.
www-data
![[Pasted image 20230830173421.png]]
ahora necesitamos escalar los privilegios dentro de la maquina.