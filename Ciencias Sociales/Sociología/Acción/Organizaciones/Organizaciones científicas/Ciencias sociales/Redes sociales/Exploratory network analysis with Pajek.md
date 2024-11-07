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

#### Sugerencia 

En Pajek tenemos disponibilidad para hacer uso de diferentes pruebas para detectar  sub grupos cohesionados al interior de una red. No obstante, no podemos concluir que el resultado de una prueba se traduzca en la existencia de una grupo cohesionado en la realidad, se deben contrastar los datos estructurales con los atributos de cada uno de los actores.

## Sentimientos y amistad

Los análisis en ARS permiten aplicación en los afectos de un grupo de personas, es posible entonces distinguir entre valoraciones positivas y negativas, por lo tanto se espera vínculos positivos dentro del grupo y vínculos negativos entre grupos. 

Para comprender estos patrones de afectividad se acude a la teoría del balance, estos vínculos no tienen una constatación empírica más allá de la comunicación de una relación. Se asume que procesos sociales más amplios explican las conductas particulares, desde la teoría se sostiene que **una persona se siente incómoda cuando desacuerda en un tópico con un amigo**, por lo que sentirá presión por cambiar esa situación de desbalance.

Pajek ofrece una red especial para expresar las estructuras de afectividad, estos son los grafos señalizados, los cuales tienen **en cada línea un signo positivo o un signo negativo**. Para ingresar el concepto de balance debemos introducir el de ciclo. Cada ciclo es un *path* cerrado diferenciado de otro al no compartir vértices o actores entre sí. Podemos decir entonces que un ciclo está balanceado cuando: 1) existe un número par de líneas negativas o 2) no existe ninguna línea negativa en el ciclo. Las redes señalizadas están mejor diseñadas cuando estas son direccionadas, esto es debido al carácter unidireccional del vínculo afectivo. 

La teoría parte del punto de vista o percepción de una persona (P) y lo que piensa acerca de otra persona (O). El balance estructural de una red de sentimientos se interesa por todos los sentimientos de los miembros del grupo hacia cada uno de los miembros del grupo. El balance tendrá en cuenta todos los patrones de los vínculos de afecto en un grupo social.

Los grafos señalizados puede ser : ==balanceados o clusterizables==. Para que un grafo sea balanceado la red puede ser 'partida' en dos clúster de modo que todas las líneas positivas están contenidas en un clúster y todas las líneas negativas están localizadas entre los clúster. Cada uno de los semi ciclos deben estar balanceados. Y un grafo es clusterizable si se cumple las condiciones de una red balanceada con el añadido que pueden existir más de dos clúster. La clusterabilidad se refiere  la capacidad que tiene un ciclo o un semi ciclo de conformar el mismo un clúster. 

### Encontrando el balance

Preguntarnos por el balance nos deriva hacia una cuestión mucho más profunda, a saber, el conflicto y la inestabilidad. Es entonces condición sine qua non de las clúster balanceados su conflictos con otros en esa misma condición, ==la condición del balance es el conflicto==.  No obstante, la teoría del balance hipotetiza que en el transcurso del tiempo las relaciones de afecto tienden a estabilizarse, siendo la estabilización interna producto de un intenso periodo de polarización social.

En redes señalizadas sin particiones previas debemos generar un clúster y escoger la partición donde menos número de líneas no permitidas existan. El número de líneas no permitidas constituyen el grado de balance de una red señalizada, y su uso permite escoger la mejor distribución de particiones. 

#### técnica de optimización

Para encontrar la mejor partición se debe reorganizar los clúster hasta encontrar la mejor solución, en dicho proceso pueden que se encuentren algunas soluciones que encajan igualmente bien, aunque ninguna de ellas sea el mejor orden posible. Dependiendo del número de clúster a encontrar se pueden generar diferentes resultados, es difícil determinar el número de clúster que producirá el menor número de score negativo, teniendo en cuenta que los valores de línea no permitidos, sean negativos o positivos, pueden tener pesos diferentes.  En Pajek la partición ingresada junto con la red indica el número de clúster a encontrar y el primer clúster que el algoritmo intentará descifrar y mejorar. 
## Afiliaciones 

Hasta ahora hemos tratado con redes sociales cuyos actores eran de un sólo tipo: personas o organizaciones. No obstante, para examinar con mayor agudeza algunas 'realidades' sociales es necesario contar con ambos tipos de actores; un ejemplo son las **afiliaciones**, es decir, la pertenencia de un actor a una organización. En base en los desarrollos de George Simmel, podemos llamar **círculo social** al grupo de personas que se reúnen alrededor de una o más organizaciones y eventos. La afiliación es por lo tanto una relación entre personas y organizaciones en el que se manejan varios presupuestos:
+ La afiliación siempre se observará en una membresía en una 'institución' que explicite un rasgo estructural
+ La afiliación como el cómputo total de estas presentes en una organización revelan el *arreglo* institucional, es decir, las decisiones sobre la expedición de membresías expresa el funcionamiento de una organización
+ Una organizaciones expide decisiones sobre afiliaciones y los afiliados interactuarán al interior de la organización unos con otros con igual posibilidad
	1) Los afiliados en una organización tenderán a compartir similaridad en otros contextos sociales 
	2) Diferentes organizaciones pueden sobreponerse en sus afiliados debido a que las personas en un círculo social adscriben a más de una organización
### redes de 2 modos y de 1 modo
enfocado en el análisis de vaoleres de linea (line value)

Una **red de afiliación** es una con , por lo menos, dos conjuntos de vértices , donde sólo un conjunto de vértices puede interactuar con el otro; de tal forma que las interacciones entre el mismo conjunto de vértices no están habilitadas. Estos dos conjuntos de vértices reciben el nombre habitualmente de *actores y eventos*. Estos tipos de redes son definidas como **red de 2 modos**, formalmente definida como: una red donde *los vértices son divididos en dos conjuntos y los vértices solo pueden ser conectados con otros del conjunto restante*. El primer conjunto es referido como **filas** y el segundo como **columnas**    

#### conceptos red de 2 modos

Algunos conceptos en redes de 2 modos no pueden ser interpretados de la misma manera que en redes de 1 modo. Para el grado del vértice se introducen dos nuevas distinciones: **tamaño del evento** para indicar el número de vecinos de un evento descontando líneas múltiples y bucles, y **puntaje de participación** para indicar el número de vecinos que tiene un actor descontando líneas múltiples y bucles. Debido a la 'naturaleza' muy diferente de estos dos conjuntos de vértices el grado de un actor o evento debe tener formas de interpretación distintas, de la misma forma el modo en que se mide la densidad de una red será distinta. 

Debido a la complejidad asociada a la medición de redes de 2 modos , el abordaje sobre este tipo de redes no se hará conservando la forma de red de 2 modos. En cambio se optará por la transformación de redes de 2 modos a redes de 1 modo, por lo tanto, tendremos como resultado dos redes de 1 modo, la red de 1 modo de los actores y la red de un modo de los eventos. Cada vértice tendrá un valor de bucle que indicará **el grado en la red de 2 modos** , a su vez, los vértices de actores o eventos se transforman en líneas cuyo valor será **el total de vértices que compartían en la red de 2 modos**. Esto deriva en que en cualquier transformación de una red de 2 modos a una red de 1 modo obtendremos una red no simple. Las líneas múltiples generadas serán remplazadas por una línea con el número original de las líneas entre dos vértices. Dada la transformación será responsabilidad del investigador saber  que vectores representa cada unidad en el valor de la línea.   

Como advertencia cabe mencionar que debido a esta poca claridad respecto a las etiquetas de los vértices transformados en unidades en los valores de las líneas, en estructuras rígidas como cliqués no se puede sino concluir que se comparte en dicho cliqué uno o más actores o eventos, no siendo posible, salvo por un análisis manual, conocer el número de actores diferentes en un cliqué. 

### m-Slices o islas

Una vez tenemos una red de 1- modo ya sea con las *filas o columnas* es relevante conocer entre dicha red las grupos de nodos mejor cohesionados entre sí. La técnica de extraer una sub red de otra sub red completa para, por ejemplo, extraer los cliqués y observar una estructura cohesionada. No obstante, al manejar una red reducida añade varias problemas interpretativos que hacen impracticable esta forma de observar la cohesión de un grupo. Debido a la dificultad de conocer las etiquetas de cada línea (antiguo actor) no se puede sino concluir que *en estructuras rígidas como cliqués solo se puede saber en que se comparte uno o más actores o eventos, sin especificar su número*

Ante esta dificultad se desarrolla una nueva noción, introducida por el sociólogo John Scott, se m-Slices o **islas**. Se mantiene el concepto islas en la primera edición del libro y en la última de islas. El concepto de **isla** se refiere a un *grupo cohesivo sobre la base de líneas múltiples en vez de en su número de vecinos*. Formalmente la isla se describe como **la máxima sub red de vértices conectados directa o indirectamente por líneas con un valor mayor que las líneas hacia otros vértices afuera de la isla**. Así una isla es un técnica para descubrir grupos densamente conectados.    

### Comunidades 

Introducidos en la tercera edición se refiere a las 'comunidades' detectables gracias a los *comunity detection methods*. Estas técnicas entiendes una comunidad como *clúster de vértices para los cuales la densidad de las líneas al interior del clúster es mayor que la densidad de las líneas entre los clúster*. 

En Pajek están integrados dos métodos de detección de comunidades: **Louvain method** y **VOS quality method**. Ambos buscan la partición de vértices en clúster con el mayor valor de modularidad (o VOS quality función). La modularidad es una popular medida para comparar líneas y sus valores de línea afuera y dentro del clúster. También existe el **external internal index** que mide, en un rango que va desde $-1$ hasta $1$ , el grado en que se respeta la afirmación : ==en un clúster los vértices están más conectados entre si que entre otros clúster==. 

# Part 3: Brokerage

La relación social es comprendida mediante la **metáfora del canal**. la red de ese canal permite identificar a quien le llega y a quien le tarda en llegar y a quien no le llega en absoluto. Mediante esta red se transmiten información, servicios y clientes. Se analiza la posición que ocupa un nodo en la red donde estar conectado suele ser ventajoso: 
+ sociabilidad: número e intensidad de líneas de una persona 
+ centralidad: nodos cruciales para la transmisión 
El análisis de redes estudiado y posibilita en Pajek está centrado en el intercambio de información donde la dirección de los vínculos no es importante en la mayoría de los casos 
## Center and periphery

Aquí se abordan dos conceptos: centralidad y centralización. y refiere a la existencia de actores y organizaciones que son centrales, por tanto, con mejor acceso a la información y mejores oportunidades de esparcir información. La **centralidad** es un acercamiento ego céntrico a la posición de vértices individuales en una red. La **centralización** es una perspectiva socio - céntrica al caracterizar la red en su totalidad. Básicamente, la centralidad se refiere a los actores y la centralización a la red. 

El concepto de centralidad permite el desarrollo de la **distancia** cuando percibimos que la información llega más fácil a aquellos nodos más centrales; este concepto indica el *número de pasos o intermediarios necesarios para alguien para alcanzar otra persona en la red usando la distancia más pequeña entre dos vértices*. La medida de centralidad de un vértice es el grado, es decir, el número de vecinos. ¿ Cual sería , entonces, dado un número de líneas, la estructura más eficiente para intercambios de información de un vértice ? ==esta sería un red donde un vértice está conectado con todos los vértices sin que estos estén conectados entre si== (a este tipo de red se le conoce como *start net* e indica el mayor grado en todas las medidas de centralidad); debido a esto, una red presenta mayor índice de centralidad si los vértices individuales varían más de la su máxima centralidad, una mayor variación de este puntaje produce una red más centralizada. 

**El porcentaje de centralización** puede ser calculada como la variación en los grados de los vértices respecto al máximo disponible en la red dividido por el máximo grado de variación que es posible en una red del mismo tamaño. 

La **variación** se define como la diferencia absoluta entre el puntaje de centralidad de los vértices y el máximo puntaje de centralidad (grado de un vértice) entre dicha red de nodos. 

así podemos expresar la variación total como: $\sum(\text {max }V_n-V_n),\text {siendo } V_n \text { el grado de cada vertice}$   

y el cociente de centralización se expresa: $\huge \frac{\sum(\text {max }V_n-V_n)}{max V_n}$

los resultados varían entre 1 y 0 ; la obtención de la unidad indica máxima variación de la totalidad menos uno de los vértices, los valores que descienden hasta 0 indican una menor centralización de la red, en el valor más bajo indica que no existe centralización, por lo tanto, todos los vértices son igualmente centrales. Dado que en redes direccionadas el número de vecinos puede variar se recomienda trabajar con redes no direccionadas en aspectos de la realidad social donde las relaciones sea bidireccionales. 

### Closeness centrality

Volviendo al concepto de distancia. Decimos que una persona es alcanzable si hay un camino (path) entre el primer y el último vértice. La forma de referenciar el número de pasos en el camino más corto es llamado *geodesic*, así, la **distancia desde el vértice $u$ al vértice $v$ es del tamaño del geodesic entre $u$ a $v$**.

Con este concepto de distancia podemos medir un **nuevo índice de centralidad considerando las distancias en lugar del grado** . Así la medida de *closeness centrality* de un vértice es el número total de los demás vértices dividido por la suma de todas las distancias entre el vértice y todos los demás vértices. A su vez el cociente socio céntrico de *closeness centralitation*  es la suma de las variaciones en closeness centrality de los vértices dividido por la máxima variación posible del puntaje de closeness centrality en una red del mismo tamaño (mismo número de vértices). Debido a que en una red direccionada un vértice es imposible de alcanzar al otro salvo que dicha red sea fuertemente conectada, se recomienda trabajar con redes no direccionadas. 
### Betweenness centrality
Las anteriores medidas de centralidad están basadas en la "alcanzabilidad" de un actor al interior de una red. Un enfoque diferente vendría de la asunción de que una persona es más central si es más importante como un intermediario en una red de comunicación, esto viene a responder la pregunta de en qué extensión una persona controla el flujo de información.  Por tanto, un actor **que está situado en el geodesic entre muchos pares de vértices es muy importante para el flujo de información dentro de la red**. La medida de *betweennnes centrality*  de un vértice es la proporción de todas las geodesics (sin contar que empiezan o terminan en el vértice medido) entre pares de otros vértices que incluye este vértice en su geodesic. 
En una medida socio-céntrica *betweennnes centralitation* es la variación en el *betweennnes centrality* de los vértices dividido por la máxima variación en *betweennnes centrality* puntaje en una red del mismo tamaño. Un máximo puntaje  *betweennnes centrality* indica que si el vértice central desaparece entonces todos los geodesic quedan destruidos. En cambio obtener 0 indicaría en que no existe mediación entre un par de vértices 
### Eigenvector centrality 
Esta medida de centralidad asume que un vértice es más central si tienes más relaciones directas , y especialmente si estos vértices con los que existen vínculos directos son más centrales. La anterior abstracción emerge de la creencia en que es importante conocer más personas , en especial, las mejores personas. La medida de **Eigenvector centrality** de un vértice es una extensión para la cual sus vértices conectados cuentan con un alto valor en Eigenvector centrality. En una media socio céntrica el **Eigenvector centralitation** indica la variación en el Eigenvector centrality de los vértices dividido por el máxima variación en Eigenvector centrality puntaje posible en una red del mismo tamaño. 

Al aplicar esta medida a una red direccionada se derivan dos conceptos adicionales: *hubs* como vértices que son importantes enviadores, y *autoridades* como vértices que son importantes recibidores. En Pajek el investigador determina el número de hubs y autoridades que serán seleccionadas. En una red no dirigida no existe una distinción entre hubs y autoridades, por lo que sus resultados (como .vec) son idénticos. 
### Assortativity 

Producto de un artículo publicado por M.E.J Newman, aduce que los actores con un alto grado de vecinos tienden a estar conectados con actores con un alto grado de vecinos. mientras que las personas con un bajo grado de tienden a estar conectados con personas con un bajo grado de vecinos. Este fenómeno es llamado *degree Assortativity* y toma valores entre 1 para la máxima correlación y -1 para la correlación inversa. La conceptualización de estar relacionado, en preferencia, con alguien similar, en análisis de redes, está dividido en dos conceptos: Assortativity cuando la similaridad se da con respecto a una propiedad numérica de un actor; y *homophily* cuando la similaridad se da respecto a una propiedad categorial de los vértices. 

La similaridad se puede entender como una asociación , y entre variables numéricas se requieren otras mediciones que el cálculo de la similaridad entre variables categoriales. 

A la similaridad entre dos variables numéricas entre actores conectados  se conoce como *Assortativity coeficiente*, e indica la correlación entre una o dos propiedades numéricas en los vértices que están directamente conectados. Los resultados toman valores entre 1 para indicar una  Assortativity positiva, es decir, una relación (alto-alto) ; y -1 para indicar una relación negativa (alto-bajo), este último es útil para medir relaciones de simbiosis asimétrica.     

En redes no direccionadas el cálculo de la Assortativity  usará la misma propiedad numérica de ambos vértices que están conectados; así un par de vectores conectados tendrán una relación de intercambio bidireccional. En cambio, para redes direccionadas podemos distinguir entre actores enviadores y actores receptores, donde un vértice que envía está relacionado (y conectado) con el que recibe, pero no necesariamente en viceversa; así en el grado podemos distinguir entre input y output, en un vector habrán un número de vecinos diferente diferentes para cada vértice dependiendo de la dirección de los otros vectores incidentes limitando el número de relaciones para la correlación, y en dos vectores , uno de ellos toma la posición de envidador y otro el de receptor.

En Pajek, existe una excepción para este cálculo:  una propiedad categorial (.vec) dicotómica puede ser usada y Pajek la interpretará como tal. Si la categoría no es dicotómica Pajek la tratará como propiedad numérica. 
## Bridge and Brokerage

Los vínculos de una persona y nuestros son importantes en una red social, el análisis de redes descubrió que la clase de este vínculo es más importante que el número total de vínculos. Existen personas que ayudan a 'puentear' huecos estructurales, como los que existen en las redes de comunicación informal donde un actor puede conectar dos sub grupos poco conectados entre si.

### Bridges and Bi component 

Los vínculos sociales son importantes para la difusión de información (si estamos en un organización toma más importancia la importancia de las estructuras informales), asumiendo esto podemos (y debemos) preguntarnos acerca de si existen posiciones en la red vitales para la difusión o si son usadas estas posiciones para beneficio personal

Podemos decir que una línea es un puente si al 'cortarse' o desaparecer se genera una componente aislado; por tanto, un *puente* es una línea que una vez removida aumenta el número de componentes de una red. Por otro lado, remover un vértice de una red significa que el vértice y todas las líneas incidentes con el vértice son removidas de la red, se le llama *cut vertex* o *articulation point* al vértice cuya eliminación incrementa el número de componentes de una red. 

#### Bi component
 Un bi componente es simplemente un componente de tamaño mínimo tres y máximo sin un *cut vertex*. Dentro de cada bi componente cada actor recibe información de , por lo menos, dos fuentes diferentes, existiendo por lo menos dos paths hacia el vértice. Puede ser una sub red débilmente conectada de una red que en su conjunto total no podría considerarse un bi componente, esto se debe a que un bi componente no contiene cut vertex si se observa sólo al interior de él e se ignora el resto de la red. Los cut vertex son buenos indicadores de los bordes de un bi componente o puentes. 

Siguiendo la teoría *la fuerza de los vínculos débiles* podemos interpretar estos como puentes ya que atraviesan las fronteras grupales. Ser puente es sólo un proxy de sus oportunidades de ser un puente en una red. No obstante, el investigador es quien debe decidir que interpretar como vínculo débil en su investigación. 

En Pajek es posible encontrar los bi componentes de una red y los resultados varían respecto del número mínimo que ingresos como número mínimo en el tamaño del bi componente, Si indicamos un valor mínimo de 3 solo se reportarán los cut vertex que conectan dos o más bi componentes. Por otro lado, si indicamos un valor de 2 se reportarán todos los bi componentes y puentes. Los resultados se guardarán en el apartado de jerarquía ya que un sólo vértice puede pertenecer a varios bi componentes. 

Puede surgir la pregunta de porque existen un bi componente de tamaño dos, esto se debe a que intermedia entre dos bi componentes. Al interior de un bi componente no pueden existir puentes, esto se debe a que un bi componente lo conforma la máxima sub red posible donde se cumpla la condición de la no existencia de un cut vertex, sólo en un puente , es decir, entre una linea que uno dos vértices de bi componentes distintos, el número de vértices no podría aumentar sin que aparezca un cut vertex. 

### Ego network y constraint 

Los puentes y los cut vertex son mediadas socio céntricas que observar la totalidad de la red. No obstante, el *ego centered approach* se enfoca en la medición de una persona o actor en la red y sus posibilidades de intermediar entre otras personas (bróker) 

Para analizar las relaciones de intercambio (o su posibilidad) se usan las triadas, que es la red más pequeña que tiene dos personas o más e puede iluminar los vínculos al interior de un grupo. Con base a teorías psicológicas y sociológicas se reconoce que una conexión completa de tres personas (o sea, un cliqué) derivan en comportamientos grupales mas que individuales, todos ellos se comportan similarmente al compartir normas e información. No obstante, si esta conexión no es completa puede desarrollarse una *tertius strategy* que consiste en inducir y explotar una competición o rivalidad entre otros dos actores que no están directamente conectados, en esta situación son aprovechados los *estructural holes* entre los vértices no conectados dando un control sobre el flujo o corriente de una red. 

Por otra parte, para evitar crear y caer en *estructural holes*, existe una *constraint* (limitación) que significa que no puedes remover ningún vínculo sin crear un *hueco estructural* alrededor de si, por tanto, estamos obligados a mantener sus vínculos. 

Una red egocéntrica, necesaria para calcular la intermediación personal, de un vértice contiene este vértice, sus vecinos y todas las líneas entre los vértices seleccionados. Con esta disposición de la red se analiza la red como un conjunto de triadas , y por cada triada podemos determinar si 'limita' a ego o si, por el contrario, contiene un hueco estructural que puede ser explotado. Como resultado se indicará que una baja 'limitación' indica la existencia de varios agujeros estructurales y viceversa. 

¿Cómo se definiría esta 'limitación' o *diadic constraint*?  Sobre un vértice $u$ ejercida por un vínculo entre vértices $u$ y $v$  es la medida en que $u$ tiene más y más fuertes vínculos con vecinos que están fuertemente conectados con el vértice $v$ . Esta es la idea conceptual detrás del estricto cálculo; para conocer las variables del cálculo es importante abordar el concepto de *fuerza proporcional*, este se define con respecto a un vínculo con respecto a todos los vínculos de una persona , es computado como el valor de la línea que representa el vínculo, dividido por la suma de valores de todos las líneas incidentes con una persona, ==el cálculo del valor de la línea es especialmente importante cunado este valor representa cantidades o distancias==.  Este cálculo es la simple indicación de la importancia o exclusividad de un vínculo. Como resultado Pajek arrojará , sin importar la naturaleza de la red recibida, una red simple directa y que contiene sólo arcos bidireccionales con el valor de aportación de un nodo a otro nodo. Una vez tenemos esto podemos calcular el  *diadic constraint* a través del cuadrado de la suma de la inversión más la proporción diádica de 'limitación' entre todos los vértices que cumplen la condición de limitación para el nodo que 'invierte'

Luego del cálculo en cada línea queda impreso su *diadic constraint* con cada nodo incidente, para conocer que nodos están más limitados que todos en su conjunto podemos calcular el *agregado de limitación* que indica la suma de todos los valores de *diadic constraint* de una persona, toma valores entre 1 y 0, un mayor valor indica menor libertad para remover una línea y viceversa. Esta medida en Pajek sale como una archivo .vec

Las líneas directas directas entre vecinos de ego aumentan la coacción, por lo que analizar la densidad entre ellos nos daría una idea de lo limitado que está un actor, a esta mediada se la conoce como *densidad de red personal* que no es más que la densidad de todos los vértices incidentes de ego entre ellos, sin contar con ego, un proporción de las líneas existentes entre las líneas posible

En Pajek un sólo comando computa la fuerza proporcional de los vínculos, la diadic constraint y la limitación agregada, este es el *structural holes* que devuelve múltiples archivos.

### Afiliaciones y Brokerage roles

Dentro de una red social el cálculo de bi componentes , puentes , oportunidades o limitaciones de intermediar es posible , y es esperable, que sea aplicable a un grupo social amplio para detectar esos puntos importantes que median entre otros sub grupos más pequeños. No obstante, también se pueden extender estos análisis al interior de un grupo en particular para conocer las 'limitaciones' de los nodos al interior del grupo, esta medida puede indicar que tan posible es que un liderazgo al interior del grupo sea remplazado, para ello el nodo que lo remplazaría debe tener un limitación más baja y los nodos que u actores que harán el cambio deben jugar el *tertius strategy* entre el nodo a remplazar y el nodo que lo va a remplazar, estos dos nodos cruciales no pueden estar directamente conectados. Las red debe ser procesada para que no existe ninguna línea entre grupos, luego se aplica de nuevo el comando de *structural holes* y se obtienen los mismos archivos. 

En una red con una división de grupos ya establecida es posible establecer roles al interior de la misma según su posición y partición correspondiente. Para el establecimiento de roles se parte de una triada que no constituya un cliqué, una triada donde una persona $v$ media entre una persona $v$ y una persona $w$ puede mostrar **cinco patrones** de roles en la afiliación diferentes, estos son : 1) coordinador, broker itinerante,  representative, gatekeeper, iliasion. (luego insertar explicación de cada uno)

Los resultados del análisis de roles de una red (o actor particular, el resultado devuelve la cantidad de veces que cumple un rol) puede ser comparado con otras características para determinar si ciertas tipos de actores o tipos de relación social desarrollan tipos particulares de *brokerage roles*
# Part 4 : ranking
## Genealogías y citaciones 
### genealogías 
==El tiempo es responsable de un tipo especial de asimetría en una relación social porque ordena los eventos y generaciones de una forma irreversible==, la identidad social y la posición en una estructura social es parcialmente fundada en ancestros comunes, ya sea en una cuestión intelectual como las citaciones como en un enlace biológico. Una tradición puede ser definida por un **común conjunto de ancestros , por un reenlace estructural o por co citación en largos periodos de tiempo**. 

En el manejo de redes genealógicas estas toman la nomenclatura de **ore graph** donde los *arcos siguen el flujo de tiempo*. Existen dos tipos de líneas que indican dos clases de 'familia': familia de hijos u orientación y familia de esposa o procreación. Cuando importamos esta base de datos familiares, usualmente en formato GEDCOM, Pajek genera diferentes vectores y particiones que corresponden con cada uno de las personas en la red. A partir de toda la información disponible podemos , por ejemplo, obtener medidas con los clúster de hermanos , con los particiones de hombres y mujeres, con las ramas o linajes , con los descendientes  y con el cálculo de geodesics. Algunas conceptos o categorías de la teoría del parentesco pueden ser encontrados con el uso inteligente de matrices multiplicativas, siendo la propia genealogía una matriz. 

Uno de los conceptos centrales en la investigación de grupos o secciones cohesionadas al interior de una genealogía son los *reenlaces estructurales*, esta concepto remite al fenómeno en que las familias se casan más de una vez en el curso del tiempo, indicando si existen matrimonios de sangre o no; este factor endógamo  es un indicativo de cohesión social al interior de la genealogía.

Para distinguir en una red ore graph entre semi-ciclos que representan enlaces estructurales y aquellos que no fue desarrollado un nuevo tipo de red: parentage graph o P graph.  En un P graph cada vértice es una pareja o un soltero , por lo tanto, se reduce significativamente el número total de vértices y , debido a la eliminación de la línea entre esposos y que no existen arcos separados de padres a hijos, la red es acíclica. En un definición formal decimos que un **tree** es un grafo conectado que no contiene semi-ciclos, varios de estos grafos , siguiendo la metáfora, conformarían un **bosque**.  En Pajek existe la medición *relinking index* para medir el nivel de enlace, la medición arroja un valor que puede variar entre 0 y 1, indicando, respectivamente, mínimo reenlace y máximo reenlace. 

En Pajek la manipulación de complejas redes genealógicas transita a través de funciones de partición por segmento, binarización y extracción. No obstante, para facilitar la manipulación de los datos se insta a usar herramientas  distintas a Pajek. 
### citaciones 

Las redes de citaciones pueden develar tendencias, cambios y grupos especializados en el conjunto de publicaciones científicas disponibles en un sistema que transforma conocimiento o información científica. En este capítulo se aborda una técnica especial para análisis de citas con un enfoque en el flujo de tiempo llamado *main path analysis*. Las más importantes citaciones constituyen uno o más caminos principales que son probablemente el andamiaje de una tradición investigativa. El main path analysis calcula la **medida en la cual una particular citación o artículo es necesario para unir artículos**, esta medida de la 'necesidad'  se mide en el *peso transversal* de cada artículo o citación. 

Esta es una medida que funciona en una *red direccionada acíclica* la cual , para efectos de nuestro análisis, clasifica los vértices en: vértices fuente para aquellos vértices que contienen cero *indegree*  y los vértices sink como aquellos con cero *outdegree*. Una vez se identifican los vértices sink y fuente puede calcularse el peso transversal del vértice o arco como la **proporción de todos los caminos entre todos los caminos entre los vértices (fuente-sink) que contiene o interviene el vértice al que se le calculará el peso transversal**. 
El peso de un vértice puede formularse así: $\huge\frac{\text{número de caminos que pasan por el vértice}}{\text{total caminos desde la fuente hasta el sink}}$ Donde cada valor de línea de un camino entre un nodo y otro se formula como: $\huge\frac{n}{\text{Total de caminos desde el vértice hasta todos los sink}}$ , no obstante, si dos caminos pasan por la misma línea direccionada (arco) entonces la línea duplica su valor, así el valor $n$ toma el valor de los caminos que pasan por un arco.

Por lo tanto, en una red de citaciones, **el camino principal es el camino desde un vértice fuente a un vértice sink con el mayor peso transversal en sus arcos y vértices**. 

==Una vez ya se ha calculado el peso transversal de vértices y arcos en una red de citaciones== , podemos extraer el *main path* usando algunos métodos propuestos e integrados en Pajek:

1) *Forward local main path search*: se selecciona vértices fuentes a los que inciden con arcos del mayor peso, se repite este proceso hasta alcanzar un sink vértice
2) *Backward local main path search*:  se selecciona uno o más sink vértices que inciden con arcos y vértices del mayor peso más en sentido contrario a la dirección de la línea, se repite este proceso hasta alcanzar las fuentes
3) *Key-route local main path search*:  Seleccionamos un limitado número de arcos (por ejemplo diez). Estos son los arcos o vértices con el mayor peso transversal. Los arcos seleccionados son llamados key-routes y no necesitan incidir ni con vértices fuente o sink. Para cada key-routes encontramos el camino principal desde un vértice fuente al key-routes y desde el key-routes al vértice sink. El resultado consiste en el camino principal obtenido por todos los key-routes. 

Estos tres métodos definidos son llamados *local main path methods* porque al ejecutarlos buscamos **sólo localmente para el actual arco en cada paso, sólo chequeamos arcos que son incidentes con el actual vértices (cualquiera sea el método de selección) y con la correcta dirección (también definido por el método)**

En contraste con los métodos de búsqueda local , el global main path method busca los caminos con la mayor suma total de pesos transversales en toda la red. Algunos métodos globales ofrecidos por Pajek son: 

1) *Estándar global main path*: es el camino desde la fuente al sink vértice con la mayor suma general de pesos transversales en cada arco y vértice por donde pasa el camino. También a esta medida se le conoce como *critical path method* (CPM) 
2) *Key-routes global main path*: Empezamos con algunos arcos como key-routes, para cada key-routes buscamos el camino principal que contiene el key-routes desde el vértice fuente hasta el vértice sink con el mayor peso transversal general de la red. Aunque es usual seleccionar algunos arcos (citaciones) con el mayor peso transversal son seleccionados como key-routes, esto no es necesario.

Si queremos extraer un componente de camino principal en la red de citaciones podemos seguir los siguientes pasos, se elige un valor de corte entre 0 y 1, para luego remover todos los arcos de la red con un peso transversal menor a este valor seleccionado. Repetimos este proceso hasta encontrar el valor más bajo que , a su vez, produce un componente que conecta, al menos, un vértice fuente con un vértice sink. 

Como consideración metodológica Pajek ofrece la 'normalización' como una medición que no afecta el camino principal extraído de la red de citaciones con los pesos transversales ya computados, sino sólo modifica el rango y la variación entre esos pesos transversales. Otro asunto que merece ser considerado al final de cada análisis: la elección de los artículos incluidos en la base de datos restringe el número y tamaño de las tradiciones investigativas que pueden ser encontradas, se concluye que una red de citaciones es virtualmente incompleta. Por último, en el cálculo de cada medida Pajek pregunta sobre el nivel de tolerancia, este corresponde a una modificación al valor de corte, por lo que una mayor tolerancia significa disminuir este valor de corte.

Ver summary 






