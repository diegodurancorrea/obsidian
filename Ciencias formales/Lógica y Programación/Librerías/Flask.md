---
Fecha_creacion:: 2025-09-23
Ultima_modificacion:: 2025-09-23
Nombre_documento: Flask
tipo:: Librería
autor:: python
---
Este resumen corresponde al curso de flask en Platzi, el objetivo de esta formación es aprender a crear APIS y hacer conexiones con bases de datos u ORM's . 

Flask es un microframe de código abierto escrito en python que facilita la creación la creación de aplicaciones web , en especial para servicios API REST. la documentación se encuentra disponible [aqui](https://flask-es.readthedocs.io/quickstart/#deploying-to-a-web-server); las notas a continuación intentarán clarificar contenidos estructurales de la librería.     

Una aplicación sencilla flask puede ser la siguiente: 

~~~python fold title:app_flask.py
from flask import Flask

app = Flask(__name__) # --> aplicación toma el nombre del archivo
 
@app.route("/") # --> decorador route define el endpoint url 
def hello_world():
    return "<p>Hello, World!</p>"
~~~

e iniciamos la aplicación ejecutando en la terminal: 

~~~bash
$ flask --app app_flask run 
--host=0.0.0 --> agregar para hacer público el servidor en la red local
~~~
# Render Templater

# Peticiones 
