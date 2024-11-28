[back](/docs/add_method/home.md)
# Iteración 1

## Descripcion

## Drivers
- Proposito del diseño
    - Permitir que cada microservicio gestione su propia persistencia de datos, garantizando independencia y escalabilidad, al mismo tiempo que se minimiza el impacto de fallos en un microservicio sobre el resto del sistema.
- [Atributos de calidad](/docs/atributos-de-calidad.md)
    - QA-Dis-1
- Consideraciones de la arquitectura
    - El desacoplamiento de los microservicios implica la posibilidad de utilizar tecnologías de bases de datos distribuidas heterogéneas, lo que conlleva beneficios y desafíos que deben evaluarse cuidadosamente.

## Objetivos

- Lograr que el modelo persistencia de los datos se corresponda con la arquitectura desacoplada de los microservicios.
- Asegurar que las bases de datos puedan escalar horizontalmente según las necesidades de cada servicio.

## Elementos elegidos para refinar
El foco de esta iteración está en definir cómo cada microservicio interactuará con su base de datos, seleccionando tecnologías específicas que cumplan con las necesidades de cada uno.

## Opciones a considerar/conceptos de diseño considerados
| Opción | Pros | Cons |
|---|---|---|
| Base de datos centralizada | Simplicidad en la gestión, transacciones consistentes entre microservicios | Dependencias fuertes entre servicios, punto único de fallo, escalabilidad limitada |
| Bases de datos distribuidas | Independencia entre microservicios, elección tecnológica según las necesidades de cada servicio, escalabilidad horizontal | Mayor complejidad en transacciones distribuidas, posible inconsistencia eventual, mayor sobrecarga operativa e infraestructural |
## Instanciacion de elementos
Cada microservicio gestionará su persistencia con una base de datos propia. Las tecnologías seleccionadas responden a los requisitos específicos de cada servicio:

- Clientes: PostgreSQL: Base de datos relacional que soporta consultas complejas y garantiza consistencia.
- Pedidos: MongoDB: Base de datos NoSQL que permite almacenar datos no estructurados, ideal para el modelo dinámico de pedidos.
- Repartos y rutas: MongoDB: Adecuada para datos geoespaciales y optimización de rutas.
- Pagos: PostgreSQL: Garantiza la integridad y consistencia necesarias para transacciones financieras.
- Incidencias: MongoDB: Flexibilidad en el manejo de datos no estructurados y de resolución rápida.

## Decisiones tomadas
Se decidió utilizar bases de datos distribuidas, asignando a cada microservicio una base de datos independiente. Esto permite la selección de tecnologías que mejor se ajusten a las necesidades específicas de cada servicio, facilitando el desacoplamiento y la escalabilidad. Esta decisión permite que cada equipo de desarrollo se focalice en su propia persistencia de datos de manera independiente del resto.  
No se desestima que eventualmente esta decisión introduzca desafíos en términos de consistencia y gestión de transacciones distribuidas.

## Artefactos generados

### ADR generado
- [ 0002-bases-de-datos-distribuidas ](/docs/decisions/0002-bases-de-datos-distribuidas.md): Documento que detalla las razones y consecuencias de utilizar bases de datos distribuidas, así como las tecnologías elegidas para cada microservicio.

### Diagrama/sketch del resultado
![image](/docs/resources/bases-de-datos.png)
