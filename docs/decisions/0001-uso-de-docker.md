# Uso de Docker

## Contexto y problema
El sistema debe tener un tiempo de despliegue rápido, pudiendo adaptarse facilmente a diferentes entornos tanto locales como en la nube.

## Opciones consideradas
* Uso de maquinas virtuales
* Uso de contenedores con Docker

## Opcion elegida
Opcion elegida: "Uso de contenedores con Docker" ya que los contenedores pueden ser desplegados en una variedad de plataformas sin necesidad de grandes cambios. A su vez las modificaciones pueden ser desplegadas rapidamente. 

### Consecuencias
* Buena, los contenedores posibilitan mayor portabilidad y desplegabilidad.
* Buena, los microservicios pueden ser desplegados por contenedor, permitiendo modificarlos independientemente uno de otro.
* Mala, se suma una nueva tecnologia al stack.