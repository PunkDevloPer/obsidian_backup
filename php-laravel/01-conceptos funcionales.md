para que una ruta en laravel funcione de forma correcta debe ser creada en el apartado routes en el archivo web.php
 las rutas se leen de manera vertical  o sea de arriba a abajo por lo tanto el orden en el que se creen puede alterar el resultado de la vista 
 
Route::get('apuntes', function () {

    return "Bienvenido a la pagina de apuntes";

});
esta es la estructura general de las rutas.
donde "apuntes" es el nombre de la ruta.

<h1>Controladores</h1>

los controladores son los que manejan los datos que retorna el modelo para pasarlos a la vista.
los controladores se crean en la carpeta
->app ->http ->controllers
para crear un controlador se escribe lo siguiente
->php artisan make:controller HomeController

<h1>Uso de los Controladores</h1>
para usar los controladores debemos "importarlos" a  el archivo web.php haciendo uso de la palabra reservada "use" seguido del namespace del controlador ejemplo:
->use App\\Http\\Controllers\\HomeController
luego lo que hacemos es simplemente en el mismo archivo web.php usar el controlador
Route::get('apuntes', HomeController::class});
y lo que devolvia el Route lo ponemos en el HomeController.php
 el cual es algo asi :
<?php
namespace App\http\Controllers;
use illuminate\http\Request;
class Homecontroller extends controller
{
	public function __invoke()
	{
		return "Bienvenido a la web principal";
	}
};
?>

<h1> Metodos de controlador</h1>
para que el controaldor funcione adecuadamente luego de hacer el paso anterior, lo que se debe realizar es crear los métodos que administran las rutas
<?php
namespace App\Http\Controllers;
use App\Http\Controllers\Controller;
use Illuminate\Http\Request;
class CursoController extends Controller
{
    public function index()
    {
    return "Bienvenido al index de los cursos";
    }
    
    public function create(){
    return "Bienvenido a crear cursos";}
    
    public function show(){
    return "Bienvenido a ver cursos";
    }
}

?>

luego en el archivo web.php se pasan esos metodos dentro de la ruta
	-> Route::get('cursos',[CursoController::class, 'index'])
	-> Route::get('cursos',[CursoController::class, 'create'])
	-> Route::get('cursos',[CursoController::class, 'show'])
y en los metodos ponemos lo que queremos que la ruta devuelva 
<h1>Vistas</h1>
las vistas son las que muestran la información html estas vistas se pueden administrar en la carpeta 
resources -> views
dentro de la carpeta views se crean archivos php de acuerdo a los metodos.
por ejemplo hay un método index entonces en el view debe ir index.php, esta regla se aplica mas por buenas practicas y para saber que modelo-> vista -> controlador corresponde a cada  método
entonces corresponde crear tres archivos
* index.php
* show.php
* create.php

para que las vistas sean tomadas hay que agregarlas al controlador en el  metodo   correspondiente hay que invocar el metodo view() si esta en una carpeta entonces 
view(cursos.index)
->return view(index)
->return view(show)
->return view(create)

<h1>Sistema de plantillas Blade</h1>
Blade es un sistema de plantillas que facilita el uso de código html, lo primero es crear una carpeta llamada layouts dentro de la carpeta views, ahora dentro de layouts creamos el archivo plantilla.blade.php
la estructura de archivos es algo como 
|--views
		|--layouts
				|--plantilla.blade.php
				|--index.blade.php

así podemos utilizar el codigo html "global" una sola vez como por ejemplo la barra de navegacion, el menu algunos iconos, Etc

para establecer las etiquetas que queremos que sean dinámicas se hace con @yield('title')
y en el body seria @yield('content')

ahora para que esto funcione lo importamos en las vistas
 con el siguiente argumento 
 -> @extends(layouts.plantilla)
  lo que esta dentro del paréntesis es realmente la ruta donde esta la plantilla.
  para el titulo seria ->@section('title', 'Home')
  en donde title es el nombre del yield y el home es el titulo que va a adquirir cada plantilla por lo que puede cambiar, por ejemplo @section('title', 'Cursos') o @section('title', 'Plantillas')






