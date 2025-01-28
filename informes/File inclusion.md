
#### Introducción

Este informe se basa en un documento titulado "Los Vengadores" que detalla una serie de metodologías y herramientas utilizadas para llevar a cabo un ejercicio de penetración en una red. Las técnicas descritas abarcan desde el escaneo de red hasta la explotación de vulnerabilidades mediante la obtención de una reverse shell. A continuación, se presenta un resumen de las etapas principales y las herramientas utilizadas.

#### Escaneo de Red

**Nmap:**

- **Comando Utilizado:** `sudo nmap -p- -open -sS -sV -Pn --min-rate 5000 10.0.2.15 -vvv`
- **Resultados:** Se identificaron dos puertos abiertos: 22 (SSH) y 80 (Servidor web).

Es importante agregar la IP de la máquina objetivo al archivo `/etc/hosts` para su correcto funcionamiento, permitiendo acceso a la URL `losvengadores.com`.

#### Fuzzing de Directorios

**Gobuster:**

- **Comando Utilizado:** `gobuster dir -u http://losvengadores.com/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`
- Se exploraron varias rutas, pero ninguna fue útil para el reto específico.

#### Enumeración

**Herramientas Utilizadas:**

- **Burpsuite:** Para interceptar y manipular peticiones web.
- **Sqlmap:** Para identificar y explotar vulnerabilidades SQL.

**Proceso:**

1. Interceptación de la petición de búsqueda en la página inicial utilizando Burpsuite.
2. Exportación de la petición interceptada a un archivo `.req`.
3. Ejecución de Sqlmap para inyectar y extraer datos de la base de datos:
    
    bash
    
    Copiar código
    
    `sqlmap -r losvengadoress.req -p searchVal --batch --level 5 --risk 3 --dump -All --threads 10`
    

#### Explotación

**Autenticación:**

- Usuario: `capitanamerica`
- Contraseña: `adamantium`

**Acceso y Modificación:**

- Navegar a la URL de login y autenticarse con las credenciales obtenidas.
- Modificar la URL eliminando `panelControl.php` para acceder a la funcionalidad de carga de archivos.

**Carga de Reverse Shell:**

1. Modificación del formulario de carga de CV en el HTML:
    
    html
    
    Copiar código
    
    `<div class="col-sm-12 col-md-6">     <form action="CV-upload.php" method="post" enctype="multipart/form-data">         <input id="cv" name="cv" type="file" placeholder="Your CV" />         <button class="btn tm-btn-submit" onclick="upload_cv()">Submit</button>     </form> </div>`
    
2. Creación y carga de un archivo `cv.php` con una reverse shell generada desde `https://www.revshells.com/`.
3. Ejecución de un listener en el atacante:
    
    bash
    
    Copiar código
    
    `nc -nlvp 4444`
    
4. Navegación a la URL donde se subió la reverse shell para activarla.