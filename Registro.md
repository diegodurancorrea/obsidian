---
Fecha_creacion:: 2024-01-25
Ultima_modificacion:: NaN
Nombre_documento: Registro
tipo:: resumen
---

 
# TOTAL

```dataview 
table Fecha_creacion as "Fecha Creación" , Ultima_modificacion as "Última Modificación",tipo

From !"Templates" & !"Imagenes" & !"Excalidraw"
```
# RESEÑAS

``` dataview 
table Fecha_creacion as "Fecha Creación" , tipo , autor 
from !"Templates" 
where tipo = "Reseña corta"  or  tipo = "Reseña larga"
```
# CODIGO

``` dataview 
table Fecha_creacion as "Fecha Creación" , tipo , autor 
from !"Templates" 
where tipo = "Componente del lenguaje"  or  tipo = "Librería" or tipo = "Lógica"
```
