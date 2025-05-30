---
"Fecha_creacion:": 2025-02-23
"Ultima_modificacion:": 2025-02-23
"Nombre_documento:": Teorías sistémicas de la comunicación
"Tipo_documento:": Artículo
"tipo:": Reseña larga
"autor:": Dirk Baeker
"Link:": https://revistamad.uchile.cl/index.php/RMAD/article/view/47267/49290
---
# Desarrollo

En este artículo exploraremos a profundidad la siguiente tesis que presumiblemente tomamos como verdadera: *el conjunto de posibles mensajes, así como el mensaje que será seleccionado de ese conjunto (contexto), debe ser construido por los participantes de la comunicación*. 

Las teorías sistémicas de la comunicación se derivan de una *deconstrucción* del modelo de ==transmisión== de Claude Shannon. Debemos tener en mente un escenario como el siguiente $\Box a  \rightarrow \Box b$ ; a Shannon nunca le interesó el aspecto semántico de la comunicación, su enfoque *ingenieril* estuvo en comprender adecuadamente la transmisión entre dos máquinas: *que la señal transmitida pueda ser recibida como la misma señal por un receptor (a pesar del ruido)*. La innovación del modelo de Shannon fue proponer que **la parte que lidia con el ruido es la misma que recibe la señal**, Shannon usó la *mecánica estadística* para "corregir" el ruido de las diferentes señales, lo que quiere decir que el receptor, en el momento de percibir la señal supone, razonablemente, que dicha señal haya sido distorsionada ( la más de las veces inintencionalmente). Podemos representar lo anterior así $\Box a  \rightarrow \Box b(a_1,a_2,a_3,...)$ , en efecto, cada receptor genera estadísticamente un conjunto de *posibles mensajes (señales)* , de los que seleccionamos el más probablemente correcto en contraposición con el probablemente distorsionado, esto significa, en una necesaria abstracción, que **el control de la transmisión en la comunicación se basa sobre el cálculo y manejo de la contingencia**.

El observador, como un agente por completo ajeno, lidia con el ruido y reproduce fielmente lo que se quiso transmitir debido a la *inverificabilidad* de la identidad del mensaje por parte de los interlocutores, esta es precisamente la razón de la introducción del observador a los modelos comunicacionales de la criptografía, asegurarse de la existencia de un canal limpio que facilita la comunicación, a su vez que asegura la "buena" intención de los esfuerzos comunicativos (sin distorsión, sin portada y sin dobles sentidos ). 

Ahora enfoquemos el concepto de **selección** con el modo de observación de las teorías cibernéticas, de lo que se tratará es de re interpretar la forma en cómo un sistema lidia con el *control de la información*. Los problema ingenieriles de la transmisión y la identidad del mensaje se 'cambian' por la *selección* y la *recursividad* respectivamente, el cambio no es arbitrario, corresponde a observar la *selección* al interior de un sistema que *se conecta recursivamente*, los participantes del sistema están *acoplados estructuralmente*, tanto el receptor como el emisor (cuya ontología depende del punto de vista) son unidades complejas que se relacionan para lidiar mutuamente con su propia complejidad. En este contexto debemos introducir el concepto de **información**, la información (una de las partes constitutivas de la unidad comunicativa) es *la relación de un mensaje con un set de otros posibles mensajes*. Tanto la selección como la información son *decisiones* que se toman en un sistema que se "sostiene" gracias a las operaciones de la comunicación. 

Sin entrar en minucia sobre lo que se entiende un sistema de comunicación, apuntamos que en éste, en cada *selección informativa* existe una relación, antes modelada con los términos de señal y ruido, ahora como de **redundancia y variedad**, aunque no se estipula un balance específico entre estas variables , guían, en su conjunto, las operaciones de los sistemas de comunicación. 

Los sistemas de comunicación, en definitiva:

 1. Son sistemas donde sus unidades seleccionan mensajes de un conjunto de posibles mensajes
 2. Son sistemas donde cualquier unidad acoplada al sistema es un observador que produce sus propias distinciones para identificar mensajes
 3. Son sistemas que son producidos por un mensaje identificado por una unidad participante en un sistema , y , selectiva y recurrentemente es atribuida a otra (unidad, a un conjunto de mensajes y una fuente de ruido posible)

Así como en el modelo ingenieril el problema de la identidad (y de la comunicación en general) consiste en lidiar con el ruido, el sistema de comunicación, para alcanzar una exitosa reproducción, debe lidiar con la variedad de tal forma que sea posible la emergencia de la redundancia. Podemos representar esta diferencia a continuación: 

$\text{Modelo de Shannon = }\Box a \xrightarrow[a]{transmite} \Box b (a_1,a_2,a_3)^{ruido}\xrightarrow[probabilidad]{identidad} \Box b(a_1)$

$\text{Sistema de comunicación = }\Box a \xleftarrow[a_1]{obsevación} \Box b (a_1,a_2,a_3)^{variedad}\xrightarrow[redundancia]{selección} \Box b(a_1)$

Es evidente que al observar las relaciones entre $\Box a$ y $\Box b$ pensemos que la comunicación se trata de un asunto relacional, y en efecto lo es, en ambas llegamos a la conclusión de que para la producción y reproducción de *mensajes* es imprescindible los dos lados del modelo. En la distinción cualitativa que marca el modelo sistémico de comunicación se produce un re enfoque en una *identidad* que se vuelve recursiva, es decir, la identidad se genera cuando *el mensaje va de un lado a otro de las unidades comunicativas y es seleccionado positivamente cada vez que se vuelve sobre él*, en otras palabras el *mensaje* es , en efecto, *redundante* en tanto se encuentra simultáneamente en "diferentes lugares" , la *identidad* del mensaje se construye de esta forma; pero esto supone que las unidades comunicativas aceptan el mensaje y, más complicado aún, que éstas quieren participar en el sistema de comunicación. Toda interacción es un sistema constituido de sus unidades participantes, por lo que garantizar dicha participación es un riesgo que la comunicación debe superara acudiendo, en una forma muy general, a una estructura y cultura que haga atractiva la participación; aunque este no es un artículo en específico sobre este tema, es importante señalar las complejidades de trabajar con sistemas de comunicación, complejidades que derivan del hecho , muchas veces encubierto, de que toda participación, es siempre auto motivacional (auto socialización)[^5]. 

Ahora enfrentemos más incisivamente el asunto del *manejo de error* en los modelos de comunicación. Shannon era consciente que su propuesta probabilística traía un incómodo supuesto: la identidad del mensaje es inverificable salvo añadamos otro observador que simultáneamente monitoree los dos lados en el momento de la transmisión, así lo dejó por escrito en sus trabajos sobre criptografía. En ese modelo es posible verificar la identidad , pero en el salto a lo sistemas de comunicación el asunto se complejiza aún más. La investigación científica (empírica) se enfrenta con dificultades con la noción de comunicación, no es posible saber si una comunicación efectivamente está ocurriendo dado que la distinción (información, acto de comunicar) no cuenta con un mecanismo biológico determinísticamente causal que podamos usar como un indicador infalible.  El concepto de comunicación no es un objeto que se pueda mostrar y medir, es, en cambio, un principio explicativo que ayuda a ordenar la observación y generar marcos para realizar descripciones más ambiciosas y sofisticadas que indican la perspectiva de un observador respecto de una realidad compleja.[^1] Esto no quiere decir que la comunicación no deje rastro o evidencia alguna, las propias descripciones organizadas de la historia social son muestra de que la comunicación en parte queda en parte impresa en "el mundo sensible". Retomando la *corrección del error* en el modelo del sistema de comunicación, lo que vería un observador "externo", si es que lo hay, sería que sobre *las descripciones que se expresan sobre el mundo* las dos unidades primarias se 'corrigen'  mutuamente sus 'errores' de observación[^2], es una corrección del error *recursivamente organizada*. 
## Impactos

En una forma muy general, aunque no menos cierta, todas las derivaciones de el modelo de comunicación propuesto y presentado por Shannon, son el primer paso constitutivo de su propia teoría, así cada teoría posterior es, en realidad, una *teoría de la comunicación* inspirada en Shannon. Baeker señala tres teorías posteriores que se desarrollaron apoyándose en Shannon: 

### Cibernética
Desarrollando la noción de sistema como *unidad de la diferencia*, Wiener apunta que un sistema refiere a muchas contingencias para enfrentarse al mundo. En su modelo se combina la *operación de un mensaje que cambia el estado del mundo* (y del propio sistema) con la *distribución de elementos (organización) que son, al mismo tiempo, producidas por dicha operación*. Más adelante, con posteriores desarrollos, se amplia la autonomía sistémica con *la doble clausura operativa* para explicar la emergencia de los sistemas complejos: la primera versa sobre una recursividad operacional , sobre una restricción fronteriza sobre los elementos que están al interior del sistema; y la segunda, que es una selección sobre las estructuras y culturas, un cierre auto descriptivo que funciona gracias a la libertad que tiene de manejar la contingencia. 

Esta misma distinción de la doble clausura (y la naturaleza de sus diferentes cierres) genera una distinción autopoiética entre: 1) los elementos que producen la red de elementos, como la 'invisible' comunicación  auto referente cuya forma de vinculación se mantiene inaccesible para un observador y , 2) la red de elementos o la estructura que contribuye a la reproducción y que, como las personas y las jerarquías, puede observarse experimentalmente. 
### Teoría de los sistemas sociales 
El sistema social *es la versión luhmanniana de una teoría de la comunicación*, en este modelo la *comunicación* como operación, es el ultra elemento del sistema social, del que se componen todos los demás. Una vez iniciado el sistema social , de su recursividad se infieren las culturas como las estructuras del sistema mismo, son aquellos elementos que una y otra vez se reproducen. Para este modelo, lo que se llama **sentido** no es otra cosa que, lo que en el modelo de Shannon se apuntaló como la agregación entre el **mensaje, el conjunto de posibles mensajes, y la selección de este conjunto de posibles mensajes**[^3]. 

El sistema social, una vez iniciado, puede irritarse a sí mismo, esto es posible gracias a su múltiple composición, a la auto referencia de sus comunicaciones, a las temporalización de sus mismas operaciones y al tener como entorno a la sociedad donde las perturbaciones son esperadas, captadas en el 'aire' e incorporadas[^4]. Sobre la base de esta irritación / auto irritación los sistemas sociales, en concordancia con la segunda clausura, se seleccionan estructuras y culturas que , en términos teóricos, no son sino la indicación del grado de agencia de los sistemas sociales para auto describirse. 
### Las leyes de la forma

Aunque George Spencer Brown no pretendió desarrollar ninguna teoría de la comunicación, su modelo  lógico puede ser (y lo es por Baeker) interpretado bajo una teoría de la comunicación. 
```lof
elemento comunicativo auto constituido:: = :: (M[1]) N$1

```
La $M$ representa la selección de la distinción, las dos líneas a la derecha más próxima a ella representan la distinción que nos habla de un observador marcándola, de la indicación que viene con esta (de un lado y del otro), y un virtual lado no marcado que necesariamente la acompaña. La $N$ representa el conjunto de posibles mensajes ya determinados o dejados sin marcar. La línea inferior representa que estamos ante una comunicación auto contenida.   





 
# Footnotes

[^1]: Por tanto no remite a una realidad sustancial primigenia
[^2]: Mismo problema planteado en [[El Giro de Lenin o el Factor-R de la Comunicación|la objeción de contingencia]]
[^3]: Es un buen complemente, quizá más claro, a [[Sistemas sociales; lineamientos para una teoría general#Capítulo 2 (El sentido)|el sentido en la teoría ]]
[^4]: Que el entorno de los sistemas sociales sea la sociedad apuntala que nos encontramos ante una teoría que lidia con la propia reflexividad de la teoría
[^5]: esta reflexión sobre la motivación en muy importante si queremos ahondar más en los sistemas sociales