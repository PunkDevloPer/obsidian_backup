### Commits:

#### 1. Definición:
   - Un commit en Git representa un conjunto de cambios realizados en los archivos de un repositorio en un momento específico.
   - Cada commit tiene un mensaje descriptivo que resume los cambios introducidos.

#### 2. Características principales:
   - Sirven como instantáneas del estado del proyecto en un punto dado.
   - Proporcionan un historial detallado de quién realizó qué cambios y cuándo.
   - Son inmutables y permanentes una vez creados.

#### 3. Operaciones comunes:
   - `git commit -m "Mensaje descriptivo"`: Guarda los cambios en el repositorio después de haber agregado los archivos al área de preparación (`git add`).

### Ramas:

#### 1. Definición:
   - Las ramas en Git son líneas de desarrollo independientes que se bifurcan del flujo principal del proyecto (rama `master` por defecto).
   - Permiten trabajar en nuevas funcionalidades, arreglar errores o experimentar sin afectar el código base.

#### 2. Características principales:
   - Cada rama tiene su propio historial de commits, lo que permite cambios separados del resto del proyecto.
   - Facilitan el desarrollo paralelo y colaborativo, ya que varios desarrolladores pueden trabajar en diferentes ramas sin interferir entre sí.
   - Se pueden fusionar (`merge`) con otras ramas para combinar los cambios.

#### 3. Operaciones comunes:
   - `git branch nombre_de_rama`: Crea una nueva rama con el nombre especificado.
   - `git checkout nombre_de_rama`: Cambia a la rama especificada.
   - `git merge nombre_de_rama`: Fusiona los cambios de una rama con la rama actual.

### Etiquetas (tags):

#### 1. Definición:
   - Las etiquetas en Git se utilizan para marcar puntos específicos en el historial del repositorio, como versiones estables o hitos importantes.
   - Sirven como referencias estáticas a ciertos commits.

#### 2. Características principales:
   - Se usan comúnmente para marcar versiones estables o importantes de un proyecto.
   - Permanecen inalterables después de su creación y son útiles para referenciar puntos específicos en el historial.

#### 3. Operaciones comunes:
   - `git tag nombre_etiqueta`: Crea una etiqueta ligera en el commit actual.
   - `git tag -a nombre_etiqueta -m "Mensaje descriptivo"`: Crea una etiqueta anotada con un mensaje descriptivo.
   - `git push origin --tags`: Envía todas las etiquetas al repositorio remoto.