---
Fecha_creacion:: 2025-09-23
Ultima_modificacion:: 2025-09-23
Nombre_documento: Flask
tipo:: Librería
autor:: python
---
Este resumen corresponde al curso de flask en Platzi, el objetivo de esta formación es aprender a crear APIS y hacer conexiones con bases de datos u ORM's . 

Flask es un microframe de código abierto escrito en 

~~~python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
~~~
