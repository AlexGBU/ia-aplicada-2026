# Semana 03: transformaciones y errores detectados

Laboratorio de limpieza y anonimización de un registro de accesos. Todos los datos son ficticios.

Archivos de esta carpeta:
- `accesos_crudo.csv`: datos originales, sin tocar (incluye los errores introducidos).
- `accesos_anonimizado.csv`: versión anonimizada, exportada como valores.
- `transformaciones.md`: este documento.

## Tabla de transformaciones (accesos_crudo → accesos_anonimizado)

| Columna original | Qué le hice | Técnica | Por qué |
|---|---|---|---|
| id | Conservar | Sin cambio | Es solo un número de registro y no identifica a nadie por sí solo. Sirve para contar y ordenar accesos. |
| nombre | Seudonimizar | Código estable (P001 a P036) con BUSCARV contra tabla_seudonimos | Es un identificador directo. El código permite ver cuántas veces aparece una persona sin saber quién es. Mientras exista la tabla, sigue siendo dato personal. |
| correo | Eliminar | Se quitó la columna; se probó enmascarar (l***@correo.com) y se descartó | Es un identificador directo y no hace falta para el análisis. Enmascarado no sirve para contactar a nadie y deja la inicial y el dominio, que ayudan a reidentificar. |
| telefono | Eliminar | Se quitó la columna | Es un identificador directo y no aporta nada a los patrones de acceso. |
| fecha_acceso | Generalizar | semana, con NUM.DE.SEMANA en modo ISO (21) | La fecha exacta, combinada con otros datos, puede señalar a una persona. La semana conserva la tendencia y pierde la precisión. |
| hora_entrada | Generalizar | franja (Madrugada, Mañana, Tarde, Noche) | La hora exacta es un identificador indirecto. La franja conserva cuándo entró, aunque "Noche" mezcla horas normales con fuera de horario. |
| area | Conservar | Sin cambio | Es necesaria para el análisis y por sí sola no identifica a nadie. |
| empresa | Generalizar | tipo_empresa (Constructora, Diseño, Soporte TI), con la tabla mapa_tipo_empresa | Con pocas personas por empresa, el nombre apunta a individuos. El giro conserva el contexto sin nombrar a la organización. |
| motivo | Conservar | Sin cambio | Es necesaria para el análisis y por sí sola no identifica a nadie. |

Notas:
- La hoja `tabla_seudonimos` (la llave que relaciona cada nombre con su código) **no se sube**: permite volver a identificar a las personas.
- Riesgo residual: 5 de 16 combinaciones de `tipo_empresa` + `area` + `franja` aparecen una sola vez, y al añadir `semana` 25 de las 36 filas quedan únicas. `franja` también mezcla entradas normales de 18:00 a 22:00 con accesos fuera de horario.
- Ajustes recomendados que no se aplicaron: `franja` en "Dentro de horario / Fuera de horario" (06:00 a 22:00), `tipo_dia` (laboral o fin de semana) y `semana` a mes.

## Errores detectados (limpieza contra la clave)

| Tipo de error | Introducidos (clave) | Detectados por mi limpieza | Faltaron | Por qué faltaron | Detectados que la clave no lista |
|---|---|---|---|---|---|
| Fila duplicada exacta | 2 | 4 | 0 | — | 2 |
| Fecha en formato distinto | 4 | 5 | 0 | — | 1 |
| Fecha inválida | 1 | 1 | 0 | — | 0 |
| Correo sin dominio o con mayúsculas | 5 | 6 | 0 | — | 1 |
| Teléfono con espacios o con menos de 10 dígitos | 4 | 4 | 0 | — | 0 |
| Área con distinta capitalización | 5 | 5 | 0 | — | 0 |
| Celda vacía en empresa o teléfono | 3 | 2 | 1 | El id 3 (teléfono vacío) no existe en el archivo: la fila que le tocaba es copia del id 1. | 0 |
| Hora fuera de horario laboral | 3 | 4 | 0 | — | 1 |
| Total | 27 | 31 | 1 |  | 5 |

Notas:
- Los conteos incluyen las copias eliminadas como duplicados, igual que la clave.
- Los duplicados reales están en las filas 4, 5, 11 y 12 del crudo, no solo en la 4 y la 11.
- El único faltante es un error que la clave lista pero el archivo no contiene (teléfono vacío del id 3).
- Errores no listados en la clave que sí se corrigieron: el nombre del id 8 ("ana torres") y "supervision" sin acento en el motivo.
- No se corrigieron las horas fuera de horario (23:40, 02:15, 05:30 y 22:30): son accesos inusuales reales que el análisis debe encontrar.
