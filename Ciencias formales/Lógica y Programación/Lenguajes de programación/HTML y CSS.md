---
Fecha_creacion:: 2025-10-14
Ultima_modificacion:: 2025-10-13
Nombre_documento: HTML y CSS
tipo:: Componente del lenguaje
autor:: html y css
---
Esta son las notas que tomé cuando vi el curso de *html* y *css* en Platzi. Espero que pueda servir como notas de repaso.  
# HTML

Por sus siglas *Hiper text Markup Lenguage*, es el lenguaje para crear y estructurar el contenido de las páginas web. Se fundamenta en etiquetas contenedoras que organizan y definen los elementos visuales que configura la *maquetación* del proyecto. 

Se recomienda emplear **html semántico**, también conocido como marcado semántico, que engloba las etiquetas *html* que transmiten el significado (o semántica) de su contenido, es decir, nos indican que tipo de contenido contienen y qué función desempeñan en nuestra página web; existen las etiquetas semánticas para el contenido y para la estructura. 

A continuación un ejemplo del maquetamiento usando ambas etiquetas semánticas de un archivo html básico: 

~~~html

<!DOCTYPE html>

<html lang="en">
<head> <!-- no visible -->
	<meta charset="UTF-8" />
	<meta name="robots" content="index, follow" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<link rel="stylesheet" href= "../css/style.css" /> <!-- responsive design -->
	<title>Flask App</title>
<!-- <style></style> --> <!-- estilos internos -->

</head>
<body> <!-- visible en el cliente -->

	<header>
		<nav> <!-- barra de navegación -->
		</nav>	
	</header>
	
	<main>
		<section class= 'primera sección'>
			<p> este es un párrafo </p> <!-- párrafo -->
			<figure class = 'primera imagen'>
				<img src="/../images/mango.png" alt="imagen de mango" /> <!-- la ruta relativa se interpreta desde la ubicación del archivo HTML -->
			<figcaption> images ivy DTHumano2025*+</figcaption> <!-- foot description -->
			</figure>
		
			<video controls preload="auto">
				<source src=".mp4#t=10,60"/>
			</video>
		</section>
		
		<section class= 'segunda sección'>
		
		</section>
	
	</main>
	
	<footer>
		<h1 class="titulo"> Abajo el link </h1> <!-- encabezado principal -->
		<a href="#">Link</a> <!-- enlace -->
	</footer>
	
</body>
</html>
~~~

Nótese que  las etiquetas utilizadas como etiquetas contenedoras —header, main, footer— nos ayudan a reconocer la posición de los elementos web—video,figure,p— en la página web. Existen muchas más etiquetas semánticas que las expuestas. 

Una vez tenemos nuestra página web maquetada con la estructura que construimos para distribuir la información, procedemos a aplicar estilo a las etiquetas con las que diseñamos nuestra página. Para hacerlo usamos *CSS*. 
# CSS

### Conceptos Fundamentales

CSS (Cascading Style Sheets) define la **apariencia visual** de los elementos HTML. Una **regla CSS** está compuesta por un **selector**, unas **llaves `{}`**, y dentro de ellas una o más **declaraciones** con pares `propiedad: valor;`

~~~css
p {
  color: blue;
  font-size: 1.6rem;
}
~~~
#### Selectores
- `#id` → selecciona por identificador único.
- `.class` → selecciona por clase.
- `tag` → selecciona por etiqueta HTML.
- `*` → selecciona todos los elementos.
#### Pseudoclases y pseudoelementos
- `:hover`, `:active`, `:first-child`
- `::before`, `::after`, `::selection`
#### Modelo de Caja
Cada elemento en CSS es una **caja** compuesta por:  
`content + padding + border + margin`
>  Recomendación:  
> `* { box-sizing: border-box; margin: 0; padding: 0; }`

Esto evita desbordamientos y facilita el control del tamaño.

### Herencia y Especificidad
La **herencia** permite que los estilos de un elemento padre se transmitan a sus hijos.   En caso de conflicto, CSS aplica las siguientes reglas de prioridad:
1. `!important`
2. Estilos en línea (`style=""`) del árbol html
3. Selectores por `id`
4. Selectores por clase o pseudoclase
5. Selectores por etiqueta
> En caso de empate, gana la **última declaración** en el documento.
### Medidas y Unidades
- **Absolutas:** no cambian con el tamaño del dispositivo (`px` --> píxeles).
- **Relativas:** se adaptan (`em`, `rem`, `%`, `vw`, `vh`).
    - `em` → relativo al tamaño de fuente del padre inmediato.
    - `rem` → relativo al tamaño base (*root*) del documento (`html { font-size: 62.5%; }` = 1rem → 10px).

### Position y Display
#### Position
Controla la **ubicación** de los elementos:
- `static` (por defecto)
- `relative`
- `absolute`
- `fixed`
- `sticky`
> Para posiciones diferentes a `static` se habilita alinear, distribuir y re dimensionar el elemento libremente en su contenedor 
#### Display
Determina **cómo se muestra** un elemento, empleado principalmente para distribuir varios elementos contenidos en la misma etiqueta padre:
- `block`: ocupa todo el ancho de la página.
- `inline`: solo el espacio necesario.
- `inline-block`: combina características de ambos.
- `none`: oculta el elemento.
###  Flexbox
`display: flex` convierte al elemento padre en un **contenedor flexible**.  
Esto permite alinear, distribuir y redimensionar los hijos con facilidad.
#### Propiedades principales
- **flex-direction:** dirección del eje principal (`row`, `column`).
- **justify-content:** alineación horizontal (`flex-start`, `center`, `space-between`, etc.).
- **align-items:** alineación vertical (`flex-start`, `center`, `stretch`, etc.).
- **flex-wrap:** permite saltos de línea si los elementos exceden el contenedor.
- **order:** define el orden de los elementos.
- **flex-grow:** cuánto espacio extra ocupa un elemento.
- **flex-basis:** tamaño inicial de un elemento.
> 🔗 [Guía completa de Flexbox – CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
### Variables en CSS
Las **variables** permiten almacenar valores reutilizables:
~~~css
:root {
  --primary-color: #322f3d;
  --font-size: 1.6rem;
} 

header {
  background: var(--primary-color);
  font-size: var(--font-size);
}
~~~

> Se declaran con `--nombre-variable` dentro de `:root` (alcance global). Se usan con la función `var(--nombre-variable)`.

### Tipografías y Web Fonts
#### Familias genéricas:
- `serif` (Times New Roman)
- `sans-serif` (Verdana)
- `cursive`
- `monospace` (Roboto Mono)
#### Formas de importar fuentes
1. Desde Google Fonts mediante `<link>` en el `<head>`.
2. Descargando el archivo `.ttf` y usándolo localmente:
~~~css
@font-face {
  font-family: 'ChakraPetch-Regular';
  src: url(../fonts/ChakraPetch-Regular.ttf);
}
~~~
### Diseño Responsivo (Responsive Design)
El **Responsive Design** adapta el diseño a diferentes tamaños de pantalla mediante **media queries**.

~~~css
@media (min-width: 600px) {
	.contenedor{ 
	max-width: 600px;
	margin: 0 auto ; 
	} 
	
	.col { width: 50% };
}
~~~
O cargando hojas de estilo específicas
~~~html
<link rel="stylesheet" href="tablet.css" media="screen and (min-width: 600px)">
~~~
#### Patrones comunes de diseño responsivo
- **Mostly Fluid:** cuadrícula fluida con pocos puntos de interrupción.
- **Column Drop:** las columnas se apilan verticalmente en pantallas pequeñas.
- **Layout Shifter:** el más dinámico, permite reordenar elementos y cambiar posiciones según el ancho del viewport.

~~~html
<picture>
  <source media="(min-width: 1000px)" srcset="large.jpg" />
  <source media="(min-width: 800px)" srcset="medium.jpg" />
  <img src="small.jpg" alt="responsive image" />
</picture>
~~~

