---
Fecha_creacion:: 2025-07-15
Ultima_modificacion:: 2025-07-15
Nombre_documento: SQL Alquemist
tipo:: Librería
autor:: Python
---
>El objetivo de este aprendizaje es integrar los archivos Pajek en un formato tabular compatible con las bases de datos SQL 

SQLAlchemy es una librería en Python orientada hacia ORM (*objet relational mapping*) que se compone de dos diferentes API: **ORM** para mapear sesiones con la base de datos, y **CORE** establecer la conectividad y procesamiento directo de las consultas SQL  

# Estableciendo la conexión

la conexión se establece a través de un **objeto** llamado **engine** como la fuente central de la conexión. las sesiones de ORM es el equivalente a las conexiones del CORE
```python fold title:connection.py ln:true
from sqlalchemy import create_engine , text, Session
engine = create_engine('URL_string' , echo = True ) # varía según cada db , echo: produce logs

# usamos el objeto text() para ejecutar sentencias crudas SQL, no debe ser el común cuando usamos SQLalchemy
# manejamos el engine con un manejador de contexto with

# usamos connect() 'commit as you go' : debemos hacer commit()   
with engine.connect() as conn: 
	conn.execute(text('SQL_statement'))
	conn.commit() # si no se explicita se ejecuta un ROLLBACK

# usamos begin() 'begins one' , modo recomendado   
with engine.begin() as conn: # expresion recomendada
	conn.execute(text('SQL_statement'))

# Podemos usar una Session como equivalente a Connection cuando no usamos construcciones ORM

with Session(engine) as session: 
	session.execute(text('SQL_statement')) # pasa las expresiones SQL directamente al CORE
```
### Enviar múltiples parámetros (executemany)

SQLAlchemy soporta múltiples *request insert* a una sentencia SQL que será invocada múltiples veces 
```python fold title:executemany.py ln:true
from sqlalchemy import create_engine , text, Session
engine = create_engine('URL_string' , echo = True ) # varía según cada db , echo: produce logs

with engine.connect() as conn:
    conn.execute(
        text("INSERT INTO some_table (x, y) VALUES (:x, :y)"),
        [{"x": 11, "y": 12}, {"x": 13, "y": 14}],
    )
    conn.commit()
```

Al igual que podemos enviar múltiples parámetros también podemos recibir múltiples selecciones de las sentencia *SELECT* , se almacenará en la variable (llamémoslo *result*) un objeto iterable de filas que se comportarán como *tuplas* de python. Podemos acceder a estos datos a través de diferente formas: tuple assigment, integer index, atribute name  y  mapping access. 

```python fold title:tuple_assigment.py  ln:true
result = conn.execute(text("select x, y from some_table"))

for x, y in result:
    print(x,y)
```

