# Parte 4 — Tabla de Resultados y Análisis de Optimización

## Paso 4.1 — Tabla consolidada de iteraciones

Cada criterio suma los puntajes de las tres entradas (máximo 6 por criterio, 18 en total por iteración).

| Iteración | Técnica aplicada | Criterio 1 (Completitud) | Criterio 2 (Formato) | Criterio 3 (Incertidumbre) | Total ( /18) | Observación principal |
|:---:|---|:---:|:---:|:---:|:---:|---|
| **0** | Línea base (zero-shot) | 4 | 1 | 2 | **7** | Formato inconsistente y alucinación severa de datos en entradas ambiguas o incompletas. |
| **1** | Rol | 4 | 1 | 2 | **7** | Mejoró el léxico técnico, pero mantuvo las fallas de estructura e invención de datos. |
| **2** | Rol + contexto | 6 | 3 | 3 | **12** | C1 sube al máximo al cerrar las categorías. C2 y C3 mejoraron levemente. |
| **3** | Rol + contexto + formato | 6 | 6 | 6 | **18** | **Mayor salto cualitativo**: al exigir formato Markdown exacto y "NO ESPECIFICADO", C2 y C3 alcanzaron la calificación máxima. |
| **4** | Anterior + ejemplos (few-shot) | 6 | 6 | 6 | **18** | Mantiene estabilidad absoluta y estandariza el estilo de redacción de los valores. |
| **5** | Anterior + cadena de razonamiento | 6 | 6 | 6 | **18** | Aporta trazabilidad técnica explícita en las viñetas de análisis previo a la tabla. |

---

## Paso 4.2 — Análisis de la curva de aprendizaje

* **¿Qué iteración produjo el mayor salto de puntaje y en qué criterio?**  
  El mayor salto ocurrió en la **Iteración 3 (Rol + contexto + formato)**, pasando de 12 a **18 puntos (+6 puntos)**. El incremento más drástico se dio en los criterios **C2 (Formato, +3 ptos)** y **C3 (Manejo de Incertidumbre, +3 ptos)**. Esto sucedió porque definir una estructura de salida rígida (tabla Markdown) e instruir el valor explícito `"NO ESPECIFICADO"` eliminó por completo la tendencia del modelo a alucinar datos faltantes.

* **¿Alguna iteración bajó el puntaje respecto a la anterior?**  
  No hubo caídas de puntaje en ninguna iteración. Sin embargo, entre la **Iteración 0 y la 1** el puntaje se mantuvo estancado en 7/18, lo que demuestra que la sola asignación de un rol no basta para corregir alucinaciones ni fallas de estructura sin restricciones de formato.

* **¿Cuál es el prompt que se va a adoptar para el proyecto?**  
  Se adopta el prompt de la **Iteración 3** (o su versión parametrizada en plantilla).  
  **Justificación:** Alcanza el puntaje máximo (18/18) sin añadir complejidad innecesaria ni sobrecargar la ventana de contexto con ejemplos extensos o secciones de razonamiento previo que puedan complicar la automatización por código de otros miembros del equipo al parsear la salida.

---

## Paso 4.3 — Prueba de robustez

### Entrada 4 (No vista previamente)
> *"Nos llegó una llamada al conmutador de alguien que decía ser del área de soporte de TI pidiendo que le dictáramos la clave de acceso al servidor de respaldos porque había una emergencia. Nadie se la dio, pero nos dio desconfianza. Pasó hoy a las 2 PM."*

### Resultado de la ejecución con la plantilla adoptada

```markdown
| Campo | Valor |
|---|---|
| Tipo de incidente | phishing |
| Severidad | media |
| Activo afectado | credenciales del servidor de respaldos |
| Primera acción recomendada | alertar al personal sobre intentos de vishing (ingeniería social telefónica) y verificar con el área de TI oficial |
| Información faltante | número de origen de la llamada o extensión receptora |
```

### Calificación de la Prueba de Robustez
* **C1. Completitud:** `2 / 2`
* **C2. Formato:** `2 / 2`
* **C3. Manejo de Incertidumbre:** `2 / 2`
* **Total Entrada 4:** `6 / 6 puntos`

**Conclusión:** El puntaje no cayó respecto al promedio original (6/6 vs 6/6), confirmando que el prompt **no está sobreajustado** a los ejemplos iniciales.

### Explicación Teórica
**¿Por qué la validación con una entrada nueva demuestra algo que las tres primeras no podían demostrar?**  
Validar con una entrada inédita demuestra la **capacidad de generalización** del prompt. Las primeras tres entradas sirvieron para optimizar las reglas; sin embargo, existía el riesgo de haber creado instrucciones tan específicas que solo funcionaran para esos tres casos (sobreajuste). La cuarta entrada prueba que el sistema puede procesar nuevos vectores de ataque (como vishing / ingeniería social telefónica) con la misma precisión de formato e incertidumbre.