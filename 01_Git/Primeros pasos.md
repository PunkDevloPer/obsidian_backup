
Git es un sistema de control de versiones para guardar los cambios en los proyectos que se deben modificar a medida que pasa el tiempo.
es de gran ayuda ya que muestra un registro de los cambios que se han hecho a lo largo del proyecto
Git tiene un funcionamiento particular, en cuanto a los archivos cuando un archivo es rastreable esta en modo Tracked si no es rastreable esta en modo Untracked, por lo pronto con la siguiente explicación es suficiente para entender el concepto 
 
`tracked y untracked`

cuando aun no se ha dado git add el archivo esta en modo untrack y cuando se hace el hace el git add  entra en estado tracked y entra a staging (en la memoria)->lugar temporal antes de enviar cambios al repositorio 
cuando se hace el commit -m es cuando se confirman los cambios y se hace trackead en el staging y pasan a ser almacenados en el repositorio y se les asigna un identificador, es aquí en donde se ven reflejados los cambios que se realizan sobre cada archivo dentro del repositorio.

cada commit es una versión de cambios hacia el repositorio.

la rama Main es la rama "definitiva" del proyecto por lo que esta rama no va a sufrir modificaciones directas si no que vamos a hacer versiones modificadas y cuando estemos seguros podremos agregar los cambios a la rama principal "Main"