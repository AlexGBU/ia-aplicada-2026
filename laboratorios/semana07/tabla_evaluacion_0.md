Optimización de PromptsPaso 3.1 — Iteración 1: Asignar un rolPrompt UtilizadoEres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Clasifica este reporte de incidente:

[ENTRADA]
Resultados y PuntajesEntradaC1. Completitud (0-2)C2. Formato (0-2)C3. Incertidumbre (0-2)Total Entrada (0-6)Observación principalEntrada 12125El vocabulario cambió a uno más técnico y enfocado en la operación (SOC), pero sigue entregando texto libre.Entrada 21001Mantiene la alucinación de datos (asume IPs y vectores de malware) a pesar de adoptar un tono más técnico.Entrada 31001Intenta resolver el dilema técnico con terminología de red, pero no formaliza la contradicción.Total Iteración 1: 7 / 18 puntosPaso 3.2 — Iteración 2: Agregar contextoPrompt UtilizadoEres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: acceso no autorizado, phishing, malware, pérdida de dispositivo, otro. Las severidades posibles son: baja, media, alta.

Clasifica este reporte de incidente:

[ENTRADA]
Resultados y PuntajesEntradaC1. Completitud (0-2)C2. Formato (0-2)C3. Incertidumbre (0-2)Total Entrada (0-6)Observación principalEntrada 12125Clasificó correctamente dentro de las categorías cerradas (Acceso no autorizado / Alta).Entrada 22103C1 sube porque ya sabe qué categorías usar (Phishing / Media), pero C3 falla al no marcar explícitamente la falta de datos.Entrada 32114Identificó la categoría (Otro / Media) y mejoró el marco de referencia gracias al contexto.Total Iteración 2: 12 / 18 puntosPaso 3.3 — Iteración 3: Exigir un formato de salidaPrompt UtilizadoEres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: acceso no autorizado, phishing, malware, pérdida de dispositivo, otro. Las severidades posibles son: baja, media, alta.

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

[ENTRADA]
Resultados y PuntajesEntradaC1. Completitud (0-2)C2. Formato (0-2)C3. Incertidumbre (0-2)Total Entrada (0-6)Observación principalEntrada 12226Cumplimiento perfecto del formato estandarizado y completitud.Entrada 22226C2 y C3 suben drásticamente. Al exigir "NO ESPECIFICADO", no inventó la IP ni la hora del ataque.Entrada 32226Identificó las contradicciones en la fila de información faltante y no inventó una solución técnica absurda.Total Iteración 3: 18 / 18 puntosPregunta Teórica — Paso 3.3¿Por qué decirle al modelo qué hacer cuando no tiene información funciona mejor que pedirle "no inventes"?Decirle a un LLM "no inventes" o "no alucines" es una instrucción de restricción negativa que no le proporciona una vía de escape estructural en su proceso probabilístico de generación de tokens. Los modelos de lenguaje están optimizados para completar el texto de forma coherente; si encuentran un vacío de información, la ruta con mayor probabilidad estadística es completar ese vacío con datos verosímiles pero falsos.Por el contrario, darle una regla explícita e instruir un token de reemplazo exacto (como escribir "NO ESPECIFICADO") le da un camino de salida válido dentro de la estructura exigida. Esto convierte la incertidumbre en un valor de entrada válido en su generación, evitando la tentación probabilística de rellenar los huecos con invenciones.Paso 3.4 — Iteración 4: Agregar ejemplos (Few-Shot)Prompt UtilizadoEres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: acceso no autorizado, phishing, malware, pérdida de dispositivo, otro. Las severidades posibles son: baja, media, alta.

Ejemplo de entrada:
"Recibí un correo del banco pidiendo que confirme mi tarjeta en un enlace. Di clic y puse mis datos. Fue hoy a las 10 am desde la laptop de la oficina."

Ejemplo de salida:
| Campo | Valor |
|---|---|
| Tipo de incidente | phishing |
| Severidad | alta |
| Activo afectado | credenciales bancarias del usuario; laptop de oficina |
| Primera acción recomendada | contactar al banco para bloquear la tarjeta y reportar al área de seguridad |
| Información faltante | ninguna |

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

[ENTRADA]
Resultados y PuntajesEntradaC1. Completitud (0-2)C2. Formato (0-2)C3. Incertidumbre (0-2)Total Entrada (0-6)Observación principalEntrada 12226El ejemplo consolidó la precisión del vocabulario dentro de la tabla.Entrada 22226El ejemplo guió la forma exacta de clasificar activos sin copiar datos falsos.Entrada 32226Formato exacto e impecable manejo de la contradicción.Total Iteración 4: 18 / 18 puntosPaso 3.5 — Iteración 5: Cadena de Razonamiento (Chain of Thought)Prompt UtilizadoEres analista de seguridad de primer nivel en un centro de operaciones. Tu lector es un técnico que atenderá el incidente y necesita información precisa.

Contexto: este texto proviene de un formulario que llenan usuarios sin conocimientos técnicos. Los tipos de incidente posibles son: acceso no autorizado, phishing, malware, pérdida de dispositivo, otro. Las severidades posibles son: baja, media, alta.

Antes de la tabla, escribe una sección titulada "Análisis" con tres viñetas: 
- qué información explícita hay en el texto
- qué se puede inferir con seguridad
- qué no se puede determinar

Después escribe la tabla con el formato exacto:

| Campo | Valor |
|---|---|
| Tipo de incidente | |
| Severidad | |
| Activo afectado | |
| Primera acción recomendada | |
| Información faltante | |

Si un campo no puede determinarse a partir del texto, escribe "NO ESPECIFICADO" en Valor y explica qué falta en la fila "Información faltante".

Clasifica este reporte de incidente:

[ENTRADA]
Resultados y PuntajesEntradaC1. Completitud (0-2)C2. Formato (0-2)C3. Incertidumbre (0-2)Total Entrada (0-6)Observación principalEntrada 12226La sección de análisis desglosa impecablemente el contexto antes de llenar la matriz.Entrada 22226Máxima transparencia: separa lo conocido de lo desconocido de forma quirúrgica.Entrada 32226Evidencia el conflicto técnico explícitamente en las viñetas antes de concluir la tabla.Total Iteración 5: 18 / 18 puntosTabla Comparativa Global de Puntajes (Iteración 0 a Iteración 5)IteraciónTécnica AplicadaEntrada 1Entrada 2Entrada 3Puntaje Total ( /18)Iteración 0Línea base (Prompt mínimo)5117Iteración 1Asignación de Rol5117Iteración 2Adición de Contexto y Categorías53412Iteración 3Estructura de Formato y Manejo de Vacíos66618Iteración 4Ejemplos Guiados (Few-Shot)66618Iteración 5Cadena de Razonamiento (CoT)66618Captura Obligatoria — Ficha de la Iteración 5 (Entrada 2: Información Faltante)Texto de entrada procesado"Hola, creo que alguien entró a mi correo corporativo porque me llegó un aviso raro de inicio de sesión desde otro país. No sé desde cuándo pasó. Ya cambié la contraseña. ¿Qué hago ahora?"Respuesta exacta obtenida del modeloAnálisisQué información explícita hay en el texto: El usuario recibió una notificación de inicio de sesión no habitual desde otro país en su correo corporativo; no conoce la fecha de inicio del incidente; el usuario ya realizó un cambio preventivo de contraseña.Qué se puede inferir con seguridad: Hubo una alerta de posible acceso no autorizado a la cuenta de correo corporativo; el usuario no cuenta con conocimientos técnicos de ciberseguridad.Qué no se puede determinar: La dirección IP de origen, el tipo exacto de aviso, si hubo filtración o exfiltración de correos, si el dispositivo del usuario está infectado con malware o si se mantienen sesiones activas en otros dispositivos.CampoValorTipo de incidenteacceso no autorizadoSeveridadmediaActivo afectadocuenta de correo corporativoPrimera acción recomendadacerrar todas las sesiones activas, habilitar autenticación multifactor (MFA) y enviar cabeceras del correo de alerta al SOCInformación faltantedirección IP de origen, logs de auditoría del servidor de correo y confirmación de sesiones cerradasCalificación Anotada (Iteración 5 — Entrada 2)C1. Completitud de Triage Técnico: 2 / 2 — Todos los campos clave de triage requeridos fueron completados correctamente.C2. Formato y Estructura Auditables: 2 / 2 — Se generó la sección de Análisis respetando las tres viñetas requeridas y la tabla Markdown exacta.C3. Manejo de Incertidumbre y Supuestos: 2 / 2 — Se desglosó explícitamente en el análisis lo que no se podía determinar y se llenó la casilla de "Información faltante" sin inventar datos como IPs falsas o vectores no confirmados.Puntaje Entrada 2 (Iteración 5): 6 / 6 puntos
