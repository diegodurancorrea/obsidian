---
Fecha_creacion:: 2024-02-04
Ultima_modificacion:: NaN
Nombre_documento: REGEX
tipo:: Componente del lenguaje
autor:: Regex
---

## 1.1 ¿Qué significa 'expresión regular'?

>*Las expresiones regulares expresan un lenguaje definido por una gramática regular que se puede resolver con un [[autómata finito no determinista (NFA)]], donde la coincidencia está representada por los estados.* 

###### Ejemplo:

```copy
 ^[01]*1$
```

![[Pasted image 20240204004057.png]]
Los autómatas pueden variar los motores de expresiones regulares. El nivel al que pueden aspirar es hacia  patrones escalones más arriba en el modelo lingüístico de Noam Chomsky.  El motor <code>re</code> de Python sólo soporta el nivel *regular*. 

## 2.1 Agrupación regular y atómica 

#### 2.2 regular 

> *Los grupos regulares que no capturan permiten que el motor vuelva a ingresar al grupo e intente hacer coincidir algo diferente (como una alternancia diferente, o hacer coincidir menos caracteres cuando se usa un cuantificador)*

Los grupos regulares que no capturan tienen el formato ``(?:...)`` con un ``?:``

Es decir, en la agrupación regular el motor de búsqueda tiene en cuenta los estados anteriores de coincidencia y puede recordarlos para hacer coincidir con la consulta. En el artículo *[[attencion is all you need]]* se destaca la importancia de revisar los estados anteriores. 
#### 2.3 Atómica

> *Los grupos atómicos difieren de los grupos regulares que no capturan, ya que está prohibido el retroceso. Una vez que el grupo sale, toda la información de seguimiento se descarta, por lo que no se pueden intentar coincidencias alternativas*

Los grupos atómicos tienen el formato  ``(?>...)``  con un ``?>``

## 3.1 Caracteres de ancla

> *Una gran cantidad de motores de expresiones regulares utilizan un modo "multilínea" para buscar varias líneas en un archivo de forma independiente. Por lo tanto, al usar $ , estos motores coincidirán con los finales de todas las líneas. Sin embargo, los motores que no utilizan este tipo de modo multilínea solo coincidirán con la última posición de la cadena proporcionada para la búsqueda.*

``g$`` 

## 4.1 Clases y negación 

> *La clase de personaje se denota por <code>[]</code> . El contenido dentro de una clase de caracteres se trata como un <code>single character separately</code>*. 

+ ``[12345]`` coincide con solo uno de los elementos. coincide una singularidad *one code,* no la cadena
+ El rango en la clase de caracteres se denota usando <code>-</code>  ej. : <code>[A-Z]</code> .  los rangos más utilizados son: <code>[AZ] , [az] o [0-9]</code> y combinados son <code>[A-Za-z0-9]</code>
+ para hacer coincidir el ``-`` debemos escaparlo: ``[AZ\-az] `` así. 
+ La clase de caracteres negados se denota por ``[^..]`` .El signo de careta ``^`` denota coincidir con cualquier carácter excepto el presente en la clase de carácter. eje    ``[^cat]`` coincide con cualquier carácter excepto ``c a o`` . 
	+ solo funciona al inicio de la clase de carácter
	+ la expresión ``[^]`` sólo funciona en JavaScript
+ Las clases de caracteres *POSIX* son secuencias predefinidas para un determinado conjunto de caracteres. Para utilizar el interior de una secuencia de corchetes (también conocida como clase de caracteres), también debe incluir los corchetes.
	+  ``[[:digit:]-]{2}`` coincide con:
		• --
		• 11
		• -2
		• 3-

## 5.1 Cuantificadores posesivos

| cuantificador |                                                                                                                                              codicioso                                                                                                                                               |                                                                                                 perezoso                                                                                                  |                                                                                                                                                           posesivo                                                                                                                                                           |
| ------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| cero o mas    |                                                                                                                                                  *                                                                                                                                                   |                                                                                                    *?                                                                                                     |                                                                                                                                                              *+                                                                                                                                                              |
| uno o mas     |                                                                                                                                                  +                                                                                                                                                   |                                                                                                    +?                                                                                                     |                                                                                                                                                              ++                                                                                                                                                              |
| cero o uno    |                                                                                                                                                  ?                                                                                                                                                   |                                                                                                    ??                                                                                                     |                                                                                                                                                              ?+                                                                                                                                                              |
|               | Un cuantificador codicioso siempre intenta repetir el sub-patrón tantas veces como sea posible<br>antes de explorar coincidencias más cortas por retroceso.<br>En general, un patrón codicioso coincidirá con la cadena más larga posible.<br>Por defecto, todos los cuantificadores son codiciosos. | Un cuantificador perezoso (también llamado no codicioso o reacio ) siempre intenta repetir el subpatrón<br>tan pocas veces como sea posible, antes de explorar coincidencias más largas por<br>expansión. | La noción de cuantificador codicioso / perezoso solo existe en los motores de regex de retroceso.<br>En los motores de expresiones regulares sin retroceso o los motores de expresiones regulares<br>que cumplen con POSIX, los cuantificadores solo especifican el límite superior y el límite inferior<br>de la repetición |



>*Debido a que los cuantificadores posesivos no hacen retroceso, pueden resultar en un aumento significativo del rendimiento en patrones largos o complejos. Sin embargo, pueden ser peligrosos (como se ilustra arriba) si uno no es consciente de cómo, precisamente, los cuantificadores funcionan internamente.* 


El estándar POSIX no incluye el ``?`` Operador, muchos motores de expresiones regulares POSIX no tienen una comparación perezosa. Mientras que la refactorización, especialmente con el "mejor truco" , puede ayudar a emparejar, en algunos casos, la única manera de tener un verdadero juego perezoso es usar un motor que lo soporte.

El uso de la clase de caracteres negados reduce el problema del seguimiento y puede ahorrarle mucho tiempo a la CPU cuando se trata de entradas grandes.



## 6.1 Escapando

En Python:  `` pattern = r'regex' `` o  `` pattern = r"regex" ``
###### ¿Qué es el escape?

> *El escape de caracteres es lo que permite buscar y encontrar literalmente ciertos caracteres (reservados por el motor de expresiones regulares para manipular búsquedas) en la cadena de entrada. El escape depende del contexto*

Barras invertidas: 

Decir que la barra invertida es el carácter de "escape" es un poco confuso. La barra invertida se escapa y la barra invertida trae; en realidad, **activa o desactiva el Meta carácter frente al estado literal del personaje que se encuentra frente a él**. Para utilizar una barra invertida literal en cualquier parte de una expresión regular, debe ser escapada por otra barra invertida. 

| soportes | [] |
| :--: | ---- |
| parentesis | () |
| aparatos ortopédicos | {} |
| operadores | +-?* |
| anclajes | ^ o $ |
| otros | \  .  , |

**/ Delimitadores /**

Muchos idiomas permiten que las expresiones regulares se incluyan o delimiten entre un par caracteres específicos, generalmente la barra diagonal hacia adelante / .

Los delimitadores tienen un impacto en el escape: si el delimitador es / y la expresión regular necesita buscar / literales, entonces la barra inclinada debe escaparse antes de que pueda ser un literal ( ``\/`` ).





## 7.1 Grupos de captura

`` abc_regex = re.compile("^abc", re.MULTILINE);``
