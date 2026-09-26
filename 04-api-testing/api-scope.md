# API Testing — Alcance 

## API 
Swagger Petstore (https://petstore.swagger.io/)

## Alcance funcional 
Gestión de mascotas (`/pet`).

## Operaciones seleccionadas 

| Método HTTP | Endpoint | Propósito |
|---|---|---|
| POST | `/pet` | Crear/añadir una nueva mascota al sistema. |
| GET | `/pet/{petId}` | Consultar la información de una mascota existente por su ID. |
| PUT | `/pet` | Actualizar la información de una mascota existente. |
| DELETE | `/pet/{petId}` | Eliminar una mascota del registro del sistema. |

## Justificación 
¿Por qué seleccionaste estas operaciones? 

Se seleccionaron estas cuatro operaciones porque representan el ciclo de vida completo de un recurso en una API (operaciones CRUD: Create, Read, Update, Delete). Validar esta secuencia permite asegurar que las funciones principales del negocio operen de manera coherente.

## Condiciones de prueba identificadas 
¿Qué condiciones consideras necesario verificar? 

- Creación exitosa de un registro con datos válidos.
- Búsqueda correcta de un registro existente mediante su ID único.
- Manejo adecuado de errores al consultar un ID que no existe (escenario negativo).
- Actualización correcta de los datos de un registro preexistente.
- Eliminación exitosa de un registro y posterior verificación de su inexistencia.

## Fuera de alcance 
¿Qué operaciones o aspectos no probarás en este ejercicio? 

- Operaciones relacionadas con usuarios (`/user`) y órdenes de compra (`/store`).
- Subida de imágenes para una mascota (`POST /pet/{petId}/uploadImage`).
- Actualización de mascotas mediante datos de formulario (`POST /pet/{petId}`).
- Pruebas de rendimiento, carga o seguridad (autenticación OAuth/API Key).

