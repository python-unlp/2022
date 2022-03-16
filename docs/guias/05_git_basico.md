# Git básico

## Introducción

Como ya vimos Git es una herramienta muy buena que nos permite manejar
versiones de nuestro código de manera distribuida con nuestro equipo de
trabajo. Para poder realizar esto es necesario contar con un Servidor de
Git aparte de tener la herramienta instalada en su máquina. En esta
oportunidad vamos a analizar un poco [GitHub](https://github.com/) que
es el Servidor de Git más popular actualmente.

## Crear repositorio en Git

**Ahora vamos a crear nuestro primer repositorio en **Git**, agregarle algunos
archivos y publicarlos en el Servidor de git GitHub:**

* Realiza la instalación de la herramienta **Git** en tu máquina. Tienes una
  guía provista por la cátedra en el [siguiente
    enlace]().

!!! info
    Recorda también realizar la correcta configuración de Git antes de
    usarlo poniendo tu _nombre_ y tu _mail_ que serán datos requeridos para
    cuando quiera hacer tu primer commit.

* Crear un repositorio local con Git en tu máquina dentro de un directorio
  llamado `ejemplo_python`.

```bash
mkdir ejemplo_python
```

```bash
git init
```

![Git Init](img/05_01_git_init.png)

* Mueve dentro de este directorio el programa `run.py` que escribiste en el
  punto 2 de la sección Python.

```bash
cd ejemplo_python
```

* Ahora notarás que hay cambios en tu repositorio Git local:

```bash
git status
```

![Create app](img/05_02_git_status.png)

!!! warning
    Recorda siempre elegir un mensaje adecuado para los commits cuando uses Git.

* Para agregar este archivo al versionado de Git debemos hacer:

```bash
git add app.py
```

![Git add](img/05_03_git_status.png)

* Pocede a crear el primer commit con ese archivo.

```bash
git commit -m "Mensaje de commit"
```

![Git commit](img/05_04_git_commit_log.png)

* Agrega un `README.md` que servirá de documentación para el repositorio donde
  esté el nombre y número de alumno escrito. Modifica la aplicación principal
  también. **Nuevamente notarás cambios en el repositorio local.**

![Git status](img/05_05_status.png)

* Crea un segundo commit

![Git Commit](img/05_06_commit.png)

Hasta el momento todos las acciones realizadas fueron en tu máquina.

Ahora llega el turno de interactuar con el servidor de Git (Github en
este caso) que es el lugar en donde estará disponible el código para
compartirlo.

!!! info
    Para esto es necesario que tengas una cuenta en Github así que si no
    cuentas con una aún puedes [crearla aquí](https://github.com/join).

![Create repo](img/05_07_create_repo.png)

Para usar GitHub de forma segura tienes dos opciones:

- Generar una clave SSH y agregarla al usuario (seguir la guía de [SSH](02_ssh.md)).
- Usar el método HTTP, pero deberás escribir tu usuario y contraseña para cada
  operación con el servidor Github.

Con tu cuenta creada debes crear tu repositorio remoto dentro de Github.

Con tu nuevo repositorio creado resta realizar el enlace entre el repositorio
local en el que viniste trabajando y el repositorio remoto que recién se creó.
Para eso tienes que actualizar tu remote dentro de tu repositorio local con la
url del repositorio remoto (ver comandos sugeridos al crear el repositorio en Github).

Si todo está correctamente configurado, sólo resta hacer el "push" de los cambios.
