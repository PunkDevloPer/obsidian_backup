`git clone url:` trae un repositorio remoto y lo almacena de forma local

`git remote show:` muestra  el identificador del repositorio remoto que tienes configurado en ese repositorio local. Generalmente es "origin"

`git push :` envia los cambios del repositorio local al repositorio remoto

`git fetch:` es el comando que le dice a tu git local que recupere la última información de los metadatos del original (aunque no hace ninguna transferencia de archivos. Es más bien como comprobar si hay algún cambio disponible).

`git pull:` por otro lado hace eso Y trae (copia) esos cambios del repositorio remoto.

las ramas son formas de hacer cambios sin afectar la rama principal Master

master es la rama principal en donde esta la historia de commits o cambios

una rama es una copia del ultimo commit en otro lado y los cambios  no serán observados en la rama master hasta que se haga un merge

para crear una rama se utiliza 
`Git branch nombre de la rama:` esto nos crea una copia exacta de la rama en la que estamos 
`Git checkoutnombre de la rama:` con este comando cambiamos a la rama que acabamos de crear que es una copia de la rama master, aquí podemos hacer cambios sin afectar directamente la rama master
luego se hace lo mismo que en la rama master para enviar el commit
git add y git commit -m 
