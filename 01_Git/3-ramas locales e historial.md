
`git branch:`Se utiliza para crear una rama dependiendo de donde se encuentre el HEAD del repositorio también para ver cuantas ramas existen actualmente en el repositorio local
`Git checkout nombre de la rama:` con este comando cambiamos a la rama que acabamos de crear que es una copia de la rama master, aquí podemos hacer cambios sin afectar directamente la rama master
luego se hace lo mismo que en la rama master para enviar el commit
git add y git commit -m "comentario"
<h1>Historial </h1>
`git rm -cached archivo:` significa que esta en memoria ram que aun no esta guardado en la base de datos, toca repetir git add 

`git status:` nos da la información histórica de los cambios que se han realizado

`git show:` muestra todos los archivos que se han cambiado 

`git reset id del cambio --hard :` devuelve todo a un estado inicial 

`git reset  id del cambio --soft:` devuelve todo a la versión anterior 
pero lo que tengamos en staging se queda allí hasta que realicemos un commit

`git log --stat :` muestra los cambios y la cantidad de bits modificados así como el identificador del commit  que nos sirve para hacer un reset en caso de ser necesario.

`git checkout :` nos muestra el archivo original en su primera versión copiando el id que nos da el id del primer commit.
`git merge:` Este comando nos sirve para fusionar una rama secundaria con la rama Master 




