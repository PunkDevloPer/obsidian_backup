 primero hacemos el scaneo con nmap usando los parametros de siempre.
-p- --open -sS -sC -sV  min -rate 5000 -Pn 10.10.1.150 -oN informe
esperamos  a que se realice el escaneo, seguido a ello vemos que tiene abierto el puerto 80 donde corre un servicio apache 
![[Agente1.PNG]]
ingresamos a la dirección ip desde el navegador http://10.10.1.150 y enseguida vemos un mensaje  donde nos indican que los agentes deben usar su propio nombre clave para acceder al sitio. en este caso la primera pantalla firman como agente R 
![[agente2.PNG]]
una vez hecho lo anterior debemos ir a la terminal y escribir lo siguiente 
curl  -A "R" -L 10.10.44.94
"si no saben para que sirve curl vallan al apartado de linux "
donde va la R se puede ir cambiando y leyendo lo que dice. cada pagina.
si ponemos A sale un mensaje y así sucesivamente, recomiendo que prueben el ABCJ
![[agente3.png]]

una vez obtenida la información tenemos que mirar si el usuario corresponde aun servicio ssh o ftp ya que son los otros servicios que salen al realizar el escaneo
probamos conexion via ftp primero  y luego ssh


2- Fuerza bruta con hydra
 en la terminal usamos el comando hydra -l ip destino  usuario -P diccionario -s  *puerto*
 
* Ejemplo -> hydra 10.10.44.94 ftp -l jianren -P rockyou.txt   -s 21
	* opcional -> instalamos la herramienta binwalk sudo apt-get install binwalk 
una vez dentro del ftp  lo primero que hacemos es ver las carpetas o archivos 
![[agente 5.PNG]]

luego con mget descargamos todo 
![[agente6.PNG]]
una vez descargados los archivos usamos la herramienta que instalamos anteriormente.