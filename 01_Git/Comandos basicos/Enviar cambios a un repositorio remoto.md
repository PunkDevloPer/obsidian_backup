`git push` es un comando en Git que se utiliza para enviar los commits realizados en tu repositorio local a un repositorio remoto, como GitHub, GitLab o Bitbucket. Este comando sincroniza los cambios locales con el repositorio remoto, actualizando el historial del repositorio remoto con tus últimos commits.

### Uso básico de `git push`:

#### 1. Empujar commits a un repositorio remoto:
   - Después de realizar commits en tu repositorio local, puedes usar `git push` para enviar esos commits al repositorio remoto.

   ```bash
   git push nombre_remoto nombre_rama
   ```

   Reemplaza `nombre_remoto` con el nombre del repositorio remoto (por ejemplo, `origin` por defecto en GitHub) y `nombre_rama` con el nombre de la rama en la que estás trabajando.

#### 2. Empujar la rama actual al repositorio remoto:
   - Si estás trabajando en una rama local y deseas enviar los commits de esa rama al repositorio remoto con el mismo nombre:

   ```bash
   git push nombre_remoto nombre_rama_local
   ```

   Esto enviará la rama local especificada al repositorio remoto con el mismo nombre.

### Ejemplo de uso de `git push`:

Supongamos que estás trabajando en una rama llamada `main` y quieres enviar los commits de esa rama al repositorio remoto llamado `origin` (el repositorio remoto por defecto en GitHub). Para ello, ejecutarías:

```bash
git push origin main
```

Esto enviará los commits de la rama `main` de tu repositorio local al repositorio remoto `origin` en GitHub, actualizando la rama `main` en el repositorio remoto con tus cambios.

