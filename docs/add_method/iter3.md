[back](/docs/add_method/home.md)
# Iteración 3

## Descripcion
Esta iteración se enfoca en diseñar el microservicio de estadísticas. Este microservicio debe recolectar, procesar y servir información en tiempo real sobre el estado de los pedidos, la situación de los camiones y datos de clientes.  
El principal desafío es garantizar un procesamiento eficiente sin afectar el rendimiento general del sistema y cumplir con los atributos de calidad definidos.

## Drivers
- Proposito del diseño
    - Proveer un servicio eficiente y escalable para el procesamiento en tiempo real de estadísticas, garantizando un flujo constante de datos actualizados.
- [Requerimientos funcionales](/docs/requerimientos-funcionales.md)
    - UC-5
- [Atributos de calidad](/docs/atributos-de-calidad.md)
    - QA-Per-1
    - QA-Per-2
    - QA-Dis-1
- Consideraciones de la arquitectura
    - Diseñar una arquitectura basada en eventos para garantizar un procesamiento en tiempo real.
    - Utilizar un modelo desacoplado para facilitar escalabilidad y mantenibilidad.
    - Implementar tolerancia a fallos en la ingesta y procesamiento de datos.
    - Incorporar caching para mejorar tiempos de consulta.

## Objetivos

- Proveer una arquitectura modular y extensible.

- Garantizar la interoperabilidad con microservicios como Pedidos, Reparto y Rutas, y Clientes, usando mensajería basada en eventos.

- Proveer una arquitectura modular que permita agregar nuevos tipos de estadísticas o adaptarse a cambios en las fuentes de datos sin interrumpir el servicio.

## Elementos elegidos para refinar

En esta iteración se decide atacar el microservicio de estadísticas, logrando que el mismo funcione de manera confiable. Se trabajará con la integración de otros microservicios semi-criticos como lo son "Reparto y rutas" y "Pedidos".

## Opciones a considerar/conceptos de diseño considerados
| Opción | Pros | Cons |
|---|---|---|
| Base de datos NoSQL como MongoDB para datos en tiempo real | Buen desempeño para lecturas y escrituras intensivas | Sobrecarga de administración en comparación con bases de datos completamente gestionadas |
|Uso de Apache Kafka para manejo de eventos| Altamente escalable y confiable para manejar grandes volúmenes de datos | Mayor complejidad operativa |

## Instanciacion de elementos
- Ingestor de datos
    - Captura eventos desde microservicios fuente (Pedidos, Rutas, Clientes) utilizando, por ejemplo, Kafka.

- Procesador en tiempo real
    - Consume eventos desde el ingestor de datos y aplica cálculos de estadísticas en tiempo real.

- Base de datos de estadísticas
    - MongoDB para almacenar datos en tiempo real.

- API RESTful
    - Permite a los clientes consultar estadísticas preprocesadas y en tiempo real.

## Decisiones tomadas
- Se utilizará una base de datos NoSQL debido a su capacidad para manejar altas tasas de escritura.
- Se implementará una API utilizando REST, para las consultas de los clientes.

## Artefactos generados

### ADR generado
- [ 0004-diseno-microservicio-estadisticas ](/docs/decisions/0004-diseno-microservicio-estadisticas.md)


### Diagrama/sketch del resultado
![image](/docs/resources/estadisticas.png)
