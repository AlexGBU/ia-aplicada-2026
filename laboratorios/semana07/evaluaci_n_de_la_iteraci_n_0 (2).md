# Evaluación de la Iteración 0 (Línea Base)

## Tabla general de evaluación

| Entrada | C1. Completitud (0-2) | C2. Formato (0-2) | C3. Manejo de Incertidumbre (0-2) | Total Entrada (0-6) | Observación principal |
|---|:---:|:---:|:---:|:---:|---|
| **Entrada 1 (Clara y completa)** | 2 | 1 | 2 | **5** | El análisis fue adecuado, pero el formato fue texto libre con viñetas en lugar de una estructura estandarizada de triage. |
| **Entrada 2 (Información faltante)** | 1 | 0 | **0** | **1** | Inventó detalles no presentes en la entrada (vector de phishing, hora de acceso e IP), omitiendo marcar explícitamente la información faltante. |
| **Entrada 3 (Contradictoria/Ambigua)** | 1 | 0 | **0** | **1** | Intentó ofrecer una solución directa ignorando el conflicto de seguridad fundamental entre el bloqueo total y el acceso BYOD sin restricciones. |

### Puntaje Total de la Iteración 0
$$\text{Puntaje Total Iteración 0} = 5 + 1 + 1 = \mathbf{7 / 18 \text{ puntos}}$$

---

## Ficha detallada para captura obligatoria (Entrada 2 — Información faltante)

### Texto de entrada evaluado
> *"Hola, creo que alguien entró a mi correo corporativo porque me llegó un aviso raro de inicio de sesión desde otro país. No sé desde cuándo pasó. Ya cambié la contraseña. ¿Qué hago ahora?"*

### Calificación por criterio

* **C1. Completitud de Triage Técnico: `1 / 2`**
  * *Razón:* Cubrió las acciones básicas de contención previa, pero omitió campos requeridos en una hoja de triage profesional (p. ej., asignación formal de impacto en la infraestructura o requerimientos de preservación de evidencia).
* **C2. Formato y Estructura Auditables: `0 / 2`**
  * *Razón:* Generó una respuesta en texto continuo con lista numerada estándar. No utilizó ninguna plantilla de respuesta a incidentes ni delimitadores estructurados.
* **C3. Manejo de Incertidumbre y Supuestos: `0 / 2` (Fallo crítico)**
  * *Razón:* Asumió con certeza absoluta que el incidente se originó por un ataque de *Phishing* y recomendó pasos basados en la presencia de direcciones IP y logs que nunca se proporcionaron en la entrada, en lugar de declarar explícitamente los datos faltantes para realizar el diagnóstico.

**Puntaje final de la Entrada 2:** `1 / 6 puntos`