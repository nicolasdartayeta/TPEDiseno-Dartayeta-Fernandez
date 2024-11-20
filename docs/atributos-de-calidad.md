[back](/README.md)
# Atributos de calidad
Los atributos de calidad fueron plasmados en los siguientes escenarios:

## Performance
| **ID** | **Escenario** |
|---|---|
| QA-Per-1 | Cuando un cliente realiza un pedido en condiciones normales de trafico este debe ser procesado por el sistema en menos de tres segundos, informandole al usuario si hubo algun error o no.|
|QA-Per-2|Cuando se realiza la planificacion de rutas de reparto el sistema debe generar la planificacion en menos de 30 segundos.|

## Disponibilidad
| **ID** | **Escenario** |
|---|---|
|QA-Dis-1|En el caso de haber una caida de algun microservicio el sistema debe detectar este fallo y poder continuar informando el error.|
|QA-Dis-2| Ante la orden de una compra, el sistema debe contar con la disponibilidad del componente de ruteo en el 99% de los intentos. |

## Modificabiliad
| **ID** | **Escenario** |
|---|---|
| QA-Mod-1 | Ante la implementacion de un nuevos algoritmos de ruteo de mayor eficiencia, el sistema debe poder cambiar el o los modulos existentes en menos de 2 dias. |
| QA-Mod-2 | El sistema debe contar con la posibilidad de agregar nuevos métodos de pago ante la llegada de nuevos sistemas de entidades externas. |

## Seguridad
| **ID** | **Escenario** |
|---|---|
| QA-Seg-1 | Ante un intento de acceso no autorizado a datos de clientes, el sistema detecta y bloquea el intento en 100% de los casos, registrando el evento para auditoría, sin exponer información sensible.|
| QA-Seg-2 | Ante una transaccion inusual debido a grandes montos o usuarios nuevos, el sistema debe catalogar la compra como "sospechosa", dandole la potestad al administrador de aprobarla o rechazarla. |

## Escalabilidad
| **ID** | **Escenario** |
|---|---|
| QA-Esc-1 | Durante una promoción, se incrementan los pedidos a 10 veces la carga normal. El microservicio de Pedidos se escala automáticamente, manteniendo el tiempo de respuesta debajo de 2 segundos.|

## Desplegabilidad
| **ID** | **Escenario** |
|---|---|
| QA-Des-1 | Ante un cambio de implementacion de un microservicio, el sistema debe desplegar el mismo en menos de 30 minutos.|

## Portabilidad
| **ID** | **Escenario** |
|---|---|
| QA-Por-1 | El sistema debe poder desplegarse tanto localmente o como en cualquier plataforma en la nube. |

## Interoperabilidad
| **ID** | **Escenario** |
|---|---|
| QA-Int-1 | Cuando el usuario realiza un pago, el sistema debe comunicarse eficientemente con MercadoPago y validar la transacción. |

