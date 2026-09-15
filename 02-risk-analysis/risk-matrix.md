
# Risk Matrix

| ID | Riesgo | Impacto | Probabilidad | Nivel | Justificación |
|---|---|---|---|---|---|
| R1 | Permitir la venta y procesamiento de órdenes para productos que no tienen stock disponible (`not in stock`). | 4 | 4 | 16 | Reportado en el sistema de bugs. El flujo de checkout permite confirmar compras de productos agotados, lo que genera cobros indebidos, cancelaciones manuales e insatisfacción crítica del cliente. |
| R2 | Pérdida de la información del carrito de compras al cerrar e iniciar sesión o al perder la sesión activa. | 4 | 4 | 16 | Reportado en el sistema de bugs. Obliga al usuario a rearmar su pedido desde cero, interrumpiendo el embudo de conversión y provocando el abandono directo de la compra. |
| R3 | Eliminación o modificación maliciosa/accidental del catálogo de mascotas mediante la API por falta de autenticación en endpoints como `DELETE /pet/{id}`. | 5 | 4 | 20 | La API pública no exige credenciales ni API Keys obligatorias para alterar datos, exponiendo el inventario a pérdidas masivas de información y desajustes con la Web. |
| R4 | Inconsistencia de datos de inventario entre la API y la aplicación Web debido a la falta de sincronización en tiempo real. | 4 | 3 | 12 | Al ser dos sistemas independientes sin integración confirmada, los cambios realizados en la API pueden no verse reflejados en la interfaz Web, mostrando información falsa a los compradores. |
| R5 | Fallos en el registro de nuevos usuarios a través del formulario "Register Now" que impidan la creación de cuentas. | 4 | 3 | 12 | Bloquea la captación de nuevos clientes en la plataforma, impidiéndoles avanzar hacia el proceso de pago y afectando directamente los ingresos del negocio. |