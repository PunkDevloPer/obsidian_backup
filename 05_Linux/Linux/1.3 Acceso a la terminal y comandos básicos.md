para dividir comandos muy largos se usa \  para dar un salto de linea en la terminal
 para ejecutar comandos simultaneos se usa ; por ejemplo clear ; ls el punto y coma concatena los comandos
 El operador &&:and concatena dos comandos pero esta condicionado a que se ejecute el primer comando. 
  EJEMPLO:
  * clear && ls-> limpia la consola y ejecuta ls mientras el comando clear se cumpla el comando ls tambien se cumple.
  * mkdir carpeta && cd carpeta -> crea el directorio carpeta e ingresa  al mismo mientras mkdir se cumpla cd se cumple
el comando pipe || es parecido al comando && pero este ejecuta los comandos independiente mente de si uno se cumple o no.
EJEMPLO:

clear || ls -> limpia la consola y ejecuta el listado de directorios, no importa si clear no se cumple , ls se cumplirá

<h1>ATAJOS DEL SHELL</h1>
`Ctrl + A` Ir al principio de la linea en la que se esta escribiendo.
`Ctrl + E` Ir al final de la linea en la que se esta escribiendo.
`Ctrl + L` Borra la pantalla, similar al comando `clear`
`Ctrl + U` Borra la linea anterior a la posición del cursor. Si esta al final de la linea, borra toda la linea.
`Ctrl + H` Borra el carácter anterior a la posición del cursos. Igual que retroceso.
`Ctrl + R` Permite buscar entre los comandos utilizados anteriormente.
`Ctrl + C` Interrumpe la ejecución de un programa.
`Ctrl + D` Cierra la shell actual.
`Ctrl + W` Corta la palabra anterior a la posición cursor.
`Ctrl + K` Corta la linea siguiente a la posición del cursor.
`Ctrl + T` Intercambia los dos últimos caracteres anteriores a la posición del cursor.
`Esc + T` Intercambia las dos últimas palabras anteriores a la posición del cursor.
`Alt + .` o `!$` Referencia el último argumento del comando anterior.
`Alt + F` Avanza el cursor una palabra en la linea actual.
`Alt + B` Retrocede el cursor una palabra en la linea actual.
`Alt + l/u` Convierte la palabra en mayúsculas o minúsculas.
`Tab` Autocompleta nombres de archivos y carpetas.
<h1>CREAR ALIAS DE COMANDOS LINUX</h1>
para crear un alias se usa el comando alias  el nombre ='Comandos'
ejemplo: alias clist='clear ; ls'
ahora clist es un alias de clear ; ls que básicamente limpia la consola y luego lista los directorios.
para ver los comandos con "alias " se usa el comando alias sin argumentos.
para eliminar un alias se utiliza  unalias + nombre dado al comando ejemplo unalias clist elimina el comando clist




1. para crear un hash con md5sum se usa el comando echo -n palabra a hashear | md5sum
2. para ver un hash en base 64 se usa echo "hash del base64" | base64 --decode
3.  para crackear contraseñas con john se usa el comando john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-MD5 hash 
	 -> donde hash es el archivo que contiene el hash
		 -> format=raw-MD5 es el formato, aqui puede cambiar.
 