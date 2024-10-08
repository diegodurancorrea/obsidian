---
Fecha_creacion:: 2024-07-09
Ultima_modificacion:: NaN
Nombre_documento:: La fuerza de los vínculos débiles
Tipo_documento:: Artículo 
tipo:: Reseña corta
autor:: Mark Grannoveter
---
# Introducción 
El autor se pregunta por la naturaleza del vínculo entre dos actores al que analíticamente divide en dos clases: **vínculos fuertes** y **vínculos débiles**. El vínculo fuerte no es definido con claridad pero se apunta a un enlace que , por lo menos, sea emocionalmente importante y sostenido en el tiempo.  Los vínculos débiles se definen como su contrario.

El análisis de redes sociales toma como cierta la fructífera metáfora de la [[For a heterodox computational social science#1.1|granularidad]], a saber, que la conexión macro-micro puede explicarse en la extensión de vínculos duales o diadas. La mencionada e importante conexión , en la propuesta del artículo, se enfocará en un aspecto de la interacción de un sistema interpersonal, a saber, en los vínculos débiles.  
## Planteamiento matemático

### formalización de la propuesta

$C_1=\set{A,B}\text{  y  } C_2 = \lbrace{C,D,E}\rbrace$ 

$\text{ Si }A \in C_2\text{ y }B\in C_2 \implies A,B \in C_1 \text{ , donde } C_1 \text { es el grupo emergente conectado por vinculos positivos}$

La formulación corresponde con el principio de **transitividad** y analíticamente puede observarse como una línea que conecta tres actores $\set{A,B,C_2}$ así :

$A\gets C_2 \to B$

Basado en el principio de transitividad la probabilidad del tiempo compartido para la generación de un vínculo $A-B$ positivo se expresa:

$P(a/b)=P(C_2/a)*P(C_2/b)$

Por tal, **la probabilidad de coincidencia es directamente proporcional con los vínculos mutuamente compartidos**. Los actores en este nivel micro sociológico comparten lo suficiente con sus círculos más cercanos para que cada uno sepa de la existencia de otro; por tanto:

1) La línea inicial de la triada se transforma en un [[Exploratory network analysis with Pajek#Cliques y sub redes completas|cliqué]] donde cada actor está conectado fuertemente con los demás, por tanto, las elecciones sociales de aprecio y desprecio se transmiten. Esta afirmación va en la línea del experimento de Solomon Asch. 
2) Si asumimos la teoría del balance cognitivo la relación $A-B$ es más probable cuando hablamos de lazos débiles por la necesaria menor inversión en tiempo. 
### El puente y la difusión

El mantenimiento en el tiempo de la estructura tríadica inestable  $A\gets C_2 \to B$  puede ser comprendida mediante el concepto de **puente**: línea en un sistema que proporciona el único camino entre dos puntos. Los puentes son importante en la **difusión** de información y en la **movilidad** asociada a esta. No obstante, en sistemas complejos es difícil encontrar dos sub grupos aislados solo conectados por una línea, es en este escenario donde la **eficiencia**, entendida como el camino de menor esfuerzo, se transforma en una variable importante para medir  puentes y puentes locales.

Sólo hablamos de puente cuando desde $A$ no existe otro camino de un paso para llegar a $B$ más que mediante $C_2$ . En este ejemplo la línea $C_2-B$ es un puente de $grado^\infty$ para $A$ dado que dicha línea es la única que hace posible la conexión con $B$ . Para cada actor $n_1$  una línea $L$ será del grado $g$ siendo $g$ el menor número de pasos de $n_1$ hasta $n_2$  sin cruzar el puente $L$. Por tanto, a mayor número absoluto de $g$ mayor será la importancia de $L$ para $\set{n_1,n_2}$.

#### interpretación de los puentes

Debido a las consecuencias metodológicas de extraer información en base a encuestas de elección social, los vínculos débiles son representados en los sociogramas "al margen" debido a la poca selección a los que estos actores eran sujetos. Para superar la asociación entre el margen y los vínculos débiles se propone, en cambio, la distinción $(puente/no\enspace puente)$ para diferenciar los lazos débiles de los fuertes, diferenciación que resulta más fructífera al diferenciar los lazos indirectos (*"los amigos de mis amigos"*) de los lazos positivos sin redundancia, es decir, con escasa referencia al grupo primario.

Paralelamente a esta distinción corre la distinción $(denso/no\enspace denso)$ dado que se espera que los *"sectores"* en la red sean más densos entre sí que entre ellos. Los actores viven la densidad bajo la codificación  del vínculo $(fuerte/débil)$ construidos bajo un esquema $(motivación/estructural)$ dado que es inevitable (estructural) la interacción con $n$ cantidad de personas pero solo pocas personas son seleccionadas para pasar tiempo juntos. 

Los puentes constituyen el punto de contacto o bisagra entre las dinámicas grupales de pequeña escala y los procesos de movilización inter grupalmente. Deben ser interpretados como los canales más eficientes de difusión en un sistema. Sus alcances serán analizados en el siguiente apartado

# Vínculos débiles en el éxito organizativo
este apartado se refiere a la última sección del artículo

Usualmente para explicar el éxito organizativo se aduce a factores culturales y de personalidad. Pero  el fenómeno sería más aprehensible si acudimos a las características estructurales de la red conformada por  todos los actores de la red. 

Debemos preguntarnos por las posibilidades de éxito que pudiesen estar en estrecha relación con la extensión de contactos de un nodo, asumiendo que una mayor extensión está determinada por la cantidad total de vínculos débiles. Estudios confirman que la **motivación a la acción** cuyo medio de información asociado son los mass media son más exitosos son asociados con **alguien con que se tiene algún vínculo personal**.  Esta capacidad de difusión exitosa también está relacionada con la generación de [[confianza]] que , desde el modo de tratamiento del artículo, se establece cuando **la conducta puede ser predicha e influenciada**. Nuevamente, tal capacidad se desprende de tener algún tipo de contacto directo o indirecto con el líder de la organización. 
### Etnografía 

Aunque los estudios donde es más factible extraer información sociométrica son las etnografías. Esta forma de abordar el problema impide ver redes interpersonales a gran escala y , por tanto, es imposible ver hasta donde llegan, es decir, cuando se fragmenta para dar paso a otro grupo fuertemente conectado entre si. Cuando hacemos etnografía nos enfocamos en una descripción densa focalizada en un **conjunto único** sin considerar sus fronteras más allá que con la marginalidad. La evidencia empírica apunta a considerar puentes a todos los vínculos con escasa relación con el conjunto único primario. Esta innovación teórico viene acompañada con una aparente contradicción resuelta por la distinción de escalas; en grupos pequeños los lazos fuertes aumentan la cohesiva y coordinación, pero las conexiones inter grupales que existen garantizan la cohesión y coordinación mediante lazos débiles: no es posible tener aprecio o conocer a cada uno de los habitantes de mi barrio, por tanto, **Una comunidad es más unitaria y coordinada en tanto más puentes locales por persona existan**  
### Aportación al DHL y conclusiones 

1) Desde un punto de vista empírico y teórico la movilidad fuera del conjunto único reproduce las condiciones de la movilidad.  
2) El principio de transitividad (se transmite la elección para generar un nuevo vínculo fuerte) es una función que depende de fuerza del vínculo

Estas conclusiones, aparentemente simples, son un sólido paso en la compresión del fenómeno social. No obstante el propio autor advierte su principal limitación: solo se trata de un fragmento de teoría que explaya sólo un aspecto muy estrecho de la realidad social. 

