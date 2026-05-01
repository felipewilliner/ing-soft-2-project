Caso de Prueba TP-004
ID: TP-004
TÍTULO: Validación de campos obligatorios - Datos personales incompletos
PRIORIDAD: Alta
TESTER: Lead QA
FECHA EJECUCIÓN:
RESULTADO: PENDIENTE

DESCRIPCIÓN: Verificar que si la persona no existe en el sistema, todos los campos del apartado datos personales son obligatorios y se impide el guardado con mensajes específicos.

PRECONDICIONES:

Persona NO existe.

PASOS DE EJECUCIÓN:
[1] - PASO: Seleccionar DNI, dejar número documento vacío | DATO UTILIZADO: "" | RESULTADO ESPERADO: Al guardar, error: "Número de documento es obligatorio".
[2] - PASO: Completar solo número documento | DATO UTILIZADO: "11111111" | RESULTADO ESPERADO: Error: "Nombre es obligatorio".
[3] - PASO: Completar nombre, apellido, fecha, sexo, pero no CUIT | DATO UTILIZADO: Faltante CUIT | RESULTADO ESPERADO: Error: "CUIT es obligatorio para tipo DNI".
[4] - PASO: Completar todos excepto calle del domicilio | DATO UTILIZADO: Calle vacía | RESULTADO ESPERADO: Error: "Calle es obligatorio".

RESULTADO REAL:
OBSERVACIONES: