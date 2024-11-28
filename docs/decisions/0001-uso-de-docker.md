[back](/docs/decisions/home.md)
# Uso de Docker

## Contexto y problema
El sistema debe tener un tiempo de despliegue rápido, pudiendo adaptarse facilmente a diferentes entornos tanto locales como en la nube.

## Opciones consideradas
- **Uso de maquinas virtuales**: Proveen un entorno completo con un sistema operativo independiente para cada microservicio. Ofrecen un aislamiento robusto y una gestión madura para aplicaciones tradicionales. Sin embargo, su uso requiere mayores recursos de hardware, el despliegue es más lento y la portabilidad es limitada, ya que dependen de hipervisores específicos.

- **Uso de contenedores con Docker**: Los contenedores son ligeros, comparten el kernel del sistema operativo del host y permiten empaquetar microservicios con todas sus dependencias. Esto facilita la portabilidad, escalabilidad y rapidez en el despliegue.

## Opcion elegida
Se eligió la opción de usar contenedores con Docker. Los contenedores permiten una mayor portabilidad al poder desplegarse en una variedad de plataformas sin necesidad de grandes cambios, lo que simplifica la transición entre entornos de desarrollo y ambientes de despliegue. Además, las actualizaciones y modificaciones pueden ser desplegadas rápidamente, alineándose con la necesidad de tiempos de despliegue cortos. Cada microservicio será empaquetado y ejecutado en un contenedor independiente, lo que favorece su aislamiento y gestión individual.

### Consecuencias
- **Buena**, los contenedores posibilitan una portabilidad significativamente mayor, permitiendo que el mismo contenedor funcione sin modificaciones en diferentes entornos, desde una máquina de desarrollo hasta un clúster en la nube.

- **Buena**, al desplegar cada microservicio en su propio contenedor, se facilita el desarrollo y la integración continua, permitiendo actualizaciones o modificaciones específicas sin interrumpir otros servicios.

- **Buena**, el tiempo de despliegue se reduce considerablemente, ya que los contenedores son más rápidos de iniciar que las máquinas virtuales, lo que es ideal para sistemas con cambios frecuentes o necesidades de escalabilidad dinámica.

- **Mala**, se suma una nueva tecnología al stack, lo que implica un esfuerzo inicial para que el equipo aprenda a trabajar con Docker y herramientas relacionadas. Esto incluye el manejo de imágenes, redes, volúmenes y, eventualmente, herramientas de orquestación como Kubernetes si el sistema crece.

- **Mala**, los contenedores no ofrecen el mismo nivel de aislamiento que las máquinas virtuales, lo que puede representar un riesgo de seguridad si no se implementan correctamente las configuraciones y prácticas de seguridad necesarias.

## Atributos de calidad afectados
- QA-Des-1
- QA-Por-1