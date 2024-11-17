# Descomposición de módulos críticos y diseño inicial

## Contexto y Problema

Sabiendo los puntos criticos del sistema, se capturan los módulos críticos, estableciendo sus responsabilidades, relaciones para garantizar el cumplimiento de los atributos de calidad.


## Opciones consideradas

* Crear microservicios individuales para cada módulo crítico.
* Fusionar los módulos críticos en un solo microservicio.

## Opcion elegida

Opcion elegida: "Crear microservicios individuales para cada módulo crítico", dado su capacidad de modularizacion, escalabilidad y respuesta ante errores. Ademas, se ofrece flexibilidad ante actualizaciones y cambios en cada modulo individual.

### Consecuencias

* Buena, cada módulo puede escalar de manera independiente según carga individual.
* Buena, los fallos en un módulo crítico no afectan directamente a los demás.
* Mala, aumento en complejidad al gestionar múltiples servicios y bases de datos.

## Atributos de calidad satisfechos

* QA-Dis-1 (Cada módulo tiene su propia infraestructura específica para recuperación ante fallos)
* QA-Mod-1 (Nuevos algoritmos de ruteo pueden implementarse fácilmente)
* QA-Esc-1 (Cada módulo puede escalar de forma independiente)