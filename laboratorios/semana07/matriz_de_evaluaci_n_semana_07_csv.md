Iteracion,Tecnica_Aplicada,Entrada,C1_Completitud,C2_Formato,C3_Incertidumbre,Total_Entrada,Observacion
0,Linea base (zero-shot),Entrada 1,2,1,2,5,Respuesta clara pero en formato libre con viñetas.
0,Linea base (zero-shot),Entrada 2,1,0,0,1,Inventó vector de phishing e IP de origen (alucinación).
0,Linea base (zero-shot),Entrada 3,1,0,0,1,Ignoró el conflicto de seguridad entre bloqueo total y BYOD.
1,Asignacion de Rol,Entrada 1,2,1,2,5,Vocabulario técnico de SOC pero mantiene formato libre.
1,Asignacion de Rol,Entrada 2,1,0,0,1,Mantiene alucinación de datos pese al tono profesional.
1,Asignacion de Rol,Entrada 3,1,0,0,1,Vocabulario más técnico sin resolver la contradicción.
2,Rol + Contexto,Entrada 1,2,1,2,5,Clasificó correctamente en categorías cerradas (Acceso no autorizado / Alta).
2,Rol + Contexto,Entrada 2,2,1,0,3,C1 sube al usar categorías cerradas pero C3 falla sin marcar vacíos.
2,Rol + Contexto,Entrada 3,2,1,1,4,Identificó categoría (Otro / Media) con mejor marco conceptual.
3,Rol + Contexto + Formato,Entrada 1,2,2,2,6,Cumplimiento perfecto de la tabla Markdown requerida.
3,Rol + Contexto + Formato,Entrada 2,2,2,2,6,C2 y C3 máximos al forzar NO ESPECIFICADO sin inventar datos.
3,Rol + Contexto + Formato,Entrada 3,2,2,2,6,Identificó las contradicciones en la fila de información faltante.
4,Few-Shot (Ejemplos),Entrada 1,2,2,2,6,Estabilidad de formato y vocabulario consistente con el ejemplo.
4,Few-Shot (Ejemplos),Entrada 2,2,2,2,6,Clasificación precisa de activos sin copiar datos falsos del ejemplo.
4,Few-Shot (Ejemplos),Entrada 3,2,2,2,6,Estructura impecable y manejo de la contradicción sin sesgos.
5,Cadena de Razonamiento (CoT),Entrada 1,2,2,2,6,Desglose de viñetas de análisis previo antes de la matriz.
5,Cadena de Razonamiento (CoT),Entrada 2,2,2,2,6,Separación transparente de lo conocido vs lo indeterminado.
5,Cadena de Razonamiento (CoT),Entrada 3,2,2,2,6,Evidencia el conflicto técnico en viñetas previo a la tabla.