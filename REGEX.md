---
Fecha_creacion:: 2024-02-04
Ultima_modificacion:: NaN
Nombre_documento: REGEX
tipo:: Componente del lenguaje
autor:: Regex
---

# 1.1 ¿Qué significa 'expresión regular'?

>*Las expresiones regulares expresan un lenguaje definido por una gramática regular que se puede resolver con un [[autómata finito no determinista (NFA)]], donde la coincidencia está representada por los estados.* 

###### Ejemplo:

```copy
 ^[01]*1$
```

![[Pasted image 20240204004057.png]]
Los autómatas pueden variar los motores de expresiones regulares. El nivel al que pueden aspirar es hacia  patrones escalones más arriba en el modelo lingüístico de Noam Chomsky.  El motor <code>re</code> de Python sólo soporta el nivel *regular*. 

## Agrupación regular y atómica 

#### regular 

> *Los grupos regulares que no capturan permiten que el motor vuelva a ingresar al grupo e intente hacer coincidir algo diferente (como una alternancia diferente, o hacer coincidir menos caracteres cuando se usa un cuantificador)*

Los grupos regulares que no capturan tienen el formato ``(?:...)`` con un ``?:``

Es decir, en la agrupación regular el motor de búsqueda tiene en cuenta los estados anteriores de coincidencia y puede recordarlos para hacer coincidir con la consulta. En el artículo *[[attencion is all you need]]* se destaca la importancia de revisar los estados anteriores. 
#### Atómica

> *Los grupos atómicos difieren de los grupos regulares que no capturan, ya que está prohibido el retroceso. Una vez que el grupo sale, toda la información de seguimiento se descarta, por lo que no se pueden intentar coincidencias alternativas*

Los grupos atómicos tienen el formato  ``(?>...)``  con un ``?>``

## Caracteres de ancla

> *Una gran cantidad de motores de expresiones regulares utilizan un modo "multilínea" para buscar varias líneas en un archivo de forma independiente. Por lo tanto, al usar $ , estos motores coincidirán con los finales de todas las líneas. Sin embargo, los motores que no utilizan este tipo de modo multilínea solo coincidirán con la última posición de la cadena proporcionada para la búsqueda.*

``g$`` 

## Clases y negación 

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

## Cuantificadores posesivos
pag32

