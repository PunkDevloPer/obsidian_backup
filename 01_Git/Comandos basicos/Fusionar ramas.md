`git merge` es un comando en Git que se utiliza para fusionar cambios de una rama específica en otra rama, combinando los cambios y uniendo el historial de ambas ramas.

### Uso básico de `git merge`:

#### 1. Fusionar una rama en la rama actual:
   - Para fusionar los cambios de una rama específica en la rama en la que te encuentras actualmente, primero asegúrate de estar en la rama receptora y luego ejecuta:

   ```bash
   git merge nombre_rama_a_fusionar
   ```

   Reemplaza `nombre_rama_a_fusionar` con el nombre de la rama que deseas fusionar en la rama actual.

#### 2. Resolver conflictos de fusión:
   - En algunos casos, es posible que ocurran conflictos durante la fusión, especialmente si hay cambios conflictivos en ambas ramas que estás intentando fusionar. Deberás resolver manualmente estos conflictos.

### Ejemplo de uso de `git merge`:

Supongamos que estás trabajando en una rama llamada `main` y deseas fusionar los cambios de una rama llamada `nueva-funcionalidad` en tu rama actual (`main`). Para hacerlo, primero te asegurarías de estar en la rama `main` y luego ejecutarías:

```bash
git merge nueva-funcionalidad
```

Esto tomará los cambios de la rama `nueva-funcionalidad` y los fusionará en tu rama actual (`main`). Si no hay conflictos, Git intentará realizar la fusión automáticamente. Sin embargo, si hay conflictos, Git te notificará y deberás resolverlos manualmente antes de completar la fusión.
