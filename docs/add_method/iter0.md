# Iteración 0

## Descripcion
En esta iteración se define la arquitectura general del sistema y las tecnologías clave para su implementación. Al tratarse de un sistema brownfield, es necesario adaptar la solución a las restricciones y características existentes, asegurando compatibilidad con el entorno actual mientras se traza un camino hacia una arquitectura moderna y escalable.

## Drivers seleccionados
- Sistema brownfield
    - El sistema actual debe ser migrado o adaptado sin interrumpir las operaciones existentes, lo que limita algunas decisiones tecnológicas y requiere una integración progresiva.
- [Restricciones](/docs/restricciones.md)
    - Res-1
    - Res-2

## Objetivos
- Diseñar el sistema con un enfoque modular que permita identificar y dividir los microservicios a implementar.
- Seleccionar tecnologías que soporten el desarrollo, la integración continua y la fácil adaptabilidad de los microservicios considerando restricciones.

## Elementos elegidos para refinar
Dado que esta es la iteración inicial, no se está refinando un componente específico. En cambio, se están definiendo los principios arquitectónicos generales y los elementos básicos necesarios para la implementación futura del sistema.

## Opciones a considerar/conceptos de diseño considerados
En cuanto a la arquitectura no se consideran más opciones que la de microservicios dada la restricción impuesta.

En cuanto a las tecnologias que facilitan el desarrollo de dichos microservicios, se plantea el uso de virtualizacion/contenerización.

| Opción | Pros | Cons |
| --- | --- | --- |
| Maquinas virtuales | Mayor aislamiento, madurez tecnologica | Mayor consumo de recursos, arranque lento, menos portable |
| Docker | Ligero, rapido, portable | Menor aislamiento, complejo de orquestar |

## Instanciacion de elementos
Cada modulo del sistema monolítico será implementado en un microservicio. 

- Modulo clientes → Microservicio de clientes
- Modulo pedidos → Microservicio de pedidos
- Modulo reparto y rutas → Microservicio de repartos y rutas
- Modulo estadísticas → Microservicio de estadísticas
- Modulo incidencias → Microservicio de incidencias
- Modulo pagos → Microservicio de pagos

## Decisiones tomadas
Se decidió que la arquitectura del sistema sea de microservicios, planteando a su vez cuales serán estos mismos.  
Adicionalmente, se eligió el uso de contenedores Docker como tecnología base para implementar y desplegar los microservicios. Esta decisión responde a la necesidad de portabilidad, despliegue rápido y compatibilidad con múltiples entornos.

## Artefactos generados

### ADRs generados
- [ 0000-uso-de-microservicios ](/docs/decisions/0000-uso-de-microservicios%20.md): Detalla los motivos y consecuencias de adoptar la arquitectura de microservicios.
- [ 0001-uso-de-docker ](/docs/decisions/0001-uso-de-docker.md): Explica la selección de Docker como tecnología de contenedores para el sistema.

### Diagrama/sketch del resultado
El siguiente diagrama ilustra los diferentes microservicios propuestos:

![image](/docs/resources/microservicios.png)