ahora podemos buscar si existe algun script o algo que se pueda explotar.
buscando en la web aparece esto ![[Pasted image 20230911174351.png ]]
ósea que se pueden cargar archivos mediante algún panel
vamos al apartado de publicidad y creamos un archivo nuevo 
![[Pasted image 20230911175513.png ]]
yo utilice esta web que se llama shell generator. 
use el de php pentestMonkey
![[Pasted image 20230911175447.png]]
ahora hacemos un nc -nlvp 443 como pone en la web
ahora vamos a la ruta anterior donde encontramos la base de datos y buscamos el apartado de publicidad![[Pasted image 20230911175807.png]]

ejecutamos el payload
ya tenemos acceso 
![[Pasted image 20230911175941.png]]

ahora debemos tratar la TTY primero ponemos el comando
*script /dev/null -c bash
luego ctrl + Z y ejecutamos 
stty raw -echo; fg damos enter y ponemos 
reset  y luego xterm
luego hacemos 
xport TERM=xterm y un
Xport SHELL=Bash
