# Política de datos del proyecto Análisis de patrones de acceso

## 1. Alcance

Esta política cubre los datos del registro de accesos que se limpia y analiza en el proyecto:

- D1: nombre de la persona (identificador directo)
- D2: correo electrónico (identificador directo)
- D3: teléfono (identificador directo)
- D4: fecha y hora de acceso (dato de comportamiento; puede identificar de forma indirecta)
- D5: área y tipo de empresa (dato de contexto; identificador indirecto en combinación con otros)
- D6: seudónimo de la persona, P001… (dato seudonimizado) y su llave, la tabla de seudónimos (dato de alto riesgo)

## 2. Ciclo de vida

El recorrido completo está en el diagrama `ciclo_vida_dato_proyecto.drawio` (y su imagen `.png`). Las seis etapas y su responsable son:

- Captura: responsable del proyecto. Se recibe el registro y se toma solo lo necesario.
- Almacenamiento: analista de datos y proveedor de nube. El original queda intacto y se trabaja sobre una copia.
- Uso: analista de datos. Limpieza, validación y búsqueda de accesos inusuales.
- Compartición: líder del proyecto. Solo se publica la versión anonimizada.
- Retención: líder del proyecto. Se conserva únicamente lo necesario para el análisis y el reporte.
- Eliminación: líder del proyecto y administrador del sistema. Borrado seguro del original y de la llave, con confirmación documentada.

## 3. Normativa aplicable

El detalle está en la matriz `matriz_cumplimiento_proyecto.xlsx`. En resumen:

- LFPDPPP (México): aplica a los datos personales D1 a D5. Exige consentimiento, aviso de privacidad, proporcionalidad y conservación limitada, y reconoce el derecho a oponerse a un tratamiento automatizado sin intervención humana (Art. 26, fr. II).
- Ley de IA de la UE: se toma como referencia, porque el proyecto no la tiene como obligatoria; sus requisitos de supervisión humana y de revisión de sesgos son buenas prácticas.
- NIST AI RMF: marco voluntario que se sigue para gestionar riesgos (Gobernar, Mapear, Medir y Gestionar).
- Pendiente: confirmar los números de artículo de la LFPDPPP vigente en el texto oficial.

## 4. Controles comprometidos

- Declarar en el reporte el uso de IA y revisar las condiciones de servicio de cada tercero antes de usarlo. Responsable: analista de datos.
- Documentar el origen y el consentimiento del dato y publicar un aviso de privacidad con la finalidad declarada. Responsable: líder del proyecto.
- Capturar solo los datos necesarios y quitar D1, D2 y D3 en la versión de análisis. Responsable: analista de datos.
- Mantener en el reporte una sección de riesgos alineada con el diagrama. Responsable: líder del proyecto.
- Revisar a mano cualquier acceso inusual antes de atribuirlo a una persona; no tomar decisiones automáticas y dejar un canal para oponerse. Responsable: líder del proyecto.
- Revisar si los accesos inusuales se concentran en un área o tipo de empresa antes de concluir. Responsable: analista de datos.
- Usar seudónimos y no subir nunca la llave al repositorio. Responsable: analista de datos.
- Definir un plazo de retención y borrar el original y la llave al terminar, con confirmación documentada. Responsable: líder del proyecto y administrador del sistema.

## 5. Manejo de datos con herramientas de IA

Estas reglas aplican a ChatGPT, Gemini, Deepseek, Dify y a cualquier otro modelo, agente o herramienta de automatización:

- Sí se puede ingresar: datos ficticios que imiten la estructura del registro, texto sin datos personales y la versión anonimizada, solo después de verificar que ninguna combinación de campos identifique a alguien.
- No se puede ingresar nunca: D1, D2, D3, el registro original, la tabla de seudónimos ni credenciales o llaves.
- Antes de usar una herramienta nueva se revisan sus condiciones de servicio (entrenamiento, retención y cómo desactivarlos); si no se pueden entender, se usa solo con datos ficticios.
- Todo lo que devuelva un modelo (cifras, citas, artículos de ley) se verifica en la fuente original antes de usarlo.
- Si hay duda sobre un dato, se trata como no permitido. Si ocurre un error, se deja de usar la herramienta, se avisa al líder del proyecto y se anota lo ocurrido.

## 6. Revisión

- Esta política se revisa al terminar cada etapa del curso (cada vez que cambien los datos o las herramientas) y al menos una vez por semestre.
- También se revisa de inmediato si se agrega una herramienta de IA nueva o un dato nuevo.
- La elabora el analista de datos y la aprueba el líder del proyecto.
- Cada cambio se registra con fecha en el repositorio.
