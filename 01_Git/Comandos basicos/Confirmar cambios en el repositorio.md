`git commit` es un comando fundamental en Git que se utiliza para confirmar los cambios preparados en el área de preparación (staging area) en un nuevo commit en el historial del repositorio.

### Uso básico de `git commit`:

#### 1. Confirmar cambios en el área de preparación:
   - Después de agregar los cambios que deseas incluir en el próximo commit utilizando `git add`, puedes usar `git commit` para guardar esos cambios en el repositorio.

   ```bash
   git commit
   ```

   Al ejecutar este comando, se abrirá un editor de texto (como Vim o Nano) donde podrás escribir un mensaje descriptivo que explique los cambios realizados. Esto es importante para tener un historial claro y comprensible.

#### 2. Agregar un mensaje directamente en el comando:
   - También puedes agregar un mensaje directamente en el comando utilizando la bandera `-m` seguida del mensaje entre comillas:

   ```bash
   git commit -m "Mensaje descriptivo de los cambios"
   ```

   Esto permite especificar un mensaje de commit de forma rápida y directa en la misma línea de comando.

### Ejemplo de uso de `git commit`:

Después de agregar los cambios deseados al área de preparación con `git add`, ejecutas `git commit` para confirmarlos en un commit:

```bash
git commit
```

Esto abrirá un editor de texto donde puedes escribir un mensaje descriptivo que explique los cambios realizados. Una vez que guardes y cierres el editor, el commit quedará registrado en el historial del repositorio con el mensaje proporcionado.

Si prefieres agregar un mensaje directamente en el comando, puedes usar la opción `-m`:

```bash
git commit -m "Mensaje descriptivo de los cambios"
```

Esto confirmará los cambios con el mensaje proporcionado sin necesidad de abrir un editor de texto.

Recuerda que cada commit debe tener un mensaje significativo que describa los cambios realizados para mantener un historial claro y comprensible del proyecto.