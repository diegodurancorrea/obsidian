---
Fecha_creacion:: <% tp.date.now("YYYY-MM-DD") %>
Ultima_modificacion:: <% +tp.file.last_modified_date("YYYY-MM-DD") %>
Nombre_documento: <% tp.file.title %>
tipo:: <% tp.system.suggester((item) => item, ["Cita", "Textual", "Anotación", "Comentario"]) %>
---

 
