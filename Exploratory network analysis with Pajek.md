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

# Part 2 : atributtes and relations





