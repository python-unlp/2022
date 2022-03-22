# Jupyter notebook

## Introducción

Jupyter Notebook es un entorno de trabajo interactivo que permite desarrollar código en Python. Es utilizado ampliamente para análisis numéricos, estadísticas y machine learning, entre otros campos de la informática.

Algunas de las principales funciones y beneficios que provee:
* Permite editar el código desde el navegador, resaltando la sintaxis, indentación y también provee funciones de autocompletado.
* Permite ejecutar código desde el navegador, mostrando los resultados de esta ejecución.
* Provee facilidades para la documentación y visualización del código.
* No solo permite escribir código Python sino también permite visualizar otro tipo de extensiones como Markdown y HTML.
* Permite iniciar una sesión de una terminal de bash para ejecutar comandos desde el mismo navegador.
* Se puede agregar cualquier archivo **.py** o **.ipynb** simplemente arrastrandolos hasta la interfaz de la herramienta.
    * Los archivos que genera son de extensión "ipynb", con lo que podemos compartirlos con nuestros compañeros.

Esta guía está basada en la siguiente documentación: https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#creating-a-new-notebook-document

## Prerequisitos

Esta guía asume que las siguientes herramientas ya fueron instaladas correctamente en el sistema:
* Python 3.10.2
* Pip3
    * Usar alguna de las últimas versiones

## Instalación

Para instalar Jupyter Notebook utilizando pip, se debe ejecutar el comando:

```bash
pip3 install jupyter
```

## Iniciando el servidor

Una vez instalado, para poder comenzar a utilizarlo es necesario iniciar el servidor de Jupyter Notebook.
Este servidor se ejecutará en "localhost", es decir que nuestra computadora creará un servidor local ejecutando la herramienta.
Para esto se debe ejecutar el siguiente comando:

```bash
jupyter notebook
```

Una vez iniciado el servidor, nuestra computadora abrirá automáticamente el navegador web visualizando la interfaz gráfica de la herramienta.
**En caso de que esto no suceda automáticamente, abrir un navegador web e ingresar la siguiente url: http://localhost:8888/**
Por defecto el servidor se ejecuta utilizando el puerto **8888** de nuestra computadora.

Para terminar la sesión del servidor basta simplemente con ir nuevamente a la terminal donde se ejecuto el comando anterior y presionar las teclas **CTRL + C**. La herramienta le pedirá una confimación y luego apagará el servidor.
**Importante:** Guardar todos los cambios antes de apagar el servidor. De esta forma, al iniciarlo nuevamente, todos los archivos de la sesión anterior seguirán estando disponibles.

## Primeros pasos

Para comenzar a utilizar Jupyter Notebook, primero debemos crear un archivo de código Python o "notebook".
Para esto simplemente debemos hacer click en el botón "New 🔽" y seleccionar el intérprete de Python.
![image](https://jupyter-notebook.readthedocs.io/en/stable/_images/new-notebook.gif)

Una vez creado nuestro archivo notebook, solo basta con escribir código Python en él y darle click al botón "Play" para ejecutarlo y ver su resultado.
<img width="1179" alt="image" src="https://user-images.githubusercontent.com/26656167/158714034-4bb7fb48-06c4-4d1a-84ed-040d9ef3daf9.png">

La herramienta es muy flexible y permite no solo el uso de librerías externas, sino tambien referenciar a otros archivos dentro del proyecto.
Algunos ejemplos pueden encontrarse en el siguiente repositorio de Github: https://github.com/ipython/ipython/blob/master/examples/IPython%20Kernel/Rich%20Output.ipynb

En el caso de utilizar alguna librería de Python, debemos primero instalarla en nuestro sistema.
Por ejemplo en el caso de [`matplotlib`](https://matplotlib.org/stable/users/getting_started/index.html#installation-quick-start)
```bash
pip3 install matplotlib
```
Y luego podemos ejecutar código utilizando dicha librería en Jupyter Notebook.
<img width="1142" alt="image" src="https://user-images.githubusercontent.com/26656167/158714983-ee9c0e17-7e53-4cc3-a4a4-cd4de527a348.png">

