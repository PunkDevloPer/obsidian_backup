

kivy se puede usar de varias formas pero la mas adecuada es creando una especie de archivo css que realmente es un archivo con extensión .kv

para  hacer funcionar kivy con un archivo .kv que es donde se almacenan los estilos de los widgets  lo mas sencillo es definir build(self): que basicamente obliga a kivy a buscar la clase principal y obtener el archiv .kv 

 ahora, lo mas importante es que puedo crear una clase principal y dentro de esa clase meter varios metodos a los cuales puedo acceder mediante el nombre de la clase.
 por ejemplo 
```
class RootWidget(BoxLayout):  

    def say_hello(self):

        print("¡Hola desde Kivy!")

    def slider(self ):

        print("slider")
 
```
 en mi clase rootwidget tengo  dos metodos say_hello y slider en este caso son Boxlayout
 y para importarlas en mi archivo .kv debo 