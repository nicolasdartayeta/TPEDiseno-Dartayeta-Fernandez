## Integracion de MercadoPago

## Contexto y problema

Especificar el microservicio de pagos para gestionar la integración con una pasarela de pagos, que valide las transacciones y gestione la seguridad de los pagos.

## Opciones consideradas

- Usar la pasarela de pagos de MercadoPago.
- Usar la pasarela de pagos de Modo.

## Opcion elegida

Opcion elegida: "Usar la pasarela de pagos de MercadoPago". Se eligio esta opcion por la facilidad a la hora de integrarla con el microservicio de pagos. El servicio cuenta con buena documentacion y los desarrolladores estan familirizados con ella.

![image](/docs/resources/pagos.png)

### Consecuencias

- Buena, el desarrollo del microservicios de pagos se simplifica.
- Buena, es posible aplicar lógica propia antes de enviar la request a MercadoPago.
- Buena, se delega la lógica complicada de procesar el pago a MercadoPago.
- Mala, se depende de un servicio de terceros para procesar los pagos.

## Atributos de calidad satisfechos
- QA-Seg-1
- QA-Int-1
- QA-Mod-2