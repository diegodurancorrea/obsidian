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
