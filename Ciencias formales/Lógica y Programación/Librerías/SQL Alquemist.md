---
Fecha_creacion:: 2025-07-15
Ultima_modificacion:: 2025-07-15
Nombre_documento: SQL Alquemist
tipo:: Librería
autor:: Python
---
El objetivo de este aprendizaje es integrar los archivos Pajek en un formato tabular compatible con las bases de datos SQL 

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

### Metadata

Son los objetos de python que *representan conceptos como tablas y columnas* , no así los datos; tenemos una colección para manejar nuestras tablas llamado **MetaData object**, las tablas pueden referirse a otras tablas guardados en otras colecciones, aunque se recomiendo manejar una sola colección para toda la aplicación. 

```python fold title:meta_data.py  ln:true
# declaramos el MetaData Object 
from sqlalchemy import MetaData , Table , Column, Interger, String , Foreigkey 
metadata_obj = MetaData()

# declaramos un objeto tabla
user_table = Table( "user_account",
     metadata_obj,
     Column("id", Integer, primary_key=True),
     Column("name", String(30)),
     Column("fullname", String),)
     
# podemos acceder a las columnas acudiendo a la clase padre Table
user_table.c.name
user_table.c.keys()
user_table.primary_key() # muestra la llave primaria de la tabla

# declaramos un segundo objeto tabla
book_table = Table ( "book_register", 
	metadata_obj,
	Column('id' , Integer, primary_key = True)
	Column("user_id", ForeignKey("user_account.id"), nullable=False)) # añadimos constraint statements 

#invocamos el método create_all() para DDL (data definition language)
metadata_obj.create_all(engine)

```

SqlAlchemys testea la existencia de cada tabla antes de emitir **create** statements, y las crea en un orden adecuado para evitar conflictos con sentencias *constraints*. Para revertir el proceso usamos el método `MetaData.drop_all()`. 

Podemos emplear ORM para construir *declarative tables*  a través de **ORM mapped class** —con un estilo más sucinto o pythonista—, una clase mapeada es cualquier clase que queramos crear con atributos de clase que serán referidos a una tabla de la base de datos, hay pocas formas en las que esto puede lograrse, una de ellas es llamada *declarativa*  que permite *definir clases y la metadata de la tabla* a la vez—podemos consultar otros tipos de mapear una clase  [aqui](https://docs.sqlalchemy.org/en/20/orm/declarative_tables.html#orm-declarative-mapped-column-type-map)— 

~~~ python fold title:declarative_base.py 
# metadata object se encuentra al interior de la ORM construcción
from sqlalchemy.orm import DeclarativeBase

class Base(DeclarativeBase):
    pass
    
#accedemos a metadata
Base.metadata
Base.registry # mapper congiguration unit in SQLAlchemy ORM 

from typing import List
from typing import Optional
from sqlalchemy.orm import Mapped
from sqlalchemy.orm import mapped_column
from sqlalchemy.orm import relationship

class User(Base):
#método __init__ implícito que proporciona argumentos posicionales kwards
    __tablename__ = "user_account"
    id: Mapped[int] = mapped_column(primary_key=True)
    name: Mapped[str] = mapped_column(String(30))
    fullname: Mapped[Optional[str]]
    addresses: Mapped[List["Address"]] = relationship(back_populates="user")
    def __repr__(self) -> str:
        return f"User(id={self.id!r}, name={self.name!r}, fullname={self.fullname!r})"

class Address(Base):
    __tablename__ = "address"
    id: Mapped[int] = mapped_column(primary_key=True)
    email_address: Mapped[str]
    user_id = mapped_column(ForeignKey("user_account.id"))
    user: Mapped[User] = relationship(back_populates="addresses")
    def __repr__(self) -> str:
        return f"Address(id={self.id!r}, email_address={self.email_address!r})"
    
~~~

Para generar sentencias DDL en nuestra *base declarativa*  usamos el mismo método asociado a la clase MetaData. 

~~~ python fold title:declarative_base_DDL.py
Base.metadata.create_all(engine)
~~~

### table reflection

forma de generar *table objects* automáticamente a través de una base de datos existente, es el proceso inverso de las *declarative tables*.  

~~~ python fold title:table_reflection.py
from sqlalchemy import MetaData 
metadata_obj = MetaData()

some_table = Table("some_table", metadata_obj, autoload_with=engine) # identificamos el nombre de la tabla existente y lo asociamos a una nueva tabla y el la colección metadata que lo almacena. 
~~~

# Trabajando con datos
Nuestra interacción con una base de datos siempre se da en términos de una *transacción*,  una donde Interactuamos con la base de datos a través de las representación que hacemos de ella en la *meta-data*. 
## Insert
Cuando usamos el ORM para ejecutar *bulk operations*, es decir, una sola operación sobre un conjunto de datos, hacemos uso directamente de la función `insert()` 
~~~ python title:insert.py
from sqlalchemy import insert
stmt= insert(user_table).values(name="spongebob", fullname="Spongebob Squarepants")
~~~

Si hacemos `print()` de `stmt` obtenemos:
~~~sql
INSERT INTO user_account (name, fullname) VALUES (:name, :fullname)
~~~

Para ejecutar nuestras sentencias `insert()`  usamos la habitual estructura que ya vemos en [[SQL Alquemist#Estableciendo la conexión|los capítulos anteriores]], de este forma: 
~~~python
with engine.connect() as conn:
    result = conn.execute(stmt)
    conn.commit()
~~~

Las sentencias `insert()` usualmente no devuelven ningún valor, sin embargo, si sólo introducimos un valor podemos acceder a valores por defecto al nivel de la columna utilizando `result.inserted_primary_key`. 
### execute-many con insert

La sentencia `insert()` genera automáticamente cláusulas de valores cuando no utilizamos el método `insert().values()` , constituyen sentencias `values` vacías si sólo las imprimimos. Si ejecutamos esta sentencia vacía compilará la cadena SQL en base a los parámetros que pasamos al método`connection.execute()` , de esta forma podemos ejecutar varias filas a la vez. 

~~~python
with engine.connect() as conn:
    result = conn.execute(
        insert(user_table),
        [
            {"name": "sandy", "fullname": "Sandy Cheeks"},
            {"name": "patrick", "fullname": "Patrick Star"},
        ],
    )
    conn.commit()
~~~

podemos pasar una lista de diccionarios para insertar los datos, dada la construcción automática de las cláusulas que compilan en cadenas las columnas y valores, sólo el primer diccionario de la lista **determina que columnas estarán en las cláusulas values**, dado que sólo puede hacer una sentencia `insert()` para todos los parámetros.  

## select
Tanto en Core como en ORM, la función `select()` genera una estructura `Select` que se utiliza para todas las consultas `SELECT`. Al pasarla a métodos como `Connection.execute()` en Core y `Session.execute()` en ORM, se emite una instrucción `SELECT` en la transacción actual y las filas resultantes están disponibles a través del objeto `Result` devuelto.

De igual forma a las función `insert()` ejecutamos la sentencia de la siguiente forma 
~~~python
`from sqlalchemy import select
stmt = select(user_table).where(user_table.c.name == "spongebob")
print(stmt)
~~~
Los resultados arrojan un output de filas que puede ser iterado, en el caso de`Session.execute()` devuelve un objeto de la clase *nombre_tabla* que contiene los valores de cada fila. 

para configurar nuestras sentencias `SELECT` en relación a columnas y tablas: 
~~~python
# CORE
select(user_table) # selecciona todas las columnas de la tabla
select(user_table.c.name, user_table.c.fullname) # utilizamos el accesor .c para determinar las columnas individuales a seleccionar
select(user_table.c["name", "fullname"])# alternativa a la opción anterior
# ORM 
select(User)  # selecciona todas las columnas de la clase que mapea la tabla
select(User.name, User.fullname) # utilizamos los atributos de clase para determinar las columnas individuales a seleccionar
select(User.name,Address).where(User.id==Address.user_id).order_by(Address.id).all() # combinamos ambas clases 
~~~

en los casos en que necesitemos *injectar* expresiones SQL a nuestras sentencias podemos integrarlas satisfactoriamente a través de `text()` y  `literal_column` 
~~~python
#CORE
stmt=select(text("'somephrase'"),user_table.c.name).order_by(user_table.c.name) # añadimos la expresión
stmt=select(literal_column("'somephrase'").label("p"),user_table.c.name).order_by( user_table.c.name ) # con esta expresión podemos etiquetar la columna que puede ser referida en subsecuentes consultas
~~~

para filtrar usamos tanto la función `where` o `filter_by`, usamos los operadores de python para construir nuestras sentencias

~~~python
select(user_table).where(user_table.c.name == "squidward")
select(user_table).where(user_table.c.name == "1_").where(user_table.c.name == "2_") # anidamos where para simular un AND
select(address_table.c.email_address).where(
...         user_table.c.name == "squidward",
...         address_table.c.user_id == user_table.c.id,
...     )# alternativa a la línea anterior 
select(Address.email_address).where(
...         and_(
...             or_(User.name == "squidward", User.name == "sandy"),
...             Address.user_id == User.id,
...         )
...     ) # utilizamos la función or_() y and_() para filtrar 
~~~

para ordenar y agrupar usamos tanto la función `order_by` o `group_by` o `having`, usamos los operadores de python para construir nuestras sentencias

~~~python
select(user_table).order_by(user_table.c.name)
select(User).order_by(User.fullname.desc()) # en ORM tenemos la función .desc() y .asc()
~~~

QLAlchemy proporciona funciones SQL de forma abierta utilizando un espacio de nombres conocido como *func*.  Cuando usamos funciones agregadas en SQL, La cláusula GROUP BY es esencial, ya que permite particionar las filas en grupos donde se aplicarán funciones de agregación a cada grupo individualmente. Al solicitar columnas no agregadas en la cláusula COLUMNS de una instrucción SELECT, SQL requiere que todas estas columnas estén sujetas a una cláusula GROUP BY, ya sea directa o indirectamente, según una asociación de clave primaria. La cláusula HAVING se utiliza entonces de forma similar a la cláusula WHERE, con la diferencia de que filtra las filas según los valores agregados en lugar del contenido directo de la fila.
~~~python
select(User.name, func.count(Address.id).label("count"))
...         .join(Address)
...         .group_by(User.name)
...         .having(func.count(Address.id) > 1) # agrupamos y filtramos 

select(Address.user_id, func.count(Address.id).label("num_addresses"))
...     .group_by("user_id")
...     .order_by("user_id", desc("num_addresses"))# ordenamos la agrupación #CORE aliases
>>> user_alias_1 = user_table.alias()
#ORM aliases
>>> address_alias_1 = aliased(Address) # sobre una clase mapeada
~~~

