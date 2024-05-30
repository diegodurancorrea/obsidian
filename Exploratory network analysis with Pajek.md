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

Una parte importante, aunque añadida, de las redes sociales, es su capacidad para combinar los datos relacionales con atributos no relacionales que mejorar las interpretaciones estructurales. Los atributos son las propiedades de los actores que no están basados en su posición estructural al interior de una red social
## Particiones
Estos atributos cuantitativos son llamados particiones por Pajek y se definen como la **clasificación que guarda las características discretas de los vértices**, consiste en un número defino de clases que pueden, a través de la extracción de sub redes, reducir su tamaño o complejidad. las particiones, a nivel de archivo, pueden describirse como una lista de números enteros asociados a una lista de vectores; es probable que el orden de estos enteros corresponde con el grado ordinal de la variable, esto depende del investigador. La integración de los atributos es relevante porque permite constatar se existe una correlación entre estos y las características estructurales. 

### sub redes

Las particiones dividen a la red social en un número de conjuntos excluyentes entre si. La primera posibilidad que permiten las particiones es la reducción de la red social en sub redes definida como la **selección de un sub conjunto de sus vértices y de todas las líneas que sólo inciden con los vértices seleccionados.** 

#### Extracciones

las extracciones pueden ser de tres tipos: 
+ vista local:  extraer solo una parte de la red 
+ vista global: agregar todos las partes en un sólo único vértice
+ vista contextual: se selecciona que vértices reducir en una sola agregación y cuales no redecir; funciona para enfocarse en una clase de vértices respecto a unos vínculos agregados

Un vértice agregado y reducido a un sólo vértice consiste **en remplazar un sub conjunto de vértices por un sólo vértice que incide para todas las líneas que lo conectan con vértices que originalmente no incidían dentro del subconjunto seleccionado**. el valor de las líneas que ahora lo conecta corresponde con la suma de todos los valores individuales dentro del sub conjunto.  Cuando agregamos de esta manera las relaciones dentro del propio sub conjunto se representa como un bucle del vértice resultante consigo mismo, el valor de la línea también resulta de la suma de todos las relaciones individuales.

La utilidad de la extracción consiste en proveernos de una vista parcial para comprender mejor estructuras de redes muy complicadas a primera vista. 
### Un asunto metodológico

Las particiones respetan la misma secuencia de los vértices ingresados en nuestra red social. Por lo que, necesariamente, el número de entradas en la partición debe ser el mismo número de vértices en la red, es decir, compatibilidad. 
## Vectores
Los vectores guardan propiedades continuas que pueden tomar cualquier valor en un rango definido. A nivel de archivo se describe como una lista de números reales; a diferencia de las particiones, los vectores no clasifican los vértices en clases. La función del vector es, entonces, asignar un valor numérico a cada vértice en una red social y pueden ser usado en cálculos. Los valores negativos pueden ser usados en cálculos pero no pueden ser representados en un visualización
### De vector a partición 

Además de los cálculos, podemos transformar nuestros vectores en particiones; existen múltiples opciones que nos ofrece Pajek:

+ Remover decimales: se eliminan los decimales de los números reales y los enteros iguales resultantes conformarán una nueva partición 
+ Particiones por intervalos:  agregamos el límite de una nueva partición y luego añadimos el incremento, el resultado es que cada partición tendría la misma diferencia de una a otra 
+ Particiones por selección: agregamos una lista de los límites superiores de cada clase, lo que permite tener un control sobre el tamaño y la diferencia entre cada clase
+ Sub vector de una partición
#### Estadística

La estadística ofrece técnicas para describir y comparar ==atributos== , de tal manera que si las relaciones estructurales pueden ser convertidas en atributos, estos, a su vez, pueden ser incluidos en análisis estadísticos. En esta línea, los vértices agregados mediante particiones permiten las aplicaciones de las tradicionales medidas estadísticas agregativas. Por tanto, las particiones y los vectores que guardan en si características estructurales de los vértices son el puente entre los análisis de redes sociales y la estadística. 






