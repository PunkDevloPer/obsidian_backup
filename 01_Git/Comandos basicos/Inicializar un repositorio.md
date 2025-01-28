`git init` es un comando fundamental en Git que se utiliza para iniciar un repositorio nuevo o convertir un directorio existente en un repositorio Git vacío. Este comando crea una nueva carpeta `.git` en el directorio raíz del proyecto, donde se almacenará toda la información relacionada con el control de versiones.

### Funcionalidades principales de `git init`:

#### 1. Iniciar un nuevo repositorio:
   - Al ejecutar `git init` en un directorio, se crea un nuevo repositorio Git en esa ubicación.
   - Este comando prepara el entorno para comenzar a rastrear cambios en archivos y carpetas.

#### 2. Crear un repositorio vacío:
   - Crea una estructura base para el control de versiones, pero inicialmente no hay archivos rastreados ni commits realizados.

#### 3. Configurar un repositorio existente:
   - Si tienes un proyecto existente que aún no es un repositorio Git, puedes usar `git init` para comenzar a rastrear los cambios de manera versionada.

### Pasos comunes para usar `git init`:

#### 1. Crear un nuevo repositorio:
   - Abre la terminal o línea de comandos en la carpeta de tu proyecto.
   - Ejecuta `git init`.

#### 2. Rastrear cambios en archivos:
   - Una vez iniciado el repositorio, puedes comenzar a rastrear cambios en archivos específicos usando `git add` y luego confirmarlos con `git commit`.

#### 3. Configuración inicial:
   - Después de ejecutar `git init`, es común configurar ciertas opciones, como el nombre de usuario y correo electrónico, utilizando `git config`.

### Ejemplo de uso de `git init`:

```bash
# Inicia un nuevo repositorio en el directorio actual
git init
```

