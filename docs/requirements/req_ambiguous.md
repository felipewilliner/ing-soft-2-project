1. Fragmento exacto:
"si esa persona ya existe dada de alta en el sistema (no necesariamente como beneficiario), los campos se deben autocompletar (exceptuando el porcentaje de beneficio) y se deben bloquear los campos para no permitir la edición de los mismos."
•	Categoría de riesgo: Sujetos tácitos / Condicionales sin else definido.
•	Interpretación opuesta:
o	Desarrollador: Solo se bloquean los campos de datos personales ya cargados (nombre, apellido, fecha nacimiento, etc.). Los campos de domicilio o contacto, si existen en otra parte del sistema, también se bloquean.
o	Tester: No se especifica si los campos de domicilio (calle, número, CP, localidad, provincia, país) también se autocompletan y bloquean, o si se consideran parte del "apartado datos personales". Además, no se define qué ocurre si la persona existe pero tiene datos incompletos en el sistema (ej. falta sexo).
•	Redacción sugerida (con criterios de aceptación):
Dado un tipo y número de documento, si existe una persona activa en el sistema (tabla Personas, independientemente de su rol), entonces:
o	Se autocompletarán los siguientes campos (solo lectura, no editables): nombre, apellido, fecha de nacimiento, sexo, tipo y número de documento.
o	Los campos de domicilio (calle, número, código postal, localidad, provincia, país) NO se autocompletan automáticamente, y permanecen editables, a menos que la persona tenga un domicilio cargado previamente en el sistema → en ese caso se autocompleta y se bloquea.
o	El campo porcentaje de beneficio se carga vacío y editable.
o	Si la persona existe pero el sistema no tiene registrado un valor obligatorio para alguno de esos campos (ej. sexo), se deberá mostrar un mensaje indicando "Datos incompletos de la persona, complete manualmente" y permitir la edición de dicho campo.
________________________________________
2. Fragmento exacto:
"El campo cuit se debe autogenerar contemplando los campos: tipo documento, número documento y sexo. Este campo se autogenera solo en caso de que el tipo documento sea DNI, caso contrario el campo deja de ser obligatorio."
•	Categoría de riesgo: Límites difusos / Algoritmo no especificado.
•	Interpretación opuesta:
o	Desarrollador: Usa una fórmula genérica de CUIT (XX-XXXXXXXX-X) donde los primeros dos dígitos dependen del sexo (20=mujer, 23=hombre, 27=empresa, etc.) y el resto es número de DNI con ceros a la izquierda. Si no hay sexo, asigna 30 por defecto.
o	Tester: No se define qué pasa si el número de DNI tiene menos de 8 dígitos (ej. 123456 → ¿00123456?). Tampoco se especifica qué dígito verificador usar (algoritmo módulo 11, con restricciones ANSES/SICAM). Si el sexo es "otro" o "no binario", ¿qué prefijo se usa?
•	Redacción sugerida:
Si tipo documento = DNI, entonces el campo CUIT es obligatorio y se genera automáticamente según:
o	*Prefijo: "20" si sexo = "femenino", "23" si sexo = "masculino", "27" si sexo = "otro" o no informado.*
o	Número: se toma número de DNI con ceros a la izquierda hasta completar 8 dígitos.
o	Dígito verificador: se calcula con algoritmo módulo 11 estándar para CUIT (base 10, serie 5,4,3,2,7,6,5,4,3,2).
o	Formato final: XX-XXXXXXXX-X.
o	Si el CUIT generado es inválido según la ANSES (ej. por repetición), se debe mostrar un error y permitir corrección manual.
o	Si tipo documento ≠ DNI, el campo CUIT no es obligatorio, se deshabilita su autogeneración y queda opcional.
________________________________________
3. Fragmento exacto:
"El porcentaje de beneficio no debe ser 0"
"El porcentaje de beneficio siempre debe ser 100%, en caso de ya existir uno o más beneficiarios cargados, se debe habilitar la edición del porcentaje de esos beneficiarios, para que la suma de todos de 100%"
•	Categoría de riesgo: Regla contradictoria / Condicional sin else.
•	Interpretación opuesta:
o	Desarrollador: Al crear el primer beneficiario, el porcentaje se fija en 100% y no se puede editar. Al agregar un segundo beneficiario, el primero se desbloquea para cambiarlo (ej. 50% y 50%). Si edito el segundo a 30%, el primero se ajusta automáticamente a 70% o debo validar suma al guardar.
o	Tester: No se especifica si el sistema debe reasignar porcentajes automáticamente o solo validar en guardado. Tampoco se dice qué pasa si hay 3 beneficiarios y se intenta guardar con suma ≠ 100%. ¿Se rechaza o se fuerza ajuste? ¿Se permite 0% en algún caso intermedio?
•	Redacción sugerida:
*- Validación en guardado: la suma de los porcentajes de beneficio de todos los beneficiarios de la misma persona titular debe ser exactamente 100%.*
*- Si es el primer beneficiario, el porcentaje se establece en 100% y no es editable.*
- Si ya existe al menos un beneficiario, entonces:
o	todos los porcentajes son editables.
o	Al guardar, si la suma total ≠ 100%, se muestra el error: "La suma de porcentajes debe ser 100%. Actual: X%".
o	No se permite guardar hasta que la suma sea 100%.
o	*No se permite un porcentaje individual = 0% en ningún momento (validación en cada input).*
________________________________________
4. Fragmento exacto:
"Los campos calles, número, código postal, localidad, provincia y país son OBLIGATORIOS"
•	Categoría de riesgo: Métricas subjetivas / Formato no definido.
•	Interpretación opuesta:
o	Desarrollador: "Número" puede ser "S/N" o letras como "BIS". "Código postal" puede ser argentino de 4 dígitos o extranjero alfanumérico. "Provincia" puede ser selección de lista fija o texto libre.
o	Tester: ¿Qué pasa si localidad no coincide con código postal? ¿Se valida? ¿Se permite "calle" vacía si número y otros están completos? ¿Provincia extranjera se escribe igual que país?
•	Redacción sugerida:
- Los siguientes campos son obligatorios y no pueden estar vacíos ni contener solo espacios: calle, número, código postal, localidad, provincia, país.
- Formato mínimo:
o	calle: texto libre, máximo 100 caracteres.
o	*número: alfanumérico (ej. 123, 1234, 12A, S/N).*
o	código postal: hasta 10 caracteres alfanuméricos.
o	localidad, provincia, país: texto libre, máximo 50 caracteres cada uno.
- No se validará correspondencia entre CP y localidad por omisión, pero se debe permitir configuración futura de validación por tabla externa.
- Si país ≠ Argentina, provincia y CP no se validan contra padrón local.
________________________________________
5. Fragmento exacto:
"Al hacer click en guardar, se deben validar todos los campos, en caso de que alguno sea incorrecto se debe mostrar un mensaje de error y no permitir el alta."
•	Categoría de riesgo: Voz pasiva que oculta responsable / Mensaje genérico.
•	Interpretación opuesta:
o	Desarrollador: Muestra un único mensaje genérico "Error en los datos". Valida solo los campos obligatorios, no formatos ni reglas de negocio.
o	Tester: No se especifica si se debe indicar QUÉ campo falló, ni si se deben validar todos los errores a la vez o detenerse en el primero.
•	Redacción sugerida:
- Al hacer clic en "Guardar", el sistema ejecutará las siguientes validaciones antes de enviar los datos al servidor (validación en frontend) y nuevamente en backend:
o	Campos obligatorios no vacíos.
o	Formato de CUIT (si aplica).
o	*Porcentaje de beneficio ≠ 0 y suma total = 100%.*
o	Existencia de la persona (si aplica autocompletado).
- Si una o más validaciones fallan:
o	Se mostrará un mensaje de error específico por cada campo inválido, ubicado junto al campo o en un listado superior.
o	Ejemplo de mensaje: "CUIT: formato inválido. Debe ser XX-XXXXXXXX-X".
o	No se permitirá el alta hasta que todos los campos sean válidos.
*- Si todas las validaciones son correctas, se procede al alta.
________________________________________
6. Fragmento exacto:
"mostrar un mensaje de alta exitosa y mostrar la pantalla de beneficiario con todos los beneficiarios cargados"
•	Categoría de riesgo: Sujetos tácitos / Acción no atómica.
•	Interpretación opuesta:
o	Desarrollador: Muestra un toast o alert "Éxito", luego redirige al listado de beneficiarios. El nuevo beneficiario ya aparece.
o	Tester: No se especifica si se debe mantener en la misma pantalla de carga o redirigir. Tampoco se aclara si se debe mostrar un resumen del beneficiario recién creado.
•	Redacción sugerida:
- Tras un guardado exitoso:
o	Se mostrará un mensaje flotante (snackbar/toast) con el texto "Beneficiario agregado correctamente".
o	El sistema redirigirá automáticamente a la pantalla "Listado de beneficiarios" (ruta /beneficiarios).
o	En esa pantalla se mostrarán todos los beneficiarios activos, incluyendo el recién creado, ordenados por fecha de alta descendente.
o	No se requiere confirmación adicional del usuario para continuar.
