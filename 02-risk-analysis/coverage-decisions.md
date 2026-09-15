# Coverage Decisions 

## Riesgos que se probarán primero 
1. Falta de integración o inconsistencia entre la Web y la API: 
Dado que no existe confirmación de que ambos sistemas estén sincronizados, cambios realizados en la API (ej. actualizar stock con POST /pet o procesar una orden con POST /store/order) podrían no reflejarse en la aplicación Web (JPetStore) o viceversa, afectando la experiencia de compra real.

2. Fallos en el flujo de Checkout y Registro de Usuarios:
 Problemas al procesar un pedido o al registrar un usuario nuevo vía "Register Now" en la Web afectan directamente la venta, impidiendo la conversión de clientes y la generación de ingresos para el negocio.

3. Vulnerabilidades de seguridad por falta de autenticación en la API: 
La API pública no requiere autenticación obligatoria para operaciones críticas (como DELETE /pet/{id} o POST /pet), lo que representa un riesgo alto de manipulación o borrado accidental/malicioso de datos de inventario.

## ¿Por qué esos riesgos son prioridad? 
Se atenderán primero porque impactan de manera directa las dos áreas más críticas de un e-commerce: la facturación/ventas y la integridad de los datos de negocio. Si el flujo de compra falla o el inventario no se actualiza correctamente entre sistemas, la empresa pierde dinero de inmediato y la confianza del usuario. Asimismo, la falta de autenticación en la API expone al sistema a fallos catastróficos de seguridad y pérdida de información operativa.

## Qué se probará menos o quedará fuera por ahora - [Exclusión 1] - [Exclusión 2] - [Exclusión 3] 
1. Pruebas avanzadas de carga/estrés en la API Swagger: 
Dado que es un entorno público de demo y pruebas, no es prioritario simular altos volúmenes de concurrencia.

2. Diseño responsive y compatibilidad en múltiples navegadores/dispositivos (Cross-browser testing): 
La interfaz visual secundaria o problemas estéticos menores quedan en segundo plano frente al correcto funcionamiento funcional de las transacciones.

3. Validación de endpoints secundarios o no críticos de la API: 
Funcionalidades de menor impacto que no afectan directamente al flujo principal de ventas (como consultar estados de inventario secundarios o datos opcionales de usuarios).

## Justificación de exclusiones 
Estas exclusiones son razonables porque en una etapa inicial de evaluación de calidad, el esfuerzo de QA debe centrarse en la estabilidad funcional y de datos de los flujos principales (compra e inventario). Probar aspectos no funcionales como la compatibilidad de navegadores o realizar pruebas exhaustivas de carga en un entorno de demo no aportaría valor inmediato al negocio si los flujos básicos de transacción aún no están validados y asegurados.