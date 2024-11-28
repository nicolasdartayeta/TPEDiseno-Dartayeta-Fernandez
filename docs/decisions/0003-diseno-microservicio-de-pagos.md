[back](/docs/decisions/home.md)
# Diseño microservicio de pagos

## Contexto y problema
El microservicio de pagos es un componente crítico del sistema que debe gestionar transacciones de manera segura, eficiente y flexible. Su diseño debe cumplir con los siguientes requisitos clave:  

- **Seguridad**: Ante intentos de acceso no autorizado, el sistema debe detectarlos y bloquearlos en el 100% de los casos, registrando los eventos para luego ser revisados. 

- **Integración eficiente**: Debe interactuar con la pasarela de Mercado Pago de manera rápida y confiable. 

- **Extensibilidad**: El sistema debe ser modular y preparado para integrar nuevos métodos de pago de manera sencilla, anticipando cambios en las necesidades del negocio o la llegada de nuevas tecnologías de pago.  

Dado este contexto, es necesario elegir un diseño que cumpla con estos objetivos.  

## Opciones consideradas

- **Integración directa con la API de Mercado Pago**: Este enfoque consiste en implementar directamente las interacciones con Mercado Pago en el código del microservicio, sin capas intermedias ni abstracciones adicionales.  

- **Uso de un adaptador genérico para pasarelas de pago**: Este enfoque introduce una capa de abstracción que encapsula las interacciones con pasarelas de pago, permitiendo una integración más flexible y desacoplada.  

## Opcion elegida

Opción elegida: **"Uso de un adaptador genérico para pasarelas de pago"**. Se eligió esta opción porque garantiza una mayor flexibilidad y sostenibilidad a largo plazo, permitiendo integrar fácilmente nuevos métodos de pago o realizar cambios sin afectar la lógica central del microservicio. Aunque la implementación inicial puede ser más compleja, esta decisión mitiga riesgos futuros relacionados con cambios en las pasarelas de pago o la necesidad de soportar múltiples sistemas de pago.  
Además, este enfoque permite encapsular la lógica específica de cada pasarela en el adaptador, manteniendo la lógica de negocio limpia y enfocada en los objetivos del sistema. Dado que la pasarela inicial será Mercado Pago, el diseño del adaptador se ajustará para cubrir sus necesidades, pero será suficientemente genérico para extenderse a otros servicios.

![image](/docs/resources/microservicio-pagos.png)  

### Consecuencias

- **Buena**, extensibilidad del sistema: La abstracción mediante un adaptador permite agregar nuevos métodos de pago sin necesidad de modificar el núcleo del microservicio.

- **Buena**, modularidad y mantenibilidad: Al desacoplar la lógica del microservicio de las implementaciones específicas de las pasarelas, se facilita el mantenimiento y la actualización del sistema. 

- **Buena**, seguridad centralizada: El diseño permite centralizar las validaciones de seguridad en un módulo especializado, garantizando que todos los intentos de acceso no autorizado sean manejados de manera uniforme y consistente.  

- **Mala**, complejidad inicial: La necesidad de diseñar e implementar un adaptador genérico incrementa el tiempo y esfuerzo necesarios para la entrega inicial del microservicio.  

## Atributos de calidad afectados
- QA-Seg-1
- QA-Int-1
- QA-Mod-2