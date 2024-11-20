# Bases de datos distribuidas

## Contexto y problema
Algunos microservicios requieren persistencia de datos. Es necesario decidir como van a almacenar esos datos cada microservicio. independiente y desacoplada.

## Opciones consideradas

- Base de datos centralizada
- Bases de datos distribuidas

## Opcion elegida
Opcion elegida: "Bases de datos distribuidas". Cada microservicio, de necesitarlo, contará con una base de datos propia. Dependiendo el contexto se podra elegir la tecnología apropiada según los requerimientos:
- Clientes: PostgreSQL
- Pedidos: MongoDB
- Repartos y rutas: MongoDB
- Pagos: PostgreSQL
- Incidencias: MongoDB

### Consecuencias

- Buena, independencia entre servicios
- Buena, escalabilidad horizontal
- Buena, libertad de elección tecnológica
- Mala, complejidad en transacciones distribuidas
- Mala, mayor overhead de infraestructura
- Mala, posible inconsistencia entre microservicios

## Atributos de calidad afectados
- QA-Dis-1
