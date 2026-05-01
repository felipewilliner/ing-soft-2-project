Caso de Prueba TP-003
ID: TP-003
TÍTULO: Validación de suma de porcentajes al agregar segundo beneficiario
PRIORIDAD: Alta
TESTER: Lead QA
FECHA EJECUCIÓN:
RESULTADO: PENDIENTE

DESCRIPCIÓN: Verificar que al existir ya un beneficiario con 100%, al agregar un segundo beneficiario se pueda editar el porcentaje del primero y que la suma total sea 100% al guardar, rechazando sumas diferentes.

PRECONDICIONES:

El sistema tiene un titular con un beneficiario existente "Carlos" con 100% de beneficio.

El segundo beneficiario "Ana" no existe en el sistema.

PASOS DE EJECUCIÓN:
[1] - PASO: Iniciar alta de nuevo beneficiario para el mismo titular | DATO UTILIZADO: DNI de Ana inexistente | RESULTADO ESPERADO: Formulario limpio.
[2] - PASO: Completar todos los datos personales y domicilio de Ana | DATO UTILIZADO: Válidos | RESULTADO ESPERADO: Datos aceptados.
[3] - PASO: Verificar campo porcentaje de beneficio | DATO UTILIZADO: Se carga vacío o con 0 | RESULTADO ESPERADO: Por defecto vacío (no 100%).
[4] - PASO: Verificar que el beneficiario Carlos ahora tiene su porcentaje editable | DATO UTILIZADO: N/A | RESULTADO ESPERADO: En alguna sección de resumen o edición, el campo % de Carlos se habilita.
[5] - PASO: En la pantalla de edición de beneficiarios, cambiar % de Carlos a 60% | DATO UTILIZADO: "60" | RESULTADO ESPERADO: Se actualiza.
[6] - PASO: Asignar % a Ana | DATO UTILIZADO: "30" | RESULTADO ESPERADO: Se asigna.
[7] - PASO: Guardar cambios | DATO UTILIZADO: Suma = 90% | RESULTADO ESPERADO: Error: "La suma de porcentajes debe ser 100%. Actual: 90%". No se guarda.
[8] - PASO: Ajustar % de Carlos a 70% | DATO UTILIZADO: "70" | RESULTADO ESPERADO: Suma 100%.
[9] - PASO: Guardar | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Mensaje éxito.

RESULTADO REAL:
OBSERVACIONES:

