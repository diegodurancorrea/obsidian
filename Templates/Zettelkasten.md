---
Fecha_creacion:: <% tp.date.now("YYYY-MM-DD") %>
Ultima_modificacion:: <% tp.file.last_modified_date("YYYY-MM-DD") %>
Nombre_documento:: <% tp.file.title %>
Tipo_de_nota:: <% tp.system.suggester((item) => item, ["nota corta", "nota larga","nota de extensión"]) %> 
trabajo asociado:: <% tp.system.suggester((item) => item, ["trabajo grado", "pregrado","personal","semillero"]) %>
---


