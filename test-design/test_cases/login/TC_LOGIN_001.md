Caso de Prueba TP-001
ID: TP-001
TÍTULO: Alta de beneficiario - Persona NO existe en el sistema - Datos completos válidos con DNI
PRIORIDAD: Alta
TESTER: Lead QA
FECHA EJECUCIÓN:
RESULTADO: PENDIENTE

DESCRIPCIÓN: Verificar que se pueda dar de alta un nuevo beneficiario cuando la persona no existe previamente en el sistema, completando todos los datos obligatorios con un tipo de documento DNI y generación automática de CUIT.

PRECONDICIONES:

El sistema no contiene una persona con el mismo tipo y número de documento.

El usuario tiene permisos de alta de beneficiarios.

PASOS DE EJECUCIÓN:
[1] - PASO: Acceder a la pantalla de alta de beneficiario | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Se muestra el formulario de datos personales y domicilio, todos los campos vacíos y editables.
[2] - PASO: Seleccionar tipo de documento | DATO UTILIZADO: "DNI" | RESULTADO ESPERADO: El campo CUIT se vuelve obligatorio (visible o con marcador).
[3] - PASO: Ingresar número de documento | DATO UTILIZADO: "12345678" | RESULTADO ESPERADO: El campo acepta el valor.
[4] - PASO: Completar nombre | DATO UTILIZADO: "Juan" | RESULTADO ESPERADO: Campo acepta el valor.
[5] - PASO: Completar apellido | DATO UTILIZADO: "Pérez" | RESULTADO ESPERADO: Campo acepta el valor.
[6] - PASO: Completar fecha de nacimiento | DATO UTILIZADO: "15/05/1985" | RESULTADO ESPERADO: Campo acepta el valor en formato DD/MM/AAAA.
[7] - PASO: Seleccionar sexo | DATO UTILIZADO: "masculino" | RESULTADO ESPERADO: Se selecciona la opción.
[8] - PASO: Verificar campo CUIT | DATO UTILIZADO: Autogenerado | RESULTADO ESPERADO: Se genera "23-12345678-9" (según algoritmo módulo 11, prefijo 23).
[9] - PASO: Completar calle | DATO UTILIZADO: "Av. Siempre Viva" | RESULTADO ESPERADO: Campo acepta el valor.
[10] - PASO: Completar número | DATO UTILIZADO: "1234" | RESULTADO ESPERADO: Campo acepta el valor.
[11] - PASO: Completar código postal | DATO UTILIZADO: "1406" | RESULTADO ESPERADO: Campo acepta el valor.
[12] - PASO: Completar localidad | DATO UTILIZADO: "CABA" | RESULTADO ESPERADO: Campo acepta el valor.
[13] - PASO: Completar provincia | DATO UTILIZADO: "Buenos Aires" | RESULTADO ESPERADO: Campo acepta el valor.
[14] - PASO: Completar país | DATO UTILIZADO: "Argentina" | RESULTADO ESPERADO: Campo acepta el valor.
[15] - PASO: Ingresar porcentaje de beneficio | DATO UTILIZADO: "100" | RESULTADO ESPERADO: Campo acepta el valor.
[16] - PASO: Hacer clic en guardar | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Se muestra mensaje "Beneficiario agregado correctamente". Redirige a listado de beneficiarios donde aparece Juan Pérez.

RESULTADO REAL:
OBSERVACIONES: