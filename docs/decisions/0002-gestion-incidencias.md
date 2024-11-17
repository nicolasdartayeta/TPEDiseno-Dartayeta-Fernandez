# Gestión de incidencias

## Contexto y problema

Se propone acoplar "Incidencias" al microservicio de "Reparto y rutas", dada su estrecha relacion con la gestión de las rutas y flotas de transporte. 

## Opciones consideradas

* Acoplar Incidencias al microservicio de Reparto y rutas.
* Mantener Incidencias como un microservicio independiente.
* Fusionar Incidencias y Pedidos en un microservicio.

## Opcion elegida

Opcion elegida: "Acoplar Incidencias al microservicio de Reparto y rutas", ya que este enfoque centraliza la lógica en un solo servicio, reduciendo la complejidad de la arquitectura general.

### Consecuencias

* Buena, se simplifica la comunicación entre "Incidencias" y "Reparto y rutas", dado que estan en un mismo microservicio.
* Mala, se incrementa la carga en el microservicio Reparto y rutas, lo que podría requerir menor capacidad de escalabilidad.
* Buena, facilita la implementación de estrategias de respuesta a problemas, como redirigir rutas en caso de incidencias críticas.

## Atributos de calidad satisfechos
* interoperabilidad (comunicacion eficiente dentro del modulo) 