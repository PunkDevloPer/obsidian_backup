El comando `git branch` en Git se utiliza para listar, crear o borrar ramas en un repositorio. Aquí tienes una guía sobre cómo usar este comando para realizar diferentes operaciones relacionadas con las ramas:

### Funciones principales de `git branch`:

#### 1. Listar ramas:
   - Para listar todas las ramas en tu repositorio (tanto locales como remotas), simplemente ejecuta:

   ```bash
   git branch
   ```

   Esto mostrará un listado de todas las ramas presentes en tu repositorio local y resaltará la rama en la que te encuentras actualmente (marcada con `*`).

#### 2. Crear una nueva rama:
   - Si deseas crear una nueva rama a partir de la rama actual, usa:

   ```bash
   git branch nombre_nueva_rama
   ```

   Reemplaza `nombre_nueva_rama` con el nombre que desees para tu nueva rama.

#### 3. Cambiar a una rama existente:
   - Para cambiar a una rama existente, utiliza el comando `git checkout` seguido del nombre de la rama:

   ```bash
   git checkout nombre_rama_existente
   ```

   Esto te cambiará a la rama especificada.

#### 4. Eliminar una rama:
   - Para borrar una rama específica que ya no necesitas:

   ```bash
   git branch -d nombre_rama_a_borrar
   ```

   Este comando eliminará la rama si los cambios en esa rama ya han sido fusionados en otra parte del proyecto. Si deseas forzar la eliminación sin tener en cuenta la fusión, puedes usar `-D` en lugar de `-d`.

### Ejemplo de uso de `git branch`:

Supongamos que quieres:

- Ver todas las ramas en tu repositorio:
  ```bash
  git branch
  ```

- Crear una nueva rama llamada `nueva-caracteristica`:
  ```bash
  git branch nueva-caracteristica
  ```

- Cambiar a la nueva rama que acabas de crear:
  ```bash
  git checkout nueva-caracteristica
  ```

- Eliminar una rama llamada `rama-antigua`:
  ```bash
  git branch -d rama-antigua
  ```

