---
Fecha_creacion:: 2024-05-16
Ultima_modificacion:: NaN
Nombre_documento:: Exploratory network analysis with Pajek
Tipo_documento:: Libro 
tipo:: Reseña larga
autor:: Wouter de Nooy , Andrej mrvar, Vladimir Batajelj
---
# Nota introductoria 

Este es un resumen sobre un libro que es un manual para el uso del software Pajek. Los conceptos aquí presentados, por tanto, tienen su correspondencia en las técnicas que son posible gracias a la teoría de redes. No obstante, este no será una guía técnica de mencionadas técnicas, ==sólo será una exposición de la teoría que sustenta la metodología==.   
# Part 1 : Fundamentals

## Looking for social structure 

Las ciencias sociales buscan [[Sistemas sociales; lineamientos para una teoría general#Estructura y tiempo|estructuras]] sociales; el análisis de redes sociales comprenden la estructura como una red de vínculos sociales sostenidos en el tiempo. La estructura, a diferencia del [[Analisis de redes sociales conceptos y técnicas para la investigación social#Primera parte|esquema]], implica que los vínculos importan, es decir, transmiten: comportamientos, actitudes , información y bienes. 

Las representaciones de la estructura social se hará en base a un grafo. un grafo **es un conjunto de vértices y un conjunto de líneas entre un par de vértices**. ahora un red social es **un grafo con información adicional de los vértices y líneas  del grafo** (para indicar su fuerza). De esta forma un vértice en el grafo equivaldría a un actor en la red social, es decir, en una **persona, organización o nación involucrada en una relación social** , de la misma forma la línea sería un vínculo que puede tomar un valor. 

La sociometría estudia las relaciones interpersonales, y asume que la sociedad no es un agregado de individuos y sus características, sino de vínculos estructurales. ==**En la sociometría las elecciones sociales por parte del individuo son la mejor expresión de una relación social**==. El sociograma, tomando los resultado de la sociometría, es **la representación gráfica de la estructura de un grupo, que necesariamente son interrelaciónales entre sí de alguna manera**. Los sociogramas son útiles en la medida en que un representación gráfica puede revelar las realidades no visibles de otra forma, en otras palabras, **analizar e interpretar patrones de relacionamiento entre los actores**. 

### Un asunto metodológico 

Una red se diferencia de un grafo por la información; esta debe cumplir algunos requisitos, para empezar la información del vértice es cualitativamente distinta a la información estructural de la red social. Otra cuestión, de mayor relevancia, es la amplitud de la red. Es imposible saber el grado de representatividad de un conjunto de vértices tomados al azar, lo mismo sucede con nuestra selección de vértices o actores, el sesgo, en ambos casos, deviene del hecho de no tratar con la red en su conjunto. Ahora viene la pregunta: *¿Cómo sabemos que estamos trabajando con toda la red? la respuesta depende completamente de un criterio teórico*

#### construir una red social 

Los datos necesarios para construir una red social pueden ser conseguidos de dos maneras: datos directos y datos indirectos. 
##### directos
Se acude a formas que puedan recolectar datos directamente de los actores sociales. El cuestionario o free recall se erige como el método por excelencia. Dentro del cuestionario es posible restringir o no restringir las posibilidades de elección del actor (aquí no se consideran estas limitaciones y alcances), más allá de esto, las formas del cuestionario puede adquirir la forma de una pregunta para conocer rankings o comparaciones de pares desde el punto de vista del actor. 
##### indirectos
Se acude a datos ya construidos para otros fines. Una limitación de esta clase de datos es la dificultad para otorgar una identificación única de la que se puedan explorar otros datos (si acaso es necesario) 

### Manipulación 

Una vez tenemos nuestra red social construida podemos modificarla, como en el caso de que la red social sea tan grande que su visualización no arroje información de calidad. No obstante, esto no impide que no se pueda, a través de una red social gigante, extraer cálculos estructurales, que resultan más concisos y precisos que una visualización. 
#### Visualización 

En grafos la ilustración sirve para visualizar conceptos y hacer pruebas. Hay recomendaciones: 1) la distancia entre dos vértices debería expresar la fuerza o el número de sus vínculos, de la misma manera, los vértices que están conectados deberían ser dibujadas más cerca que aquellos que no lo están. 2) se debe reducir el número de líneas cruzadas para mejorar la legibilidad de la visualización.  

Pajek habilita varios comandos para lograr una mejor visualización, estos son los comandos de energía que modifican la ubicación de los vértices para minimizar la variación de la longitud de las líneas, hasta encontrar un estado de equilibrio. Encontrando limitaciones en la inicial posición en los vértices. Se recomienda:
+ la función kamada kawai para redes que no superen los 500 vértices,
+ y la función Fructerman Reingold para redes que superen los 500 vértices. Existe en esta última la posibilidad de modificar la distancia óptima entre los vértices
+ la función '*info*' crea una partición que permite observar el peor aspecto de la red para mejorarla manualmente 

## atributtes and relations

Una parte importante, aunque añadida, de las redes sociales, es su capacidad para combinar los datos relacionales con atributos no relacionales que mejorar las interpretaciones estructurales. Los atributos son las propiedades de los actores que no están basados en su posición estructural al interior de una red social
### Particiones
Estos atributos cuantitativos son llamados particiones por Pajek y se definen como la **clasificación que guarda las características discretas de los vértices**, consiste en un número defino de clases que pueden, a través de la extracción de sub redes, reducir su tamaño o complejidad. las particiones, a nivel de archivo, pueden describirse como una lista de números enteros asociados a una lista de vectores; es probable que el orden de estos enteros corresponde con el grado ordinal de la variable, esto depende del investigador. La integración de los atributos es relevante porque permite constatar se existe una correlación entre estos y las características estructurales. 

#### sub redes

Las particiones dividen a la red social en un número de conjuntos excluyentes entre si. La primera posibilidad que permiten las particiones es la reducción de la red social en sub redes definida como la **selección de un sub conjunto de sus vértices y de todas las líneas que sólo inciden con los vértices seleccionados.** 

##### Extracciones

las extracciones pueden ser de tres tipos: 
+ vista local:  extraer solo una parte de la red 
+ vista global: agregar todos las partes en un sólo único vértice
+ vista contextual: se selecciona que vértices reducir en una sola agregación y cuales no redecir; funciona para enfocarse en una clase de vértices respecto a unos vínculos agregados

Un vértice agregado y reducido a un sólo vértice consiste **en remplazar un sub conjunto de vértices por un sólo vértice que incide para todas las líneas que lo conectan con vértices que originalmente no incidían dentro del subconjunto seleccionado**. el valor de las líneas que ahora lo conecta corresponde con la suma de todos los valores individuales dentro del sub conjunto.  Cuando agregamos de esta manera las relaciones dentro del propio sub conjunto se representa como un bucle del vértice resultante consigo mismo, el valor de la línea también resulta de la suma de todos las relaciones individuales.

La utilidad de la extracción consiste en proveernos de una vista parcial para comprender mejor estructuras de redes muy complicadas a primera vista. 
#### Un asunto metodológico

Las particiones respetan la misma secuencia de los vértices ingresados en nuestra red social. Por lo que, necesariamente, el número de entradas en la partición debe ser el mismo número de vértices en la red, es decir, compatibilidad. 
### Vectores
Los vectores guardan propiedades continuas que pueden tomar cualquier valor en un rango definido. A nivel de archivo se describe como una lista de números reales; a diferencia de las particiones, los vectores no clasifican los vértices en clases. La función del vector es, entonces, asignar un valor numérico a cada vértice en una red social y pueden ser usado en cálculos. Los valores negativos pueden ser usados en cálculos pero no pueden ser representados en un visualización
#### De vector a partición 

Además de los cálculos, podemos transformar nuestros vectores en particiones; existen múltiples opciones que nos ofrece Pajek:

+ Remover decimales: se eliminan los decimales de los números reales y los enteros iguales resultantes conformarán una nueva partición 
+ Particiones por intervalos:  agregamos el límite de una nueva partición y luego añadimos el incremento, el resultado es que cada partición tendría la misma diferencia de una a otra 
+ Particiones por selección: agregamos una lista de los límites superiores de cada clase, lo que permite tener un control sobre el tamaño y la diferencia entre cada clase
+ Sub vector de una partición
##### Estadística

La estadística ofrece técnicas para describir y comparar ==atributos== , de tal manera que si las relaciones estructurales pueden ser convertidas en atributos, estos, a su vez, pueden ser incluidos en análisis estadísticos. En esta línea, los vértices agregados mediante particiones permiten las aplicaciones de las tradicionales medidas estadísticas agregativas. Por tanto, las particiones y los vectores que guardan en si características estructurales de los vértices son el puente entre los análisis de redes sociales y la estadística. 

# Part 2: Cohesión 
Las redes revelan quién está conectado y quien no lo, que organizaciones están conectadas y otras no. La hipótesis que se asume estriba en que las personas que encajan o coinciden en sus características sociales tienden a interactuar más frecuentemente; y las personas que interactúan con frecuencia con frecuencia compartirán una común actitud o identidad. 

las interacciones sociales son la base de la solidaridad, las normas compartidas, la identidad y la acción colectiva; las personas que interactúan se consideran a sí mismo como grupo sociales. A estas concesiones densas se les llama sub grupos cohesionados y se asume que están unido por más de una relación, se espera que las personas similares interactúen más entre si que entre desiguales, a esto se llama principio de homofilia. 

Una de las posibilidades con los análisis estructurales enfocados en la cohesión es observar si el grupo concuerda o difiere respecto de alguna otra característica social, y se refiere a como los vértices están interconectados.
### sub grupos cohesionados 

Los sub grupos refieren a un conjunto de vértices en una red. La cohesión está presente tanto en la red como en los subgrupos y refieren a la cantidad de vínculos que existen. Un conjunto de vértices están más cohesionadas si hay más vértices entre ellos, entonces, la densidad es **el número de líneas en una simple red , expresada como una proporción del máximo posible número de líneas**.  Una red con una total densidad se le da el nombre **una red completa**. Esta definición de densidad puede tener una concordancia con el concepto de *complejidad*, pero esta vez desde la teoría de grafos, de todas formas se asume elecciones limitadas sobre los vértices y el límite de las elecciones es el límite de la reducción de complejidad 

El **grado** se define como el número de líneas que inciden con un vértice, entonces, a mayor número de grado de cada uno de sus vértices, se comprende una mayor densidad en la red. El promedio de los grados permite una forma alternativa de medir la densidad de la red. Los grados pueden ser de tres tipos: 
+ partiendo del presupuesto que dos vértices son adyacentes si están conectados por una línea entonces
	+ Los in grados es el número de líneas que recibe un vértice
	+ los out grados es el número de líneas que envía 
	+ en el caso de no tenerse en cuenta esta diferencia, el grado correspondería con el número total de líneas que lo conectan con vértices adyacentes 

Para medir el grado en Pajek se recomiendo *simetrizar* la red, lo que significa transformar todos las líneas unidireccionales en bi-direccionales. Esta simetrización modifica la salida del comando de densidad: si se tiene en cuenta bucles y líneas múltiple , y si no las tiene en cuenta.  Los grados de los vértices de una red tienen la forma de una partición de un atributo discreto.  
#### componentes 

A las **partes conectados** de una red se la llama **componentes**, de esta forma los grupos aislados pueden ser considerados sub grupos cohesionados en un primer vistazo. 

Para definir los componentes de una red debemos abordar conceptos que hacen precisión sobre la forma en que un par de vértices están conectados. Aquí debemos tener en mente el concepto de *walk* y *semi-walk*, ambos surgen de la pregunta acerca de cómo un vértice puede conectar con otro. Un *semi-walk* de un vértice ``a``  hacia otro ``b`` se define como la secuencia de líneas tal que el vértice final de una línea sea el vértice inicial de la siguiente línea donde la secuencia comienza en un vértice ``a`` y termina en un vértice ``b``. Un *walk* añade una condicional: se respeta la dirección de la línea. 

No obstante, estas definiciones admiten soluciones infinitas porque no hay infinitas posibilidades de ir de un punto a otro. Por lo tanto, para eliminar la redundancia del *walk* y *semi-walk* debemos recurrir a otro concepto: *semi-path*  y *path*. 

un *semi path* es un *semi walk* en donde ningún vértice entre el primero y el último vértice de un *semi walk*ocurre más de una vez; de la misma forma un *path* es  un *walk* donde ningún vértice entre el primero y el último vértice ocurre más de una vez. 

Una red, por lo tanto, está conectado (débilmente) si cada uno de las vértices están conectados hacia todos los demás por , por lo menos, un *semi path*. En cambio, un componente fuerte existe en la medida en que un par de vértices estén conectados por un *path*. Un componente débil es la máxima sub grupo conectado débilmente, en cambio, un componente fuerte es la máxima sub grupo conectado fuertemente. El adjetivo máximo significa que la sub red abarca todos los vértices de tal manera que cualquier añadido alteraría esta propiedad. 

Sólo las redes direccionadas pueden diferenciar entre componentes fuertes y débiles; en redes sin dirección los componentes sólo revelaran si existe una parte de la red está desconectado entre si. En un aspecto interpretativo el uso de los componentes dependen de si consideramos que es **relevante el orden y la dirección de los actores para explicar el fenómeno social**. 

Una vez aplicado el comando en Pajek se devuelve una partición que permite identificar, en cada clase, el sub grupo al que pertenece. 

#### Cores

Para identificar los cores se usan los grados de los vértices que están conectados; en un clúster los vértices tienen un particular mínimo grado dentro de él. Estos clúster son los llamados K core y la K representa el mínimo grado de cada vértice en el core. Se recomiendo el uso de los K cores en redes no direccionadas debido a la complejidad explicativa. 

Los K cores están anidados, es decir, si existe un vértice con un K core mayor a uno , significa que ese vértice también pertenece a un K core igual a uno. Los sub grupos K en los K cores pueden no estar conectados, esto hace posible remover los K cores de una red hasta que esta se 'rompa' en componentes aislados y relativamente densos entre ellos 
##### Una definición paso a paso

la definición formal de K core es **la máxima sub red en la cual cada vértice tiene , por lo menos, un grado de k dentro de la sub red**. Esto es cierto, no obstante, surge la pregunta de como se forman los componentes y si esto no cae en la arbitrariedad. Por ello es necesario una definición más descriptiva, así, **un sub grupo K core no está conformado por todos los nodos incidente de cada vértice en el grupo sino por todos los nodos incidentes que cumplan con la condición de compartir un grado mínimo y que, por lo menos, los nodos adyacentes que hacen que el primer vértice cumpla su grado mínimo, a su vez, cumplan con la misma condición**. De lo contrario, el nodo adyacente no será tomado en cuenta para aumentar el grado del vértice analizado. 

#### Cliques y sub redes completas 

Los cliqués son conjunto de vértices donde cada vértice está directamente conectado con todos los demás vértices, formando un sub red completa, es decir, es una sub red con máxima densidad. Las sub redes competas de dos vértices no son tan significativamente relevantes como las compuestas por tres vértices o más. En suma, el cliqué es una sub red completa de total densidad que será usada para extraer a partir de ella los vértices de otra red que cumple con la característica estructural del cliqué. 

En el análisis de redes sociales los vértices que se sobre ponen con más de una sub red completa se les considera las secciones más densas ya que conectan sub redes con otras sub redes, constituyen el esqueleto de la red. Los vértices más densos pueden ser clasificados en diferentes clases y a esta clasificación se le denomina jerarquía. 

### Sugerencia 

En Pajek tenemos disponibilidad para hacer uso de diferentes pruebas para detectar  sub grupos cohesionados al interior de una red. No obstante, no podemos concluir que el resultado de una prueba se traduzca en la existencia de una grupo cohesionado en la realidad, se deben contrastar los datos estructurales con los atributos de cada uno de los actores.

## Sentimientos y amistad

Los análisis en ARS permiten aplicación en los afectos de un grupo de personas, es posible entonces distinguir entre valoraciones positivas y negativas, por lo tanto se espera vínculos positivos dentro del grupo y vínculos negativos entre grupos. 

Para comprender estos patrones de afectividad se acude a la teoría del balance, estos vínculos no tienen una constatación empírica más allá de la comunicación de una relación. Se asume que procesos sociales más amplios explican las conductas particulares, desde la teoría se sostiene que **una persona se siente incómoda cuando desacuerda en un tópico con un amigo**, por lo que sentirá presión por cambiar esa situación de desbalance.

Pajek ofrece una red especial para expresar las estructuras de afectividad, estos son los grafos señalizados, los cuales tienen **en cada línea un signo positivo o un signo negativo**. Para ingresar el concepto de balance debemos introducir el de ciclo. Cada ciclo es un *path* cerrado diferenciado de otro al no compartir vértices o actores entre sí. Podemos decir entonces que un ciclo está balanceado cuando: 1) existe un número par de líneas negativas o 2) no existe ninguna línea negativa en el ciclo. Las redes señalizadas están mejor diseñadas cuando estas son direccionadas, esto es debido al carácter unidireccional del vínculo afectivo. 

La teoría parte del punto de vista o percepción de una persona 




