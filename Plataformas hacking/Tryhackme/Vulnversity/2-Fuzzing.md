primero verificamos si esta instalado gobuster, si no esta instalado entonces corremos 

sudo apt install gobuster -y
una vez instalado vamos a usar una lista de palabras que debemos meter en el directorio

/usr/share/wordlist
primero bajamos el documento common.txt del siguiente repo :
https://github.com/v0re/dirb/blob/master/wordlists/common.txt
lo metemos en la ruta que les dije debe quedar asi
![[Pasted image 20230830164009.png]]
ahora vamos a realizar el analisis de fuerza bruta: 
![[Pasted image 20230830163210.png]]
fíjense que se pone -w (wordlists) y se da la ruta donde metimos el common.txt y usamos -q (quiet) para que solo nos muestre las rutas que nos interesan.

aquí gobuster nos encontró 5 rutas
hay que mirar cadad ruta puede tener alguna vulnerabilidad o forma de ser explotada.