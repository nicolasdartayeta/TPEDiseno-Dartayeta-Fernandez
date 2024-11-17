## Integracion de MercadoPago

## Contexto y problema

Implementar un microservicio específico para gestionar la integración con la pasarela de pago de MercadoPago, que valide las transacciones y gestione la seguridad de los pagos.

## Opciones consideradas

* Integrar la gestión de pagos dentro del microservicio de "Pedidos".
* Crear un microservicio dedicado a la gestión de pagos.

## Opcion elegida

Opcion elegida: "Crear un microservicio dedicado a la gestión de pagos", dada la posibilidad de gestionar la seguridad y monitoreo de las transacciones de manera especifica e individual al microservicio.

### Consecuencias

* Buena, mejora en la seguridad al mantener la validación de pagos y las transacciones sospechosas en un microservicio aislado.
* Buena, se reduce el riesgo de fraude o errores al centralizar el control de transacciones en un microservicio especializado.
* Mala, empeora la latencia ligeramente debido a la comunicación adicional entre microservicios.

## Atributos de calidad satisfechos
* QA-Seg-1
* QA-Seg-2
* QA-Des-1