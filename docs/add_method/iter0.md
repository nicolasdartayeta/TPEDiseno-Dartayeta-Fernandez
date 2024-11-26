# Iteración 0

## Descripcion
En esta iteración se decide la arquitectura del sistema y la tecnologia a usar para implementarla. 

## Drivers seleccionados
- Sistema brownfield
- [Restricciones](/docs/restricciones.md)
    - Res-1
    - Res-2

## Objetivos
- Diseñar el sistema al nivel de los microservicios a implementar.
- Considerar tecnologias que faciliten la implementacion de los microservicios.

## Elementos elegidos para refinar
Al ser una iteracion inicial, no se está refinando un componente en particular sino planteando la arquitectura del sistema.

## Opciones a considerar/conceptos de diseño considerados
En cuanto a la arquitectura no se consideran más opciones que la de microservicios dada la restricción impuesta.

En cuanto a las tecnologias que facilitan el desarrollo de dichos microservicios, se plantea el uso de virtualizacion/contenerización.

| Opción | Pros | Cons |
| --- | --- | --- |
| Maquinas virtuales | Mayor aislamiento, madurez tecnologica | Consumo de recursos, arranque lento |
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
Tambien se decidió usar la tecnologia de contenedores, desarrollando cada microservicio en un contenedor distinto.

## Artefactos generados

### ADRs generados
- [ 0000-uso-de-microservicios ](/docs/decisions/0000-uso-de-microservicios%20.md)
- [ 0001-uso-de-docker ](/docs/decisions/0001-uso-de-docker.md)

### Diagrama/sketch del resultado
![image](/docs/resources/microservicios.png)