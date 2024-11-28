[back](/docs/decisions/home.md)
# Uso de microservicios 

## Contexto y problema

El sistema actual cuenta con una arquitectura monolitica. Se quiere que la arquitectura cuente con una menor rigidez y sea mas facil de evolucionar a traves del tiempo.

## Opciones consideradas

* Migrar hacia un sistema basado en microservicios
* Continuar con el sistema monolito actual, modularizandolo
* Optar por un sistema hibrido

## Opcion elegida

Se eligió la opcion de **migrar hacia un sistema basado en microservicios** dada su gran flexibilidad y facilidad a la hora de escalar.  
En la actualidad hay disponibles muchas herramientas y frameworks para el desarrollo, monitoreo, y despliegue de este tipo de arquitecturas. A su vez, es una practica común por lo que muchos desarrolladores ya se encuentran familiarizados con la misma. En este sentido, la división de responsabilidades se da de manera natural respetando los microservicios planteados.
Por ultimo, es una arquitectura que, combinada con el uso de contendores, permite mucha flexibilidad a la hora del depliegue, pudiendo optar tanto por alternativas locales como cloud.

Se plantea la siguiente división de funcionalidades por microservicio:

![image](/docs/resources/microservicios.png)

### Consecuencias

- **Buena**, mejora el uso de contenedores mejora la capacidad de escalabilidad y facilita la desplegabiliad.
- **Buena**, al aislar las funcionalidades en cada microservicio es posible realizar modificaciones en ellos sin perturbar el sistema en su conjunto.
- **Buena**, flexibilidad de usar diferentes tecnologías en cada microservicio.
- **Mala**, la coexistencia de ambos sistemas durante la transicion hacia microservicios puede ser dificultosa y generar conflictos entre ambos. 
- **Mala**, complejidad a la hora de migrar un sistema monolito hacia microservicios.
- **Mala**, la flexibilidad otorgada por la arquitectura conlleva a tener que establecer prácticas comunes y estándares que respetar por parte del equipo de desarrollo.

## Restricciones afectadas
- Res-1
- Res-2
