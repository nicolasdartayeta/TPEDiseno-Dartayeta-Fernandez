[back](/docs/decisions/home.md)
# Diseño microservicio de estadisticas

## Contexto y problema
El microservicio de estadísticas requiere un diseño que sea eficiente y escalable, mientras mantiene la interoperabilidad con los microservicios existentes y una arquitectura modular que facilite futuros cambios o expansiones.

## Opciones consideradas
- Pipeline de procesamiento en tiempo real
    - Consiste en el uso de herramientas como Apache Kafka para manejar la ingesta, procesamiento y distribución de estadísticas en tiempo real.
- Consultas en tiempo real desde la base de datos
    - Basado en realizar consultas directamente a una base de datos central que almacena los datos actualizados de otros microservicios.
- Procesamiento por lotes
    - Estadísticas generadas mediante procesamiento periódico en lotes. Esta opción no cumple con el requisito de tiepo real impuesto.


## Opcion elegida
La opción elegida fue utilizar un pipeline con procesamiento en tiempo real. Esta opción fue seleccionada por su capacidad para manejar eventos de forma escalable, cumpliendo con los requisitos de procesamiento en tiempo real y desacoplando efectivamente el microservicio de estadísticas de las fuentes de datos. Este enfoque asegura que las estadísticas estén actualizadas y disponibles sin impactar la operación de los sistemas fuente.

![image](/docs/resources/estadisticas.png)

### Consecuencias

- Buena, el uso de una arquitectura basada en eventos permite separar claramente los microservicios productores (Pedidos, Rutas y Clientes) del consumidor (Estadísticas), mejorando la escalabilidad y mantenibilidad del sistema.

- Buena, la naturaleza distribuida del pipeline de procesamiento en tiempo real permite manejar incrementos significativos en la cantidad de eventos sin afectar el rendimiento global.

- Mala, se requiere la necesidad de monitoreo constante, incrementan la complejidad operativa en comparación con otras opciones.

- Mala, requiere mecanismos robustos para gestionar errores en el pipeline, como pérdida de eventos o fallos en nodos de procesamiento, lo que añade una capa adicional de dificultad al diseño.

## Casos de uso afectados

- UC-5
