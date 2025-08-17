---
"Fecha_creacion:": 2024-10-09
"Ultima_modificacion:": 2024-10-09
"Nombre_documento:": What are embeddings
"Tipo_documento:": Artículo
"tipo:": Reseña larga
"autor:": Vicki Boykis
"Link:": 
---
Este es un artículo extenso pero introductorio que sigue una linea explicativa simple: vamos a aplicar la tecnología de inteligencia artificial para producir *web services*.  Mi acercamiento a este extenso artículo se debió por mi interés en aprender las bases conceptuales de la inteligencia artificial y los embedding para la ponencia del *primer simposio de ciencias sociales computacionales de Iberoamérica*. No seguiré la linea argumentativa del artículo sino, de una forma muy laxa, apuntaré a mi manera los conceptos que aprendí y su relación casual. Este será un resumen de naturaleza distinta a las demás. 

Podemos comenzar con el concepto de **machine learning**  como el proceso fundamental a tratar, este proceso le indica a una máquina de cómputo una serie de algoritmos que debe usar para ser capaz de aprender por si mismo una tarea en particular, tales tareas van desde la *recomendación*, la *predicción* hasta la *clusterización*.  Para llegar a resolver adecuadamente cada una de las tareas asignadas debemos llevar a cabo cuatro pasos: **1)** tener un conjunto de datos que servirán de entrada o entrenamiento, **2)** escoger cuales de las características de los datos nos resulta relevante, 3) Construir un modelo con los datos seleccionados y 4) integrarlo con la API de nuestra página web. 

Para efectos prácticos nos enfocaremos en la construcción del modelo y , eventualmente, en el tratamiento de los datos para ingresarlos al modelo. Los modelos de machine learning puede dividirse en tres grandes categorías: *aprendizaje supervisado*, *aprendizaje no supervisado* y *aprendizaje por reforzamiento*. Cuando generamos un modelo lo que intentamos es que la máquina aprenda , por si misma, un **conjunto de instrucciones para generar una salida a partir de una entrada concreta**, es , en otras palabras, tomar unos datos de entrada cómo entrada para producir reglas acerca de cómo deberíamos clasificar algo  , o producir una específica salida. 

Centrémonos en el aprendizaje supervisado , este tipo de machine learning necesita de una comprobación con datos reales, por lo tanto es necesario subdividir los datos de entrada en: **1)** set de entrenamiento, **2)** set de testeo y **3)** set de validación. El modelo es , por tanto, entrenado con sólo los datos de entrenamiento; aquí debemos apuntar dos cosas: **1)** los datos que pueden ser procesados por un sistema de cómputo son números y **2)** el modelo trabaja en base a un algoritmo que tiene la capacidad de predecir una salida a partir de una entrada, no obstante, existen diferentes algoritmos que pueden ajustarse más adecuadamente a explicar un fenómeno que otro. Dentro de los algoritmos más utilizados se encuentran la regresión linear simple y múltiple, la regresión linear logística , las redes neuronales, entre otros.   

Debido a que para procesar lenguaje natural no podemos simplemente ingresarlo al modelo algorítmico, debemos transformarlo mediante un proceso de **encoding**. Estas técnicas de transformación pueden ser las siguientes: *codificación ordinal*, *codificación indicativa*, *codificación one-hot*. El proceso de encoding transforma las palabras vectores, es decir, como una lista de números cuyo tamaño x refiere a las dimensiones n.  Sobre esta base se han desarrollado las técnicas de **procesamiento de lenguaje natural**, el resultado de la codificación en su conjunto es un embedding o espacio embebido, es decir, **es información multimodal que ha sido transformada en matrices de n dimensiones compuesto ya sea por vectores , tensores o grafos**. 

Sobre la base de los alcances técnicos anteriores se han desarrollado dos clases de métodos: **1)** métodos en base al conteo y **2)** métodos en base a la predicción. Esta primer clase de métodos se sustentan en un acercamiento estadístico descriptivo. Sobre esta familia de métodos se encuentran: TF IDF , LDA , LSA, entre otros; es importante señalar aquí que estos métodos nos pueden dar una indicación sobre la relación entre dos o más palabras, pero no nos dice nada acerca de la similaridad semántica entre un conjunto de palabras. 

Los métodos en base a predicción emergieron con fuerza con la arquitectura **word2Vec** desarrollada por Google en base al uso de redes neurales multicapa que permitieron desarrollar, como un sub campo del machine learning, lo que se conoce como **deep learning**. En esta arquitectura se estableció como estándar: la tokenización , la segmentación por palabra y la remoción de ruido. Los diferentes algoritmos de redes neuronales pueden dividirse en: feed forward, convolutional neural network y recurrent neural network. Cada una de estas variaciones son el fundamento técnico de una arquitectura novedosa publicada en recientemente llamada **Transformers**, allí se implementa una arquitectura novedosa y dos métodos innovadores: 1) una arquitectura (encoder/decoder) y 2) un mecanismo de atención. Esta arquitectura ha permitido el desarrollo de diferentes modelos como el de GPT, BERT , en otros que hoy hacen posible desarrollar inteligencia artificial generativa.  






 

