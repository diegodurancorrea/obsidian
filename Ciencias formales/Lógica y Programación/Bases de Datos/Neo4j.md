---
Fecha_creacion:: 2025-07-15
Ultima_modificacion:: 2025-07-15
Nombre_documento: Neo4j
tipo:: Componente del lenguaje
autor:: Cypher
---

En este documento estarán las notas del curso en NEO4J disponible en Udemy. 
# ¿Que es?

NEO4J es una **base de datos nativa en grafos** , se diferencia de las bases de datos relacionales SQL en que no sólo almacena información con identificadores únicos o compuestos (*primary key, foreign key*) sino que almacena la **información relacional**. Respeta los principios ACID, y tiene un lenguaje propio de consulta llamado **Cypher**. La información almacenada en este tipo de bases de datos se componen de varios elementos: nodos(almacena las entidades), propiedades (las características de las entidades) y aristas(). Desde una perspectiva de las bases de datos SQL cada fila en una tabla sería una entidad , y cada columna describiría una propiedad. Existen además las *etiquetas* para distinguir entre si a un conjunto de nodos de otros. 

# Crear nodos y relaciones

A continuación los principales comandos y sintaxis para construir los datos en NEO4J, a saber, la creación de nodos y las variables asociadas a esos nodos, etiquetas , propiedades y relaciones. 

```cypher fold title:create_node ln:true 
// los nodos () son generados así: 
CREATE () ; // el ; indica el final de una consulta 
// múltiplos nodos vacíos
CREATE (),(),() ;
// los nodos pueden estar definidos con una variable
CREATE (n)(b)(c) ;
// los nodos pueden tener labels para describir al nodo  
CREATE (n:PERSONA:DOCENTE:PACIENTE) ;
// los nodos pueden tener propiedades para una variable del nodo
CREATE (n:PERSONA{key:"value"});
// los nodos pueden tener relaciones entre ellos
CREATE (n:PERSONA)--[r:RELACION]-->(n:PERSONA) ; // la fleca indica la direccionalidad 
// las consultas pueden encapsularse en variables para seer consultados luego
CREATE path = (n:PERSONA)--[r:RELACION]-->(n:PERSONA) ;
```
# Seleccionar nodos
para seleccionar los nodos en una base de datos NEO4J debemos usar la expresión
```cypher fold title:expretion_node ln:true
match(n)
return n // selecionamos todos los nodos de la database
```
A continuación  la expresión para seleccionar los nodos según **propiedades** , **etiqueta** y **relación**

```cypher fold title:march_node ln:true 
match(n:PERSONA)
return n // nodos que tiene la etiqueta PERSONA

match(n{property:'value'})
return n // nodos cuya propiedad 'property' tiene el valor 'value'

match(n)--(m)
return * // nodos y relaciones que tienen alguna relación sin importar dirección
match(n:PERSONA)-->(m:EMPRESA)
return * // nodos y relacion de n PERSONA con relación outward hacia nodo m EMPRESA

match(n:PERSONA)<--(m:DOCTOR)
return * //nodos y relacion de n PERSONA con relación inward hacia nodo m DOCTOR

match(n)-->(m)
return n // sólo nodos n con relación outward con m 
```

También podemos copiar **propiedades** de un nodo hacia otros nodos con *doc notation*

```cypher fold title:copy_node ln:true 
CREATE (n{property:"Propiedad"})
CREATE (m{property: n.property}) // copiamos la propiedad de n
```

<<<<<<< HEAD
```cypher fold title:copy_node ln:true 
CREATE (n{property:'Propiedad'})
CREATE (m{property: n.property}) // copiamos la propiedad de n
```
=======
Podemos filtrar nuestros match a través de la sentencia *return*

```cypher unfold title:filter_node ln:true 
MATCH (n)-->[r]-->(m)
RETURN Type(r) // retorna el nombre de todas las relaciones 

MATCH (n)-->[r]-->(m)
RETURN DISTINCT m // retorna todos los valores ùnicos de m 

MATCH (n{property:'property'})-->[r:LABEL]-->(m)
RETURN Type(r) // retorna el nombre de todas las relaciones 

MATCH (n{property:'property'})-->[r:LABEL]-->(m)
RETURN PROPERTY r // retorna la propiedad del nodo r  

MATCH (n:PERSON{property:'property'})-->[r:LABEL]-->(m)
RETURN PROPERTY r // retorna la propiedad del nodo r  

MATCH p = (n)-->[r:PERSON]-->(m)<--[r:ACTOR]-->(o)
RETURN RELATIONSHIP(p)  // retorna en formato lista todos la informaciòn de las relaciones   
// Or operation con | 
MATCH  (n)-->[r:PERSON|ACTOR|WOMEN]-->(m)<--[r:ACTOR]-->(o)
RETURN type (r)  // el atributo que encontró

```

Podemos **crear nuevas relaciones** entre nodos ya existentes: 

```cypher unfold title:filter_node ln:true 
MATCH (n{property:"property_1"});
MATCH (z{property:"property_2"});
CREATE (n)-->[r:NEWLINE]-->(z)
```

Podemos usar la sentencia  **OPCION** para no romper el código cuando estamos buscando relaciones que no tenemos certeza de su existencia, aunque permite mayor flexibilidad en los *querys* , no está diseñado para seleccionar múltiples nodos, por tanto, se recomienda una sintaxis línea por línea. 

```cypher unfold title:opcional_node ln:true 
OPTIONAL MATCH (n{property:"property_1"}) // si no coincide continua la siguiente sentencia
OPTIONAL MATCH (n)-->(m) // si no coincide continua la siguiente sentencia
RETURN n.property, m.property
```
>>>>>>> b4fbd8b109aa93616654fbada1b15e82b1094f9c
