
![[Pasted image 20231003154907.png]]
en la linea 14 vemos que estan automatizando un script con bash pero no tenemos permisos de edicion, tenemos que buscar alguna forma de poder subir un script con una reverse shell.
si vamos a la carpeta de los host para ver si hay algun servidor local encontramos lo siguiente
![[Pasted image 20231003155230.png]]
el script lo estan obteniendo desde el host overpass.thm por lo que debemos editar la direccion ip del host para que busque el script en nuestro equipo cuando se ejecute la tarea y se envie el script malicioso.
primero hacemos un nano en /etc/host y editamos el host de overpass.thm
luego segun la ruta de donde se va a capturar el script debemos replicarla en este caso en downloads/src/buildscript.sh 
esta ruta debe ser replicada en nuestra maquina atacante  y alli montar el servidor python
en mi caso la tengo en CTF/Tryhackme-> aqui monto el servidor python y creo la carpeta downloads/src/buldscrpt.sh 
![[Pasted image 20231003164256.png]]
montamos el servidor y tiene que aparecer un codigo 200 que indica que el archivo fue enviado 
![[Pasted image 20231003164347.png]]
en otra ventana ponemos en escucha al puerto que pusimos en el script
![[Pasted image 20231003164427.png]]
 listo con esto tendriamos nuestra maquina totalmente hackeada ya somos root
 ![[Pasted image 20231003164656.png]]