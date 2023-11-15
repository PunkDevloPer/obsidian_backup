Para realizar el reconocimiento vamos a utilizar 2 herramientas fundamentales Nmap para escaneo de puertos y Gobuster para Fuzzing
Empezamos la el reconocimiento de la maquina usando Nmap
nmap -p- --open -sS -sC -sV --min-rate 222 -Pn 10.10.11.214 -oN Escaneo
Esperamos a que se ejecute y nos fijamos en los servicios que va a encontrar para proceder a buscar una vulnerabilidad.
generalmente si tienen un puerto 80 abierto, se puede ver si existe algún sitio web
![[Pasted image 20230830160520.png]]
aquí podemos observar 3 servicios 
-->FTP
-->SSH 
-->HTTP

