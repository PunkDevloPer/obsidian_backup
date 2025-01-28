1. **Introducción**
	Evaluar la seguridad de la empresa para poder establecer hojas de respuesta frente a incidentes.
 2. **Alcances**
	esta prueba pone en evidencia lo relativamente inseguro que puede ser un entorno tanto empresarial como personal, además de resaltar las posibles medidas correctivas para subsanar la vulnerabilidad .
3. Problemas
   los problemas mas comunes durante  la ejecución del reto fueron  colapsos de el sistema ya que al requerir recursos adicionales para la virtualización se entraba en conflicto con los recursos del propio sistema HOST.

	otro problema común fue que al ejecutar el servidor local, se quedara a la escucha y no sucediera nada.
   
4. S**oluciones O Recomendaciones**
   La solución al primer problema en donde se colapsaba el sistema fue asignar recursos adicionales a la maquina victima para poder trabajar de forma normal.
   el segundo problema se soluciono asignando ambas maquinas a una red Nat, luego iniciar primero la maquina con el sistema victima y luego la maquina con el sistema atacante.
   como recomendación general las maquinas virtualizadas consumen muchos recursos por lo que entre 1 y 1.5 GB de memoria RAM asignada  en cada maquina debería ser suficiente.
   
INFORME TECNICO 

Introducción
lo primero que aremos será analizar el trafico de red entrante y saliente de nuestras maquinas. con lo que vamos a interceptar paquetes de red, luego con la ayuda de un servidor local vamos a recibir cierta información que nos va a revelar datos sensibles

las herramientas que vamos a utilizar serán:
**Kali Linux:** esta herramienta va a ser utilizada por que es una distro especializada en ciberseguridad y cuenta con las herramientas necesarias para realizar la prueba.

**Wireshark:** es una potente herramienta que nos va a permitir rastrear el trafico en la red, además viene incluida por defecto en Kali Linux

**Netcat:**  en este caso la función  de Netcat va a ser poner un puerto en escucha de una petición y en esa petición puede o no venir información relevante.  

***Fase 1 Análisis de paquetes***
en esta fase lo primero será rastrear paquetes en la red, entonces lo primero en mi caso es abrir una consola en modo root con las teclas ctrl +alt +mayus+T![[Pasted image 20240415091930.png]]
luego simplemente escribimos wireshark
una vez se abre, tenemos la interfaz principal del programa por lo que en mi caso voy a escoger la red eth0
![[Pasted image 20240415092041.png]]ahora simplemente esperamos a que wireshark rastre los paquetes que pasan por nuestra red
![[Pasted image 20240415092515.png]]
en este caso tenemos un paquete en color rojo  y uno en color gris
esto indica lo siguiente:
![[Pasted image 20240415092713.png]]
hay una solicitud de conexión en el puerto 3333 desde el puerto 6666
ahora que ya sabemos esto, vamos a poner el puerto en escucha  para ello utilizaremos nc-nlvp 3333

***Fase 2 explotación de la vulnerabilidad***
![[Pasted image 20240415092941.png]]
aquí ya hay una fuga importante de información por que esta indicando que el puerto 4444 es el puerto del panel de administración.
hacemos lo siguiente.. 
![[Pasted image 20240415093410.png]]
nos loguemos como administradores nuevamente y hacemos una conexión a la ip de la maquina que nos envió el paquete. 
![[Pasted image 20240415093506.png]]
aquí por lo general en Linux para pedir ayuda o información se usa h o help  por lo que hay mas información. filtrada. en este caso hay dos acciones que posiblemente sean peligrosas. añadir usuarios, o ver la contraseña.
y finalmente la contraseña esta en texto plano
![[Pasted image 20240415093829.png]]
*** Fase 3: tomando control del servidor ***
vamos a la maquina victima, y por defecto los usuarios comunes son administrador, root o admin.
![[Pasted image 20240415094401.png]]
aquí se realizo el intento de logueo con 3 usuarios de los cuales 1 resulto exitoso y ya estoy dentro del servidor.
***Recomendaciones para la corrección de errores**
1. no utilizar directamente el usuario root, pues hay que tener como norma general la ley del minimo privilegio, entre menos privilegios tenga un usuario mas dificil es para el atacante escalar en la infraestructura.
2. cifrar o encriptar las contraseñas, en este caso la contraseña se encontró en un texto plano lo que facilito el ataque.
3. alguna forma de autenticar que la maquina a la que se le pide la solicitud de conexión este en una lista blanca de lo contrario el servidor debe rechazar la conexión, tanto en el puerto 3333 como en el 4444
4. 
