Selección de modelo generativo para el proyecto AuditGuard IA

Modelos evaluados

Gemini 1.5 Pro / Flash (Google AI Studio): Evaluado en la Semana 5 para pruebas directas de temperatura, conteo exacto de tokens y ventana de contexto extensible.

ChatGPT (GPT-4o / GPT-3.5): Evaluado en la Semana 1 para pruebas generales de redacción y comprensión del lenguaje natural.

DeepSeek (V2/R1): Evaluado en la Semana 1 para la generación de código y análisis lógico de reglas de seguridad.

Gemini (Interfaz Web): Evaluado como alternativa de consulta rápida sin control fino de parámetros.

Evidencia de tokens

Tokens de mi documento de referencia: 1,150 tokens aproximadamente (para el documento de 4 páginas).

Caracteres por token en español: ~3.8 caracteres por token.

Implicación para mi proyecto: Como el español genera un menor número de caracteres por token que el inglés (es más "caro"), debo contemplar un margen extra de consumo de tokens al procesar reglamentos o reportes técnicos extensos en español.

Evidencia de temperatura

Temperatura que usaré para tareas de precisión: 0.0 porque garantiza consistencia absoluta al arrojar respuestas idénticas en el 100% de las ejecuciones, evitando alucinaciones en la extracción de normativas o reglas de firewall.

Temperatura que usaré para tareas creativas: 1.5 (o 0.7 para variabilidad moderada) porque incrementa el número de palabras distintas generadas (mayor vocabulario) y permite proponer ideas o redactar explicaciones más dinámicas sin quedarse con la opción determinista más básica.

Evidencia de contexto

Comportamiento observado: El modelo no presentó fallas ni alucinaciones hasta los 9,200 tokens evaluados (intento 4 con 8 copias del documento), manteniendo la capacidad de recuperar el código AZUL-7342 independientemente de si estaba al inicio, a la mitad o al final del texto.

Mis documentos del proyecto miden aproximadamente: 4,500 tokens por manual técnico o normativa.

Por lo tanto: Caben completos dentro de la ventana de contexto evaluada sin necesidad de resumirlos o dividirlos previamente.

Decisión

Modelo elegido: Gemini (vía Google AI Studio / API).

Configuración:

Temperatura 0.0 para tareas de extracción, análisis de cumplimiento normativo y revisión de código de seguridad.

Temperatura 0.7 a 1.5 para lluvias de ideas, redacción de reportes ejecutivos y generación de escenarios creativos.

Restricciones de datos según la política de la semana 4: No se ingresará información personal identificable (PII), credenciales de acceso, llaves privadas ni logs de red con direcciones IP públicas reales de clientes. Únicamente se utilizarán datos ficticios, anonimizados o de dominio público para procesar en el modelo.
