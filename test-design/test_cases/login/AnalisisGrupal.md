Análisis de los resultados generados por la IA:

La primera parte de detección de ambiguedades es excelente. Identifica problemas reales, como condiciones incompletas, y explica muy bien por que esto genera confusión.
Sin embargo, los Casos de Prueba generados presentan varios problemas de redacción y estructura:

El TP-001 detalla la carga campo por campo, pero los TP-002 y TP-003 agrupan acciones de forma muy genérica ("completar domicilio completo" o "datos válidos"). Un tester que no conoce el sistema no sabría qué datos exactos ingresar.

El TP-003 indica buscar "en alguna sección de resumen o edición". Un caso de prueba debe indicar exactamente dónde hacer clic, sin dejar lugar a la interpretación.

El TP-004 intenta probar todos los mensajes de error en un solo recorrido secuencial, ignorando que el sistema probablemente bloquee el avance desde el primer error, haciendo imposible ejecutar los pasos siguientes sin reiniciar el formulario.

También nos pareció que la cantidad de casos de prueba que nos mando fue muy breve, siendo que pudo haber hecho casos de prueba para los requerimientos que corrigió previamente.

IA utilizada: DeepSeek
Integrantes: Valentin Griglio, Felipe Williner