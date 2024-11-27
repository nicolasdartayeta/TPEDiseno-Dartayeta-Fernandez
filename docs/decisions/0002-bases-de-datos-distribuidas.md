[back](/docs/decisions/home.md)
# Bases de datos distribuidas

## Contexto y problema
Algunos microservicios requieren persistencia de datos. Es necesario definir cómo cada microservicio almacenará sus datos de manera independiente y desacoplada, manteniendo el principio de separación de responsabilidades. Esto incluye asegurar que cada microservicio tenga acceso a sus propios datos, evitando dependencias directas entre ellos, lo que a su vez facilita la escalabilidad y el mantenimiento. Sin embargo, esta decisión introduce desafíos relacionados con la consistencia de los datos y la complejidad de la gestión de múltiples bases.

## Opciones consideradas

- *Base de datos centralizada*: Un enfoque en el que todos los microservicios comparten una única base de datos. Aunque simplifica la gestión de datos y reduce la posibilidad de inconsistencias, este diseño genera un acoplamiento fuerte entre microservicios, limita la escalabilidad horizontal y crea un único punto de fallo en la arquitectura.

- *Bases de datos distribuidas*: Cada microservicio tiene su propia base de datos, lo que garantiza independencia total y permite la selección de tecnologías adecuadas para cada caso. Sin embargo, este enfoque requiere un mayor esfuerzo en la gestión de transacciones distribuidas y puede introducir posibles inconsistencias si no se implementa adecuadamente.

## Opcion elegida
La opto por el uso de bases de datos distribuidas. Este enfoque garantiza que cada microservicio cuente con su propia base de datos, asegurando su independencia. Además, permite seleccionar tecnologías específicas según los requisitos funcionales y no funcionales de cada microservicio.

- Clientes: PostgreSQL: Base de datos relacional que soporta consultas complejas y garantiza consistencia.

- Pedidos: MongoDB: Base de datos NoSQL que permite almacenar datos no estructurados, ideal para el modelo dinámico de pedidos.

- Repartos y rutas: MongoDB: Adecuada para datos geoespaciales y optimización de rutas.

- Pagos: PostgreSQL: Garantiza la integridad y consistencia necesarias para transacciones financieras.

- Incidencias: MongoDB: Flexibilidad en el manejo de datos no estructurados y de resolución rápida.

![image](/docs/resources/bases-de-datos.png)

### Consecuencias

- Buena, independencia entre servicios. Cada microservicio opera con autonomía, permitiendo su desarrollo, despliegue y mantenimiento de manera aislada del resto.

- Buena, escalabilidad horizontal. Las bases de datos distribuidas permiten escalar microservicios de manera individual, adaptándose a demandas específicas.
- Buena, libertad de elección tecnológica. Se puede seleccionar la tecnología de base de datos más adecuada para cada microservicio, optimizando su rendimiento según el caso de uso.
- Mala, complejidad en transacciones distribuidas. La coordinación de transacciones que involucren múltiples bases de datos requiere soluciones complejas.
- Mala, mayor overhead de infraestructura. La gestión de múltiples bases de datos incrementa la carga operativa, incluyendo tareas como respaldo, monitoreo y configuración.
- Mala, posible inconsistencia entre microservicios. Sin una estrategia adecuada, los datos entre microservicios podrían quedar desincronizados, especialmente en operaciones que involucren múltiples servicios.

## Atributos de calidad afectados
- QA-Dis-1