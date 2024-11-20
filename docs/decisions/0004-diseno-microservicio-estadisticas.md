[back](/docs/decisions/home.md)
# Diseño microservicio de estadisticas

## Contexto y problema
El microservicio de estadísticas debe recolectar y procesar información en tiempo real sobre el estado de los pedidos, la situación de los camiones y los datos de clientes. El desafío principal radica en garantizar que los datos se procesen en tiempo real sin afectar el rendimiento del sistema general.

## Opciones consideradas
- Pipeline de procesamiento en tiempo real
- Consultas en tiempo real desde la base de datos
- Procesamiento por lotes
    - No cumple con el requisito de ser en tiempo real.

## Opcion elegida
Opción elegida: "Pipeline de procesamiento en tiempo real". Se selecciona esta opción debido a su flexibilidad, escalabilidad y capacidad para cumplir con el procesamiento continuo de eventos sin impactar directamente la operación de las bases de datos de origen.

![image](/docs/resources/estadisticas.png)

### Consecuencias
- Buena, desacoplamiento entre los productores de datos (otros microservicios) y el consumidor (Estadísticas).
- Mala, mayor complejidad inicial en la implementación por la necesidad de recoleccion de datos y procesamiento continuo.
- Mala, requiere monitoreo y manejo de fallos en el pipeline de datos para evitar pérdida de eventos.

## Casos de uso afectados
- UC-5
