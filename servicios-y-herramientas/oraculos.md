# Oráculos

{% hint style="info" %}
Fuentes:   
[https://blockchainhub.net/blockchain-oracles/](https://blockchainhub.net/blockchain-oracles/) [https://cointelegraph.com/explained/blockchain-oracles-explained](https://cointelegraph.com/explained/blockchain-oracles-explained)​
{% endhint %}

### Introducción {#introduction}

Un oráculo, en el contexto de cadenas de bloques y contratos inteligentes, es una agente que encuentra y verifica eventos de la vida real y envía esta información a la cadena de bloques para ser usada por un contrato inteligente.

Los contratos inteligentes contienen valor y solo desbloquean ese valor si ciertas condiciones predefinidas son alcanzadas. Cuando una condición particular es alcanzada, el contrato inteligente cambia su estado y ejecuta los algoritmos definidos programáticamente, lanzando de forma automática un evento en la cadena de bloques. 

Las cadenas de bloques no pueden acceder a información fuera de su red. Un oráculo es un proveedor de información - proporcionado por un servicio de terceros - diseñado para su uso en contratos inteligentes en la cadena de bloques. La tarea primaria de los oráculos es proveer estos valores al contrato inteligente  de una manera segura y confiable. Estos pueden ser cualquier información como por ejemplo la temperatura, un pago exitoso, fluctuaciones de precios, etc.

Los oráculos son parte de contratos con múltiples firmas donde, por ejemplo, varias cuentas firman un contrato para la futura liberación de fondos solamente si ciertas condiciones son alcanzadas. Antes que cualquier fondo sea liberado un oráculo también tiene que firmar el contrato inteligente.

### La Necesidad de los Oráculos {#the-need-for-oracles}

Existe una diferencia fundamental de formatos. La cadena de bloques es determinística, lo que significa que es un reflejo de una serie de eventos que se realizan uno después de otro de manera secuencial - es una serie de transacciones. Acceder a información fuera de la cadena de bloques requeriría una serie de datos que no son secuenciales y por lo tanto seria imposible que tengan sentido para una cadena de bloques. Este aspecto de la cadena de bloques le da inmutabilidad, pero reduce su flexibilidad.

El mundo fuera de la cadena de bloques, sin embargo, es no determinístico, lo que significa que no hay un registro de los eventos de manera secuencial en el orden en que se han producido, lo que crea un problema de transparencia. La serie de datos puede ser generada desde cualquier lugar y elaborada en cualquier momento, dando mayor flexibilidad, pero dificultando la comunicación con la cadena de bloques.

Esta diferencia sustancial hace que estos dos mundos sean incompatibles entre si por naturaleza, y solamente la presencia de los oráculos pueden hacer que la comunicación entre ellos en ambas direcciones sea posible.

### **Tipos de Oráculos** {#types-of-oracles}

Hay diferentes tipos de oráculos basados en el tipo de uso. Existen oráculos de software, de hardware, de consenso, de entrada y de salida.

* **Oráculos de Software**  Los oráculos de software manejan información que está disponible en línea. Un ejemplo puede ser la temperatura, precios de commodities y bienes, demoras en vuelos o trenes, etc. La información se encuentra originada por fuentes en línea como el sitio web de la compañía. Los oráculos de software extraen la información y la envían al contrato inteligente.
* **Oráculos de Hardware**  Algunos contratos inteligentes necesitan información directa del mundo físico, por ejemplo, un auto cruzando una barrera donde sensores de movimiento deben detectar el vehículo y enviar la información a un contrato inteligente. Otra caso de uso es el de los sensores RFID en la industria de la cadena de suministro. El mayor desafío que tienen los oráculos de hardware es la habilidad de poder reportar lecturas sin sacrificar la seguridad de la información. [Oraclize](http://www.oraclize.it/) propone una solución de 2 pasos para este riesgo, proveyendo una evidencia criptográfica de las lecturas del sensor y mecanismos para evitar la manipulación que dejan inoperable el equipo en caso de violación.
* **Oráculos de Entrada**  Estos proveen información del mundo externo al contrato inteligente. Un caso de uso de ejemplo es el de una orden de compra automática en el caso que el dólar alcance un precio específico.
* **Oráculos de Salida**  Estos le permiten a un contrato inteligente enviar información al mundo exterior. Un ejemplo es el de una cerradura inteligente en el mundo real que recibe un pago a su direccion en la cadena de bloques y necesita abrirse automáticamente.
* **Oráculos de Consenso**  Los mercados de predicción como Augur y Gnosis confían en gran parte en oráculos para confirmar los resultados futuros. Usar una sola fuente de información puede ser riesgoso y no muy confiable. Para evitar la manipulación del mercado, los mercados de predicción implementan un sistema de puntuación para los oráculos. Para más seguridad, una combinación de diferentes oráculos puede ser utilizada, donde por ejemplo 3 de 5 oráculos pueden determinar el resultado de un evento.

### **Desafíos de Seguridad** {#security-challenges}

Los oráculos son servicios de terceros que no son parte del mecanismo de consenso de la cadena de bloques. El principal desafío de los oráculos es que las personas deben confiar en estas fuentes de información. Ya sea un sitio web o un sensor, la fuente de datos tiene que ser confiable. Diferentes técnicas de computación confiables pueden ser usadas para resolver este problema. Compañías como  [Oraclize](http://www.oraclize.it/), por ejemplo, han ayudado a Amazon con pruebas basadas en [TLSNotary](https://tlsnotary.org/). Town Crier, otra compañía, se está focalizando en el uso de Intel [Software Guard Extensions](https://software.intel.com/en-us/blogs/2013/09/26/protecting-application-secrets-with-intel-sgx) \(SGX\). 

Proveer a los contratos inteligentes con información confiable es crucial para los usuarios porque en el caso de fallas no existe posibilidad de dar vuelta atrás.

