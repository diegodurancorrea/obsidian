---
Fecha_creacion:: <% tp.date.now("YYYY-MM-DD") %>
Ultima_modificacion:: <% tp.file.last_modified_date("YYYY-MM-DD") %>
Nombre_documento: <% tp.file.title %>
tipo:: <% tp.system.suggester((item) => item, ["Componente del lenguaje", "Librería", "Lógica"]) %>
autor:: <% tp.system.prompt("Ingrese el nombre del lenguaje") %>
---
