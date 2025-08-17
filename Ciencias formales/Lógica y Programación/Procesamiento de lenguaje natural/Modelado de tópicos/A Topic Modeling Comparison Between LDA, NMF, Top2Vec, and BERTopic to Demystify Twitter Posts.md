---
Fecha_creacion:: 2024-03-17
Ultima_modificacion:: NaN
Nombre_documento: A Topic Modeling Comparison Between LDA, NMF, Top2Vec, and BERTopic to Demystify Twitter Posts
tipo:: Reseña corta
autor:: Roman Egger  and Joanne Yu
---

# 1.1 Objetivo
A partir de una base de datos creada a partir de *Twittees*  en referencia a tópicos relacionados con COVID-19; este artículo se propone una amplia comparación entre cuatro de las más usados algoritmos de agrupación *topic modeling* disponibles en el estado del arte. Su resultado será cual modelo ayuda mejor a informarnos más significativamente sobre lo que se está diciendo en un corpus.
# 2.1 Desarrollo

## 2.2 Ampliación del fenómeno social
La sociedad moderna ha desarrollado formas en la que la interacción pueda presentarse sin la necesidad de compartir un mismo espacio físico mientras haya acceso a una adecuada tecnología de telecomunicaciones. Las posibilidades ya han sido explotadas por la internet; por lo tanto, su conocido éxito implica un cambio significativo en la conducta humana respecto a la internet, a partir de allí, las conductas son tan variables como sean posibles, esto deriva en que las redes comunicativas digitales son un fenómeno social que ya emergió y merece ser estudiado como nuevo campo de la investigación social, que, en todo caso, se sustenta sobre una especial forma de [[Comunicación artificial]] 
## 2.3 Aplicación y resultados 

Existen dos maneras diferenciadas en la que son construidos un algoritmo de  *topic modeling*: 1) a través de  técnicas de modelos de embeddings  2) y a través de algoritmos de ponderación (estadística o matricial):
+ Para los primeros todos los documentos que conforman el corpus son tratados como un sólo documento, es decir, el proceso de construcción del espacio vectorial es continuo. Según el documento para este proceso no es necesario ningún pre procesamiento del corpus salvo la selección de este.
+ Para los segundos es requerido tomar decisiones sobre *hiper parámetros*, es decir, requieren de un necesario proceso de pre procesamiento del corpus a través de técnicas en NLP (stop words, tokenization, lematizacition, etc)  

El paso del preprocesamiento es crucial para tener en cuenta, en especial, cuando se trata de base de datos no estructuradas.  Aunque el objetivo de los algoritmos es producir un sentido sobre un corpus de información, la evaluación de ese *sentido* depende de una evaluación humana.

Durante todo el documento se comentó sobre el funcionamiento interno de los algoritmos. La explicación técnica estará en diferentes apartados como [[BERTopic]] para su continua agregación. Por tanto, la explicación técnica es obviada en esta reseña.  Los resultados de los cuatro modelos se compararon según la técnica generativa del algoritmo:

1) NMF genera mejor rendimiento que LDA, los tópicos arrojados por ambos modelos aún se encuentran en un nivel 'estándar' de la información que puede proporcionar, los tópicos alcanzadas no suelen ser informativamente significativos. Sus características son limitadas en un post procesamiento
2) BERTopic genera mayores rendimientos que Top2Vec  gracias a su modelo de representación. Los resultados arrojan mayor especificidad en BERTopic. Los resultados finales sugieren que el modelo de BERTopic es superior a los demás para tratar con bases de datos escuetas y no estructuradas. 

Para una mejor visualización de los resultados remitirse directamente al documento en el último apartado donde se exponen las ventajas y debilidades de cada algoritmo de topic modeling 


