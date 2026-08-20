# Guía del estudiante: GitHub, Git y JupyterLab

## Objetivo

En esta guía aprenderás a:

1. Instalar Git para trabajar con repositorios.
2. Clonar el repositorio del curso.
3. Instalar y abrir JupyterLab.
4. Guardar tus avances con commits y enviarlos a GitHub.

Repositorio del curso: [github.com/xkantun/curso-analisis-datos](https://github.com/xkantun/curso-analisis-datos)

## 1. Antes de comenzar: Git y GitHub no son lo mismo

- **Git** es el programa que guarda el historial de cambios en tu computadora.
- **GitHub** es el sitio donde se alojan repositorios y se comparten los cambios.
- **JupyterLab** es el entorno que usaremos para abrir y ejecutar notebooks de Python.

Por eso, normalmente instalamos **Git** en la computadora y usamos **GitHub** desde el navegador. GitHub explica esta diferencia y el uso de repositorios remotos en su documentación oficial: [About remote repositories](https://docs.github.com/en/get-started/git-basics/about-remote-repositories).

Necesitarás:

- Una cuenta de GitHub.
- Git.
- Python 3.
- Conexión a Internet para descargar el repositorio y publicar tus cambios.

## 2. Instalar Git

### Windows

Instala [Git for Windows](https://git-scm.com/install/windows). También puedes abrir PowerShell y ejecutar:

```powershell
winget install --id Git.Git -e --source winget
```

Después abre **Git Bash**, PowerShell o una nueva ventana de Terminal y comprueba la instalación:

```bash
git --version
```

### macOS

Puedes instalar las herramientas de línea de comandos de Apple:

```bash
xcode-select --install
```

O, si utilizas Homebrew:

```bash
brew install git
```

Comprueba la instalación:

```bash
git --version
```

Más información: [Instalar Git en macOS](https://git-scm.com/install/mac).

### Linux (Ubuntu o Debian)

```bash
sudo apt update
sudo apt install git python3 python3-venv
git --version
```

Consulta otras opciones en la página oficial de [instalación de Git](https://git-scm.com/install/).

### Opción gráfica: GitHub Desktop

Si prefieres una interfaz gráfica, puedes instalar [GitHub Desktop](https://desktop.github.com/). Aun así, conviene aprender los comandos básicos porque los usaremos durante el curso.

## 3. Configurar Git una sola vez

Abre una terminal y escribe tu nombre y el correo asociado a tu cuenta de GitHub:

```bash
git config --global user.name "Nombre Apellido"
git config --global user.email "tu-correo@example.com"
```

Para revisar la configuración:

```bash
git config --global --list
```

El nombre y el correo quedan asociados a los commits que hagas. No uses el correo ni la cuenta de otra persona.

## 4. Obtener el repositorio del curso

Todos los alumnos deben trabajar desde un **fork**. Un fork es una copia del repositorio en tu propia cuenta de GitHub. De esta forma podrás hacer commits y `push` sin modificar directamente el repositorio del profesor.

### 4.1 Crear un fork — paso obligatorio

1. Abre el [repositorio del curso](https://github.com/xkantun/curso-analisis-datos).
2. Haz clic en **Fork**.
3. Elige tu cuenta de GitHub y confirma la creación.
4. Abre el repositorio que se creó en tu cuenta.
5. Pulsa **Code → HTTPS → Copy** y copia la URL de tu fork.

### 4.2 Clonar desde la terminal

Primero cambia a la carpeta donde quieres guardar el curso. Por ejemplo:

```bash
cd Documents
```

Después clona tu fork usando la URL que copiaste:

```bash
git clone https://github.com/TU_USUARIO/curso-analisis-datos.git
cd curso-analisis-datos
```

En el comando anterior, reemplaza `TU_USUARIO` por tu nombre de usuario real de GitHub.

Comprueba que estás dentro del repositorio:

```bash
git remote -v
git status
```

La salida de `git remote -v` debe mostrar la dirección de tu fork, y `git status` debe indicar que estás en un repositorio Git.

Para poder recibir actualizaciones del repositorio del curso, registra también el repositorio original como `upstream`:

```bash
git remote add upstream https://github.com/xkantun/curso-analisis-datos.git
git remote -v
```

Deberás ver dos remotos:

- `origin`: tu fork personal; aquí publicarás tus commits con `git push origin main`.
- `upstream`: el repositorio del curso; de aquí recibirás actualizaciones con `git pull upstream main`.

La documentación oficial describe este flujo como **Code → HTTPS → copiar URL → `git clone`**: [Clonar un repositorio](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository).

## 5. Instalar Python y JupyterLab

Si todavía no tienes Python 3, instálalo desde [python.org](https://www.python.org/downloads/) y durante la instalación de Windows marca la opción **Add Python to PATH**.

### macOS y Linux

Desde la carpeta del repositorio:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

### Windows PowerShell

Desde la carpeta del repositorio:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

El archivo `requirements.txt` instala las bibliotecas usadas en el curso. Si necesitas instalar JupyterLab manualmente, el comando oficial es:

```bash
python -m pip install jupyterlab
jupyter lab
```

Consulta [Installing JupyterLab](https://jupyter.org/install) para más opciones.

Al ejecutar `jupyter lab`, normalmente se abrirá una pestaña del navegador con una dirección parecida a `http://localhost:8888/lab`. La terminal debe permanecer abierta mientras uses JupyterLab. Para cerrarlo, vuelve a la terminal y presiona `Ctrl+C`.

Cada vez que abras una nueva terminal, activa de nuevo el entorno virtual:

```bash
# macOS/Linux
source .venv/bin/activate

# Windows PowerShell
.venv\Scripts\Activate.ps1
```

Si Windows bloquea la activación en esa sesión, ejecuta primero:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

El entorno `.venv` ya está contemplado en el `.gitignore` del repositorio: no debes subirlo a GitHub.

## 6. Flujo de trabajo para cada clase

Antes de comenzar:

```bash
cd curso-analisis-datos

# Activa el entorno virtual:
# macOS/Linux: source .venv/bin/activate
# Windows:     .venv\Scripts\Activate.ps1

git pull upstream main
jupyter lab
```

`git pull upstream main` descarga los cambios nuevos del repositorio del curso y los integra en tu copia local. Si tienes cambios locales sin guardar, primero crea un commit o guárdalos temporalmente antes de hacer `pull`. Más información: [Obtener cambios de un repositorio remoto](https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository).

## 7. ¿Qué es un commit?

Un **commit** es una fotografía guardada del estado de tus archivos en un momento determinado. Sirve para conservar un avance y explicar qué cambiaste.

El ciclo básico es:

```text
Archivos modificados → git add → área de preparación → git commit → historial local → git push → GitHub
```

- `git add`: selecciona los cambios que formarán parte del próximo commit.
- `git commit`: guarda esos cambios en el historial local.
- `git push`: envía los commits locales a GitHub.
- `git pull`: trae a tu computadora los cambios que ya están en GitHub.

## 8. Cómo hacer un commit y subirlo a GitHub

Después de modificar y guardar un notebook:

### Paso 1: revisar el estado

```bash
git status
```

Verás qué archivos cambiaron. Los notebooks modificados aparecerán normalmente como archivos con cambios.

### Paso 2: seleccionar los archivos

Es mejor indicar los archivos concretos:

```bash
git add notebooks/01_pandas_introduccion.ipynb
```

Si modificaste varios archivos:

```bash
git add notebooks/01_pandas_introduccion.ipynb datos/ventas.csv
```

También existe `git add .`, pero agrega todos los cambios de la carpeta. Úsalo solo después de revisar que no incluya contraseñas, archivos privados, bases de datos pesadas o la carpeta `.venv`.

### Paso 3: revisar lo que se va a guardar

```bash
git diff --staged
```

### Paso 4: crear el commit

```bash
git commit -m "Completar análisis de ventas"
```

Escribe mensajes breves y descriptivos. Por ejemplo:

- `Agregar limpieza de datos`
- `Resolver ejercicios de pandas`
- `Corregir gráfico de ventas`

### Paso 5: enviar el commit a GitHub

```bash
git push origin main
```

Después actualiza la página de tu repositorio en GitHub y verifica que aparezcan los cambios.

## 9. Ejemplo completo de entrega

```bash
cd curso-analisis-datos
source .venv/bin/activate       # macOS/Linux
# Windows PowerShell: .venv\Scripts\Activate.ps1

git pull upstream main
jupyter lab

# Después de trabajar en el notebook:
git status
git add notebooks/01_pandas_introduccion.ipynb
git commit -m "Resolver ejercicios de pandas"
git push origin main
```

El `push` se enviará a tu fork personal. Entrega al profesor el enlace a tu fork o al commit correspondiente.

## 10. Comandos útiles

```bash
# Ver el estado actual
git status

# Ver los últimos commits
git log --oneline -5

# Ver cambios todavía no preparados
git diff

# Ver archivos preparados para el próximo commit
git diff --staged

# Ver la rama actual
git branch --show-current
```

## 11. Problemas frecuentes

### `git: command not found`

Git no está instalado o la terminal estaba abierta antes de instalarlo. Instálalo, cierra la terminal, abre una nueva y prueba `git --version`.

### `python` o `python3` no se reconoce

En Windows prueba `py`. En macOS/Linux prueba `python3`. Verifica que Python esté instalado.

### `No module named pandas`

Activa el entorno virtual y reinstala las dependencias:

```bash
python -m pip install -r requirements.txt
```

### `not a git repository`

Estás fuera de la carpeta del repositorio. Entra en ella:

```bash
cd curso-analisis-datos
git status
```

### `rejected` o `non-fast-forward` al hacer `push`

Primero guarda tu trabajo local y trae los cambios remotos:

```bash
git status
git add notebooks/mi_notebook.ipynb
git commit -m "Guardar avance local"
git pull upstream main
git push origin main
```

Si aparece un conflicto, Git indicará los archivos que necesitan atención. No borres cambios sin entenderlos; pide ayuda al profesor si no sabes resolverlo.

### Error de autenticación en GitHub

Usa GitHub Desktop o el administrador de credenciales de Git. GitHub no recomienda introducir la contraseña de la cuenta como contraseña de Git por HTTPS. Nunca compartas tokens, contraseñas ni claves en un notebook.

## Lista de comprobación

- [ ] Tengo una cuenta de GitHub.
- [ ] `git --version` funciona.
- [ ] Creé y cloné mi fork.
- [ ] Creé y activé `.venv`.
- [ ] Instalé `requirements.txt`.
- [ ] Puedo abrir JupyterLab con `jupyter lab`.
- [ ] Revisé los cambios con `git status`.
- [ ] Hice un commit con un mensaje claro.
- [ ] Ejecuté `git push origin main`.
- [ ] Verifiqué el resultado en GitHub.
