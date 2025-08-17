---
"Fecha_creacion:": 2025-08-14
"Ultima_modificacion:": 2025-08-14
"Nombre_documento:": A commentary of laws of form from Spencer Brown
"Tipo_documento:": Conferencia
"tipo:": Reseña corta
"autor:": 
"Link:": http://www.tydecks.info/online/themen_e_spencer_brown_logik.html
---
Este es un artículo que encontré en un blog mientras buscaba información que me facilitara una comprensión más profunda sobre las leyes de la forma de George Spencer Brown. La necesidad emerge de una aplicación que haré del cálculo de distinciones en mi trabajo de grado, y necesitaba poder explicar el significado filosófico de la noción de distinción. Por tanto el contenido de esta reseña estará concentrado en hacerme más inteligible los conceptos centrales del pensamiento de Spencer Brown. 

*No puede haber una distinción sin motivo*, esta es una frase de Spencer Brown, también aplica para las leyes de la forma. El motivo se encuentra en un problema lógico del campo matemático: las **autorreferencias negativas** son paradojas que deben evitarse; se evitan con axiomas restrictivos como los propuestos por el Whitehead y Russel. En aritmética el problema puede ser planteado cuando una expresión se contiene a si misma en los dos lados de la igualdad de la siguiente forma $\huge{x = \frac{-1}{x}}$

La solución sólo es posible añadiendo un nuevo eje numérico imaginario, la solución es simultáneamente $-i$  o  $i$ 

${-1 = \frac{-1}{-1} = 1}$

${1 = \frac{-1}{1} = -1}$

Es curioso que este tipo de problemas no suponen un problema real en programación, las expresiones habituales de los contadores se manejan en bucles, por ejemplo: 
```python
while True:
	i = i - 1
```

El problema desaparece cuando el mismo literal de la variable señala la ubicación de almacenamiento en memoria , tanto como el valor almacenado en ella. Esta misma dualidad de estados puede describir una primera noción de **autorreferencia**, un momento donde implícitamente se toma al tiempo en cuenta en la lógica sobre un proceso que es, a su vez, el resultado del proceso. La diferencia entre proceso y resultado resulta confusa y sólo depende del punto de vista del observador. 

Spencer quiere formalizar una lógica que describa el funcionamiento real de la programación, y para eso describe a la lógica: 1) como demasiado simple, casi infantil, y 2) como demasiado compleja. El punto está en que sus abstracciones acontecen sobre formas algebraicas transparentes, por lo que la veracidad de una afirmación es siempre un problema de forma, un problema de signos que se relacionan entre si a través de otros signos que son operadores. Brown se enfoca en desarrollar una lógica que formalice las formas en que las distinciones son posibles ya que considera que esta primera operación está en la base de la contabilidad de los elementos sortales[^1]. 

Una idea que debe poner en entredicho es la clásica diferencia entre el signo y su medio, sólo para decir que ningún signo da cuenta enteramente de sus medios; tal y como acontece en el álgebra en relación con la aritmética, las cualidades numéricas no pueden ser totalmente descritas algebraicamente. Es sobre esta noción de signos que se distinguen sobre medios que no pueden representar totalmente que Brown marca el punto de partida **en la distinción e indicación**

Si queremos empezar por una distinción elemental debemos empezar por un signo que preceda a la diferencia entre operandos y operadores, que pueda ser ambos, este símbolo es la *cruz* 
```lof
()
```

la *cruz* indica un lado , no importa cual sea, al mismo tiempo los hace distinguibles. podemos colocar una *cruz* al lado de otra, y en términos lógicos, tendremos que el *el valor de la llamada repetida es, nuevamente, el valor de la llamada*, esta es la ley de la llamada. 
```lof
()()::=:: ()
```
Por otra parte, *el valor del cruce hecho de nuevo no es el valor del cruce*, esta es la ley del cruce. la primera diferencia es espacial, la segunda es temporal; volver a cruzar la misma distinción es volver al pasado y deshacer lo hecho, el único valor visible es la memoria de la operación. Es semejante a cruzar una frontera dos veces, el estado inicial es restablecido, es marcar la distinción y movilizarse al interior de esta, y cuando se está allí de nuevo, marcar de nuevo la misma distinción y movilizarse al interior de esta, el resultado es que te movilizaste de un lado a otro, y si el conteo es par, terminas en el lugar donde empezaste.  
```lof
(())::=::  .
```

**La distinción es la continencia perfecta** , así Brown advierte que en la distinción se obtiene la unidad entre el signo y su medio, todo queda contenido en su interior. Una propiedad de la distinción es que a partir de las reglas lógica que escuetamente presentamos arriba, se puede ejecutar cálculos, que son transformaciones o conversiones de una cierta modularidad en otro; *la forma de cualquier número cardinal finito de cruces puede tomarse como la forma de una expresión*, de esta forma complejas construcciones lógicas de entradas y salidas puede transformarse en uno de los dos valores, en *cruz* o en *oak* que podrán ser interpretados de múltiples formas.

Como componente final de estos comentarios abordaremos la noción de *re entry*. Brown la introduce para indicar procesos infinitos, con resultados infinitos; es una figura que se repite infinitamente de manera uniforme, así: 
```lof
f::=::((((.. a)b)a)b)
::=::((f < a >)b)
(([0])$0)

```

A través de esta función podemos construir ondas que van alternando estados con cada iteración, este tipo de oscilaciones indican simplemente cambios, y la superposición de ondas iterativas pueden producir pequeños pulsos cortos en la extensión de un gran pulso dominante, en las interferencias, en los cruces del límite, encontramos una primera aparición del tiempo como cualidad implícita en la lógica de la auto referencialidad[^2], los demás operadores y operandos lógicos se construyen a partir de la relación lógica entre estas distinciones.  
# Footnotes

[^1]: aquellos elementos que perceptivamente pueden ser contados, acumulados , etc. 
[^2]: Algunas cualidades de las que carece la distinción como objeto lógico son el ordinario sucesor, no existe un distinción que pueda seguir la fórmula $n_i = n+1$, si queremos construir una secuencia sólo podremos añadir nuevas cruces u ordenarlas diferencialmente. Tampoco es posible inducir otras propiedades de la distinción, desde una perspectiva filosófica la emergencia de estas cualidades surge de un modo diferencial de observar las relaciones lógicas, proponiendo axiomas novedosos y poderosos pero indemostrables.  