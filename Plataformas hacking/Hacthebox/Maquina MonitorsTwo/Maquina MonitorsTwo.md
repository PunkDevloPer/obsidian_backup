primero hacemos un análisis de puertos con ayuda de nmap
aquí vemos que existe en el puerto 80 un servidor  y el puerto 22 una conexion ssh

![[image 1.png]]
una vez obtenidos los servicios en este caso voy a explotar el servicio http y luego entraremos a través del ssh para capturar las banderas.
una vez obtenida la vulnerabilidad vemos que el servicio es un ngix 1.18.0 lo que vamos a hacer es buscar y utilizar el siguiente repositorio:
https://github.com/FredBrave/CVE-2022-46169-CACTI-1.2.22
 se descarga el repositorio y hacemos lo siguiente.
 1 ponemos en escucha el puerto 443 con el comando nc -lvnp 443
 2 en otra ventana ejecutamos el script del repositorio que acabamos de descargar  con el siguiente comando : 
![[image 10.png]]
 una vez ejecutado  saldrá esto : 
 ![[image 11.png]]
ya estamos dentro de la maquina , ahora tenemos que hacer el tratamiento de la tty para que la terminal funcione como debe.
![[image 12.png]]
así tratamos la TTY
primero dentro de la maquina ponemos el comando script /dev/null -c bash
luego ctrl + Z y ejecutamos stty raw -echo;fg y ponemos reset xterm
![[image 13.png]]
una vez hagamos esto ya tenemos activada la consola interactiva
ahora lo que debemos hacer es buscar la forma de poder entrar al ssh.
primero vamos a buscar  la ruta /var/www/html/include y  hacemos Cat al archivo config.php
una vez dentro del archivo vemos lo siguiente 
![[image 14.png]]
el usuario es root y la contraseña igual.
ejecutamos lo siguiente mysql -u root -h db -p -e 'SELECT' * FROM cacti.user_auth;' 
con lo cual nos pedira la contraseña que es root
![[image 15.png]]
nos sale lo siguiente  en este caso vamos a tomar el usuario marcus copiamos la contraseña y la metemos en un txt con nano.![[image 16.png]]
ahora ejecutamos jhon the riper para descubrir el password
![[image 17.png]]
aquí esta la contraseña. ahora vamos por la bandera a través del ssh.
aqui ya tenemos acceso ssh ![[image 2.png]]
![[image 3.png]]
aquí tenemos la primera bandera
ahora vamos por la segunda.
buscamos la versión de Docker  con Docker -v lo cual arroja la version 20.10.5 
ahora entramos al repositorio 
https://github.com/UncleJ4ck/CVE-2021-41091
ejecutamos el comando findmnt

vamos al que dice merged 
![[image 5.png]] copiamos la ruta  y ponemos ls -l bin/bash 
![[image 7.png]]
importante asegurarse de que salga el cuadro rojo 
luego bin/bash -p y luego ponemos id
![[image 6.png]]
la bandera es root.txt asegurarse de que al ejecutar /bin/bash -p cambie a bash-5.1# ya que sin esto no 
funciona
![[image 9.png]]
 