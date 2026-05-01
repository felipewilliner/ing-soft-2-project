Caso de Prueba TP-002
ID: TP-002
TÍTULO: Alta de beneficiario - Persona YA existe en el sistema - Autocompletado y bloqueo de campos
PRIORIDAD: Alta
TESTER: Lead QA
FECHA EJECUCIÓN:
RESULTADO: PENDIENTE

DESCRIPCIÓN: Verificar que al ingresar un documento correspondiente a una persona ya existente en el sistema (no necesariamente beneficiaria), los datos personales se autocompleten y queden bloqueados para edición, permitiendo solo editar porcentaje de beneficio.

PRECONDICIONES:

El sistema tiene una persona activa con DNI 87654321, nombre "María", apellido "Gómez", sexo femenino, fecha nacimiento 10/10/1990.

Dicha persona NO es beneficiaria actualmente.

PASOS DE EJECUCIÓN:
[1] - PASO: Acceder a pantalla de alta de beneficiario | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Formulario vacío.
[2] - PASO: Seleccionar tipo documento | DATO UTILIZADO: "DNI" | RESULTADO ESPERADO: Campo CUIT obligatorio.
[3] - PASO: Ingresar número de documento | DATO UTILIZADO: "87654321" | RESULTADO ESPERADO: Al perder foco, sistema detecta existencia.
[4] - PASO: Verificar autocompletado | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Nombre "María", apellido "Gómez", sexo "femenino", fecha nacimiento "10/10/1990", CUIT "20-87654321-?" se autocompletan.
[5] - PASO: Intentar editar nombre | DATO UTILIZADO: "Mariana" | RESULTADO ESPERADO: Campo no editable (solo lectura).
[6] - PASO: Intentar editar CUIT | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Campo no editable.
[7] - PASO: Verificar campos de domicilio | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Permanecen vacíos y editables (ya que la persona no tenía domicilio cargado).
[8] - PASO: Completar domicilio completo | DATO UTILIZADO: Calle "Libertad", N° 500, CP 1000, Localidad "CABA", Provincia "Buenos Aires", País "Argentina" | RESULTADO ESPERADO: Se completan sin problemas.
[9] - PASO: Ingresar porcentaje beneficio | DATO UTILIZADO: "100" | RESULTADO ESPERADO: Campo editable, acepta valor.
[10] - PASO: Guardar | DATO UTILIZADO: N/A | RESULTADO ESPERADO: Mensaje éxito y redirección.

RESULTADO REAL:
OBSERVACIONES: