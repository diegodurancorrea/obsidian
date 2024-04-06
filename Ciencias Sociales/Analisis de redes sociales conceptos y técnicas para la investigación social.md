---
"Fecha_creacion:": 2024-03-26
"Ultima_modificacion:": NaN
Nombre_documento: Análisis de redes sociales conceptos y técnicas para la investigación social
"tipo:": Reseña larga
"autor:": Édison Gabriel Brand Monsalve
---

# Segunda parte: investigar con ARS. Una propuesta técnica

Los **Atributos** pueden ser elementos de análisis en los estudios estructurales; reflejan relaciones solidificadas a través del tiempo. Y pueden ser representados relacionalmente a través de las siguientes herramientas. 
+ Visualización topográfica: una red es una estructura de puntos a los cuales se les asigna una información que se halla conectada por lazos. Por intercambio de recursos o por pertenencia. 
+ Agrupación o disgregación de elementos por identidad y diferencia: Permite caracterizar los puntos en la estructura, es decir, darle un tratamiento estadístico para un posterior procesamiento
+ medición de relaciones sociales: medidas matemáticas para ver el nivel de cohesión en la estructura y centralidad de los puntos: 
	+ Centralidad: importancia relativa de los puntos al interior de la red, puede ser analizado en el grado de su popularidad, intermediación o vinculación. La centralidad puede ser de tres tipos: 
		+ de grado: mide el total de vínculos que tiene un punto dentro de la red, es un indicador de la comunicación del punto con los demás. 
		+ de cercanía: Mide que tan cerca está un actor de todos los demás que componen una red. Se define por la inversa de la longitud media de las rutas más cortas desde todos los otros actores de la red; se asume que a mayor cercanía, mayor influencia. 
		+ de intermediación: determina la frecuencia geodésica entre un par de actores de la red, esto es, la frecuencia con la cual un nodo es encontrado en el camino entre dos nodos. Estos nodos controlan el flujo de información en la red. 
	+ Cohesión: Permite identificar los lazos más fuertes, y los subgrupos conformados por pequeñas zonas en la red más densa por el intercambio o la pertenecía común a espacios de articulación que potencian sus objetivos 

Las relaciones se definen a través de dos modos de relación (tipo): relaciones de intercambio de recursos y relaciones de pertenencia. Los elementos que se intercambian responden a la forma en como se tematiza el entorno: riesgo o dependencia y sus respectivas estrategias de mitigación. esto sólo es cierto para relaciones de intercambio entre organizaciones. Al interior de la organización, los intercambios son comprendidos, al interior de la teoría sistémica, como *flujo mediante dependencias* , estrategia para el manejo del entorno del personal. Los *lazos* que unen a una organización están orientado a mantener la autopoiesis de la organización, los cargos de 'dirección' de la organización suelen dedicarse a la autoproducción de la información y el acoplamiento con el entorno. las demás comunicaciones son reducciones a la acción: órdenes, tareas, trabajos; generalmente realizados a la espera de una paga. 

Los atributos 'dados' a los nodos son luego analizados a partir de particiones definidas como subconjuntos de características , que permiten encontrar una equivalencia de función de la red y agrupar las organizaciones de acuerdo a la variables que las caracterizan (variables discretas) y suelen ser útiles para contrastar funciones con posiciones ocupadas en la red. 

##### pregunta de investigación

Para iniciar el análisis en ARS es necesario ubicar nuestra pregunta investigativa; para esto es necesario definir que tipo de red queremos conocer, estas pueden ser red personal , organizacional y total.  la clase de conexión y la naturaleza de los datos.
### tipos de datos 

Los datos ingresados puede ser de dos tipos:  redes lineales (emisor, receptor, vínculo) o redes matriciales (se construyen a partir de matrices adyacentes o de filiación). Las redes pueden estar acompañadas de  datos cualitativos o datos cuantitativos.

|    elemetos directos     |   elementos indirectos    | Vínculos                |  RED   |
|:------------------------:|:-------------------------:| ----------------------- |:------:|
| Primer nodo identificado | Segundo nodo identificado | contenido transaccional | Lineal |

#### diseño de ficheros 


| Tipos de fichero   | red o fichero de Network (.net)                                     | Fichero de partición                                                                                                     | Fichero de vectores                                        | Fichero de matrix |
| ------------------ | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------- | ----------------- |
| descripción        | se encuentran las unidades básicas de la red denominadas **diadas** | registro de las características cualitativas de los nodos. es una clasificación o agrupamiento de los vértices en la red | Registro de las características cuantitativas de los nodos |                   |
| Notas              | Un fichero por cada tipo de intercambio identificado                | Se debe disponer de una tabla de códigos para el análisis posterior                                                      |                                                            |                   |
| Redes dirigidas    | Denominados arcos                                                   |                                                                                                                          |                                                            |                   |
| Redes no dirigidas | Denominadas edge                                                    |                                                                                                                          |                                                            |                   |
| nodos              | modificable en color y forma                                        |                                                                                                                          |                                                            |                   |
| vinculos           | modificable en color , forma y tamaño                               |                                                                                                                          |                                                            |                   |
| redes              | posible añadir más redes con id y etiqueta                          |                                                                                                                          | 24045                                                      |                   |


| tipos de red | de un modo                                               | de dos modos                                                                                                                                                                |
| ------------ | -------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| descripción  | corresponden a relaciones entre un mismo tipo de actores | corresponden a relaciones entre dos tipos de actores                                                                                                                        |
| notas        |                                                          | Especificar el número total de nodos que tendrá la red, seguido del número de nodos que corresponden al primer tipo de actor de la red, separados por un espacio intermedio |
densidad : líneas existentes sobre el número de líneas potenciales que pueden existir en la red 