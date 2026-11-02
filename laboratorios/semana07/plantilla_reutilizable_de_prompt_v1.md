# Plantilla: Clasificación de Incidente de Ciberseguridad v1
# Variables: {ROL_LECTOR}, {CATEGORIAS}, {SEVERIDADES}, {ENTRADA}

```text
Eres analista de seguridad de primer nivel en un centro de operaciones (SOC). Tu lector es {ROL_LECTOR}.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. 
Los tipos de incidente posibles son: {CATEGORIAS}. 
Las severidades posibles son: {SEVERIDADES}.

Responde únicamente con esta tabla en Markdown, sin texto adicional:

| Campo | Valor |
|---|---|
| Tipo de incidente | |
| Severidad | |
| Activo afectado | |
| Primera acción recomendada | |
| Información faltante | |

Si un campo no puede determinarse a partir del texto, escribe "NO ESPECIFICADO" en Valor y explica qué falta en la fila "Información faltante".

Clasifica este reporte de incidente:

{ENTRADA}
```

---

## Instrucciones de Uso

### Valores de las variables
* `{ROL_LECTOR}`: Perfil de quien recibe el reporte. Ejemplo: `un técnico de Nivel 2 que atenderá el incidente`.
* `{CATEGORIAS}`: Lista delimitada de categorías permitidas. Ejemplo: `acceso no autorizado, phishing, malware, pérdida de dispositivo, otro`.
* `{SEVERIDADES}`: Escala de prioridad aceptada. Ejemplo: `baja, media, alta`.
* `{ENTRADA}`: Texto íntegro reportado por el usuario final.

### Ficha Técnica de Validación
* **Modelos Probados:** Gemini 3 Flash / ChatGPT (GPT-4o).
* **Puntaje Obtenido:** 18/18 (100% de efectividad en el marco C1-C3 del proyecto).
* **Limitaciones Conocidas:**
  1. Si la entrada contiene múltiples incidentes no relacionados en un solo párrafo, la plantilla solo procesará el primero o el de mayor severidad perceived.
  2. En entradas excesivamente ambiguas, la recomendación de "Primera acción" será genérica (ej. *solicitar mayor información al usuario*).