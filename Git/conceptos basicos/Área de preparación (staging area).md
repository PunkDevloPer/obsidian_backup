### ¿Qué es el área de preparación (staging area)?

El área de preparación es un paso intermedio entre los cambios que realizas en los archivos de tu proyecto y la confirmación de esos cambios en el repositorio Git. Funciona como un espacio donde puedes seleccionar y preparar los cambios específicos que deseas incluir en tu próximo commit.

### Funciones principales del área de preparación:

#### 1. Selección de cambios:
   - Permite elegir qué modificaciones de archivos incluir en el próximo commit. No todos los cambios realizados a los archivos necesariamente se incluyen en un commit.

#### 2. Revisión antes de confirmar:
   - Proporciona la oportunidad de revisar los cambios antes de confirmarlos definitivamente en el historial del repositorio.

#### 3. Facilita commits modulares:
   - Permite dividir tus cambios en commits más pequeños y lógicos, lo que mejora la claridad y la trazabilidad del historial.

### Proceso de uso del área de preparación:

#### 1. Modificación de archivos:
   - Realizas cambios en los archivos de tu proyecto.

#### 2. Agregar cambios al área de preparación:
   - Utilizas el comando `git add` para seleccionar los cambios que quieres incluir en el próximo commit.
   - `git add nombre_archivo`: Agrega un archivo específico al área de preparación.
   - `git add .`: Agrega todos los archivos modificados al área de preparación.

#### 3. Verificación de cambios en el área de preparación:
   - Puedes usar `git status` para ver los archivos que están en el área de preparación y los que no lo están.

#### 4. Confirmación de cambios en un commit:
   - Luego de añadir los cambios deseados al área de preparación, puedes realizar un commit con `git commit` para guardar esos cambios de forma permanente en el repositorio.

### Ventajas del área de preparación:

- **Control granular:** Te permite seleccionar cambios específicos en archivos para incluirlos en commits individuales.
- **Revisión antes de confirmar:** Brinda una oportunidad para verificar y revisar los cambios antes de que se conviertan en parte del historial del repositorio.
- **Commit más estructurados:** Facilita la creación de commits más lógicos y enfocados en funcionalidades específicas.

