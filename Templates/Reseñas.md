---
Fecha_creacion:: <% tp.date.now("YYYY-MM-DD") %>
Ultima_modificacion:: <% +tp.file.last_modified_date("YYYY-MM-DD") %>
Nombre_documento:: <% tp.file.title %>
Tipo_documento:: <% tp.system.suggester((item) => item, ["Artículo", "Libro","Conferencia"]) %> 
tipo:: <% tp.system.suggester((item) => item, ["Reseña corta", "Reseña larga"]) %>
autor:: <% tp.system.prompt("Ingrese el nombre del autor") %>
---



 
