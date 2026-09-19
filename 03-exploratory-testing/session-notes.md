# Sesión 1

## Charter
Explorar las funcionalidades de inicio de sesión, registro de nuevo usuario y edición de perfil para identificar fallos en la validación de datos, errores en la sesión del usuario o comportamientos inconsistentes en la persistencia de datos personales.

## ÁREAS
JPetStore Demo (OctoPerf) — Entorno Web / Navegador Chrome.
URL base: https://petstore.octoperf.com/actions/Catalog.action

## INICIO
19 de Septiembre de 2026 — 10:00 AM (Duración estimada: 45 min)

## TESTER
QA Tester

## DESGLOSE DE TAREAS
- Diseño / Planificación de pruebas: 15%
- Ejecución y Exploración: 65%
- Reporte y Documentación: 20%

## ARCHIVOS DE DATOS
- Datos de prueba para registro:
  - Usuario: `qa_tester_99`
  - Password: `Password123!`
  - Nombres/Apellidos con caracteres especiales: `José Á. Ñandú`
  - Correo electrónico inválido: `correo_invalido_sin_at.com`
  - Teléfono con letras: `abc-123-xyz`

## NOTAS DE PRUEBA
- Se ingresó a la página principal y se navegó al enlace **"Sign In"**.
- Se intentó iniciar sesión con credenciales por defecto (`j2ee` / `j2ee`), el acceso fue exitoso y el nombre del usuario se desplegó en pantalla.
- Se cerró sesión (Log Out) y se procedió a la opción **"Register Now!"** para crear una nueva cuenta.
- Se completó el formulario de registro utilizando caracteres especiales en los campos de nombre y apellido (`José Á. Ñandú`). El sistema permitió el registro sin arrojar alertas ni errores de codificación (UTF-8).
- Se probó la validación del campo de correo electrónico ingresando una cadena sin formato válido (`correo_invalido_sin_at.com`). El sistema aceptó el registro sin validar la estructura del email.
- Se verificó la modificación de información de cuenta en la sección "My Account" actualizando la dirección de envío; los datos se guardaron correctamente.

## LISTA DE RIESGOS
- **Falta de validación de entradas (Input Sanitization):** La ausencia de validación en campos como email o teléfono permite ingresar datos corruptos o potencialmente maliciosos en la base de datos.
- **Sesiones concurrentes / Manejo de caché:** Si el usuario presiona el botón "Atrás" del navegador después de hacer "Log Out", las páginas de la cuenta siguen visibles en caché.

## DEFECTOS (BUGS)
1. **[BUG-01] Falta de validación en el formato de correo electrónico:**
   - *Pasos para reproducir:* Ir a "Register Now", ingresar `testemail` en el campo Email y guardar.
   - *Resultado esperado:* El sistema debe mostrar un mensaje de error indicando que el formato de correo es inválido.
   - *Resultado obtenido:* El registro se completa con éxito sin validar el símbolo `@` ni el dominio.

## INCIDENTES (ISSUES)
1. **Mensajes de confirmación ambiguos:** Al actualizar la información de la cuenta en "My Account", el sistema no despliega una notificación visible (p. ej., "Datos actualizados con éxito"), lo que puede generar duda en el usuario sobre si el cambio se procesó.