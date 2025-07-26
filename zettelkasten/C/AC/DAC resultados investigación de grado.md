---
Fecha_creacion:: 2025-07-11
Ultima_modificacion:: 2025-07-11
Nombre_documento: DAC resultados investigación de grado
tipo:: Anotación
---

# Redes de aprecio


# Centralidad y grupos cohesionados de la red social de X

encontrar interpretativamente la mejor medida para extraer las sub redes para iniciar la búsqueda temática en X, 
la cohesión como la interacción más frecuente, común actitud o identidad , principio de homofilia,
componentes(partes conectadas, entonces los componentes débiles y fuertes develan aquellas ramas hacia afuera que surgen del grueso de nodos de la red al indicar caminos sin línea de retorno, por lo tanto esta no es una buena red para analizar las posibles diferencias temáticas al interior grueso de la red) (pero debemos usar los resultados de las particiones para constatar nuestro argumentación de asunto inapropiado, quizá debamos acompañar este con alguna gráfica que ejemplifique nuestro punto)
Core (ese será nuestro mecanismo para romper la red hasta encontrar componentes aislados)(nos permite conocer los grupos que están más interrelacionados entre si, y separados con los demás) (podemos visualizar si los roles políticos difieren en estos sub grupos, incluso si están en ellos, podemos hacer esto extrayendo una partición de otra partición) (son grupos que reciben de si mismo elecciones de seguidor y es mutuamente compartido)
(mejorar la redacción de la definición)
(Se aplican medidas de centralidad, es decir, medidas del grado de un nodo, lo que nos interesa conocer es quien es quien dentro del grupo que recibe elecciones como del grupo que da esas elecciones) (evidentemente debemos tener estos supuestos explicitados)
# Topic Modeling
debemos indicar el porcentaje temático que dio cada proyecto de acuerdo (80% tema 1 , 15% tema 4, etc.) 
## resultados del pivot


# Escrito

### Red Social 

Luego de ejecutado el scrapeo con los perfiles iniciales, y repetir este proceso tres veces, construimos una red de 222032 perfiles, con 340686 líneas en total, compuesto enteramente por líneas direccionadas, es decir, líneas que hacen distinguible la diferencia entre seguir y ser seguido por un perfil. La red cuenta con una densidad de 0.00000691%, y presenta un grado promedio de 3,06

[Gráfica de la red. Completado]

Gracias a la existencia de las líneas direccionadas podemos preguntarnos acerca de qué perfiles reciben para sí la mayor atención, es decir, quienes concentran más elecciones de ‘seguir’. La centralidad de los perfiles garantiza que la información que puedan comunicar sea alcanzada por una mayoría de los nodos, y aumenta la posibilidad en que tal información pueda orientar la propia opinión sobre un acontecimiento.  

[gráfico con los perfiles de mayor centralidad]

Un dato muy importante se deriva de preguntarnos acerca de la propia centralidad del concejo de Medellín en la comunicación política al interior de la red social, por lo que podemos enfocarnos en conocer cuantos de los perfiles de los concejales hacen parte de los nodos con mayor centralidad, y cuál es su relación respecto de ellos.  

[podemos visualizarlos con .vec y clu. en un gráfico, y una estadística de excel] 

Aunque las medidas de centralidad son útiles para descubrir los perfiles con mayor alcance en una red social, no es suficiente para observar las posibles grupos cohesionados que existen al interior de una red social. Las medidas de cohesión están basadas en el principio de homofilia, lo que significa que las categorías sociales agregativas tales como identidad, comunidad o grupo se explican a través de una interacción constante entre un conjunto de actores sociales representados por nodos. En los términos conceptuales del ARS se les llama *componentes* a las partes conectadas de una red, y podemos extraer los componentes de una red a través de diversos algoritmos de cohesión.  En nuestro caso empleamos el algoritmo K core cuya aplicación calcula *la máxima sub red en la cual cada vértice tiene , por lo menos, un grado de k (la k representa el grado de un nodo) dentro de la sub red*, esto significa que cada nodo pertenecerá a un clúster si comparte con sus nodos adyacentes, a su vez, la misma cantidad de relaciones; en nuestra red social significa que cada perfil pertenecerá a una sub red  si comparte con los otros perfiles adyacentes la mutua elección de ser *followers* del otro, si varios perfiles comparten entre sí la decisión de seguirse mutuamente podemos hablar de un grupo que está fuertemente interrelacionado entre si, ubicarlos al interior de la red social y observar cómo se diferencian estructural y temáticamente con otros grupos.      

[gráfico con la partición de k core,  averiguar si los concejales pertenecen a grupos k core diferentes, asociar cada grupo con su topic modelling]



