# Visión General de la Red

## Descripción

La red de EOS.IO esta compuesta de un algoritmo de consenso descentralizado \(DPoS\), un sistema de administración de los recursos de la red, un proceso de gobernanza y un conjunto de incentivos para aquellos que usan la red.

## Prueba de Participación Delegada

La [Prueba de Participación Delegada \(DPOS\)](https://steemit.com/dpos/@dantheman/dpos-consensus-algorithm-this-missing-white-paper) le dan el poder a los tenedores de tokens para seleccionar a los productores de bloques a través de un sistema de votación continuo. Cualquiera puede elegir participar en la producción de bloques y les será otorgada la posibilidad de producir bloques, si persuaden a los tenedores de tokens de votar por ellos.

Un tenedor de tokens en la cadena de bloques de EOS.IO, puede no tener la necesidad inmediata the consumir parte o todo el ancho de banda que esos tokens proporcionan, puede delegar o rentar ese ancho de banda no consumido a otros.

## Propuestas

Además de elegir productores de bloques, los tenedores de tokens pueden elegir un número de Propuestas de Trabajo creadas para beneficiar a la comunidad. Las propuestas ganadoras recibirán tokens hasta un porcentaje configurado de la inflación de tokens menos aquellos tokens que hayan sido pagados a los productores de bloques.

## Incentivo

La cadena de bloques de EOS.IO premiará con nuevos tokens a los productores de bloques cada vez que un bloque es producido. Un límite a los premios otorgados a los productores puede ser configurado de manera tal que el incremento anual total de la oferta de tokens no exceda el 5%.

## Staking

### Recursos

En la cadena de bloques de EOS.IO, hay tres amplias clases de recursos que son consumidas por las aplicaciones:

* Ancho de Banda and Almacenamiento de Registros \(Disco\);
* Poder de Cómputo y Cómputos Pendientes \(CPU\); y
* Almacenamiento del Estado \(RAM\).

### Consumo

El software de EOS.IO permite a cada cuenta consumir un porcentaje de la capacidad disponible proporcional a la cantidad de tokens que se encuentran en un contrato que bloquea los tokens por 3 días.  Por ejemplo, si una cuenta en la cadena de bloques de EOS.IO posee el 1% del total de tokens distribuibles en esa cadena de bloques, entonces tiene el potencial de utilizar el 1% de la capacidad de almacenamiento del estado.

Mientras que el ancho de banda y el poder de cómputo puede ser delegado, el almacenamiento del estado de la aplicación requerirá que el desarrollador de la aplicación posea tokens, o dejarlos reservados, hasta que el estado sea borrado. Si el estado nunca es borrado, entonces esos tokens se encuentran efectivamente fuera de circulación.

## Gobernanza

El proceso de gobernanza de la cadena de bloques de EOS.IO reconoce que el poder se origina en los poseedores de tokens que delegan el poder a los productores de bloques. El proceso de gobernanza dirige eficientemente la influencia existente de los productores de bloques para que se alínie con los intereses de los tenedores de tokens.

### Capacidades

Los Productores de Bloques tienen una autoridad limitada y controlada para congelar cuentas, actualizar aplicaciones defectuosas, y proponer cambios al protocolo que pueden dividir la cadena de bloques. Antes que cualquier cambio pueda realizarse a la cadena de bloques, los productores deben aprobarlo. Si el productor de bloques se niega a realizar los cambios deseados por los tenedores de tokens entonces pueden estos pueden quitarle el voto.

### Constitución

El software de EOSIO permite a las cadenas de bloques establecer un acuerdo de términos de servicio entre pares o contratos entre aquellos usuarios que firman la "constitución". El contenido de esta constitución define obligaciones entre los usuarios que no pueden ser completamente aplicadas a través de código y facilita la resolución de disputas estableciendo una jurisdicción y la elección de las leyes junto con otras reglas aceptadas mutuamente. Cada transacción transmitida a la red debe incorporar el hash de la constitución como parte de la firma y de esa manera explícitamente obligan al firmante a cumplir con el contrato.

### Arbitraje

La constitución de la cadena de bloques de EOS.IO blockchain establece que todos los usuarios acuerdan resolver las disputas a través de un sistema de arbitraje.

