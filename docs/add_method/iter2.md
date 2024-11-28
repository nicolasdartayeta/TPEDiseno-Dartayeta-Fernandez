# Iteración 2

## Descripcion
En esta iteración se diseña el microservicio de pagos, asegurando que cumpla con los atributos de calidad definidos: seguridad ante accesos no autorizados, comunicación eficiente con Mercado Pago, y modificabilidad para soportar nuevos métodos de pago.

## Drivers
- Proposito del diseño
    - Diseñar un microservicio que gestione pagos utilizando la pasarela de Mercado Pago, con alta seguridad, eficiencia en la comunicación y flexibilidad para futuras expansiones.

- [Atributos de calidad](/docs/atributos-de-calidad.md)
    - QA-Seg-1
    - QA-Int-1
    - QA-Mod-2
- [Restricciones](/docs/restricciones.md)
    - Res-3
- Consideraciones de la arquitectura
    - El microservicio debe ser modular para permitir cambios o expansiones sin afectar otras partes del sistema.
    
    - La comunicación con Mercado Pago debe ser robusta y manejar fallos de manera adecuada.

## Objetivos

- Diseñar los componentes necesarios para gestionar las transacciones de pago.

- Proveer mecanismos para la detección y bloqueo de accesos no autorizados.

- Garantizar una integración eficiente con la pasarela de Mercado Pago.

- Facilitar la integración futura de nuevos métodos de pago.
## Elementos elegidos para refinar
En esta iteración se refinará el diseño del microservicio de pagos, asegurando que los componentes cumplan con los atributos de calidad definidos. Además, se trabajará en la integración con la pasarela de Mercado Pago y en garantizar que el sistema sea extensible para soportar nuevos métodos de pago en el futuro.

## Opciones a considerar/conceptos de diseño considerados
| Opción | Pros | Cons |
|---|---|---|
| Integración directa con la API de Mercado Pago | Simplicidad inicial, reduce la necesidad de componentes intermedios | Menor flexibilidad para agregar nuevos métodos de pago en el futuro |
| Uso de un adaptador genérico para pasarelas de pago | Permite integrar múltiples pasarelas en el futuro sin grandes cambios en el código | Incrementa la complejidad inicial del diseño |

## Instanciacion de elementos
- PaymentController: Punto de entrada para manejar las solicitudes HTTP relacionadas con pagos.
    - Validar datos de las solicitudes.
    - Delegar la lógica al servicio correspondiente.
    - Retornar respuestas adecuadas al cliente.

- PaymentService: Lógica de negocio para gestionar transacciones y coordinar con otros componentes.
    - Enviar solicitudes a la procesador de pagos para iniciar transacciones.
    - Validar y procesar respuestas del procesador de pagos.
    - Registrar los eventos de la transacción para auditoría.

- PaymentGatewayAdapter: Define una interfaz genérica para interactuar con pasarelas de pago, comenzando con Mercado Pago.

- SecurityModule: Encargado de autenticar, autorizar y registrar intentos de pago no autorizados.
    - Autenticación y autorización de solicitudes entrantes.
    - Registro de eventos sospechosos o no autorizados para auditoría.

- AuditLogger: Sistema de registro de eventos críticos, como intentos de acceso no autorizados y resultados de transacciones.
    - Registrar cada intento de acceso no autorizado, incluyendo detalles del intento.
    - Almacenar eventos críticos de transacciones de pago.
    - Proveer capacidades de consulta para revisiones

## Decisiones tomadas
- Se diseñará un adaptador genérico para pasarelas de pago, facilitando la integración de nuevos métodos de pago en el futuro.

- Se implementará un módulo de seguridad robusto para detectar y bloquear accesos no autorizados, registrando eventos en el sistema de auditoría.

## Artefactos generados

### ADR generado
- [ 0003-diseno-microservicio-de-pagos ](/docs/decisions/0003-diseno-microservicio-de-pagos.md)

### Diagrama/sketch del resultado
![image](/docs/resources/microservicio-pagos.png)