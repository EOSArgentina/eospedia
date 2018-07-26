# EOS.IO - Whitepaper

{% hint style="info" %}
Fuente y agradecimiento: [https://steemit.com/eos/@leonel-wainer/eos-io-white-paper-tecnico-en-espanol](https://steemit.com/eos/@leonel-wainer/eos-io-white-paper-tecnico-en-espanol)
{% endhint %}

EOS.IO Technical White Paper  
BORRADOR: 5 de junio de 2017

### Resumen

El software EOS.IO presenta una nueva arquitectura blockchain diseñada para habilitar el escalado vertical y horizontal de aplicaciones descentralizadas. Esto se logra creando una construcción similar al sistema operativo sobre el cual se pueden construir aplicaciones. El software proporciona cuentas, autenticación, bases de datos, comunicación asíncrona y la programación de aplicaciones a través de cientos de núcleos de CPU o clusters. La tecnología resultante es una arquitectura blockchain que se escala a millones de transacciones por segundo, elimina las tarifas de transacciones a los usuarios, y permite el despliegue fácil y rápido de las aplicaciones descentralizadas.

Copyright © 2017 block.one  
Sin permiso, cualquiera puede usar, reproducir o distribuir cualquier material en este documento para uso no comercial y educativo \(es decir, aparte de por una cuota o con fines comerciales\) siempre que se cite la fuente original y el aviso de derechos de autor aplicable.

AVISO LEGAL: Este borrador EOS.IO Technical White paper es solo para fines informativos. block.one no garantiza la exactitud de las concluciones alcanzadas en este documento, y el documento se proporciona "tal cual" sin representaciones y garantías, expresas o implícitas, fuere lo que fuere, incluyendo, pero no limitado a: \(i\) garantías de comerciabilidad, aptitud para un fin específico, título o sin violación de derechos; \(ii\) que el contenido de este documento está libre de error o adecuado para cualquier fin; y \(iii\) dicho contenido no infringirá los derechos de terceros. Todas las garantías están expresamente excluidas. block.one y sus afiliados expresamente renuncian a toda responsabilidad por daños de cualquier tipo derivados del uso, referencia, o dependencia de cualquier información contenida en este documento, incluso si es advertido de la posibilidad de tales daños. En ningún caso block.one o sus afiliados serán responsables frente a cualquier persona o entidad por cualquier daño directo, indirecto, especial o consecuente por el uso de, referencia, o dependencia de este documento o cualquiera de los contenidos en este documento.

### Glosario

* Historial
* Requisitos Para las Aplicaciones Blockchain
* Soportar a Millones de Usuarios
* Uso Gratuito
* Actualizaciones Sencillas y Correcciones de Fallos
* Baja Latencia
* Rendimiento Secuencial
* Rendimiento Paralelo
* Algoritmo de Consenso \(DPOS\)
  * Confirmación de la Transacción
  * Transacción Como Prueba de Participación \(TaPoS\)
* Cuentas
  * Mensajes y Manejadores
  * Gestión de Permisos Basada en Funciones
    * Niveles de Permiso Nombrado
    * Grupos de Manejadores de Mensajes Nombrado
    * Mapeo de Permisos
    * Evaluación de Permisos
      * Grupos de Permisos Predeterminados
      * Evaluación Paralela de Permisos
    * Mensajes con Retardo Obligatorio
    * Recuperación de las Claves Robadas
* Ejecución Determinística Paralela de Aplicaciones
  * Minimizar la Latencia de las Comunicaciones
  * Manejadores de Mensajes de Solo Lectura
  * Transacciones Atómicas con Cuentas Múltiples
  * Evaluación Parcial del estado del Blockchain
  * Mejor Planificación Subjetiva de Esfuerzo
* Modelo de Token y Uso de Recursos
  * Medidas Objetivas y Subjetivas
  * El Receptor Paga
  * Delegación de Capacidad
  * Separar los costos de Transacción for Valor de Token
  * Costes del Almacenamiento de Estado
  * Recompensas por el Block
  * Aplicaciones de Beneficios Comunitarios
* Gobernanción
  * Bloqueo de Cuentas
  * Cambio de Código de la Cuenta
  * Constitución
  * Actualización del Protocolo y Constitución
    * Cambios Urgentes
* Scripts y Máquinas Virtuales
  * Mensajes Definidos por Esquemas
  * Base de Datos Definidos por Esquemas
  * Separando Autenticación de la Aplicación
  * Virtual Machine Independent Architecture
    * Montaje de la Web
    * Ethereum Virtual Machine \(EVM\)
* Comunicación Inter-Blockchain
  * Merkle Proofs for Light Client Validation \(LCV\)
  * Latencia de Comunicación Interchain
  * Prueba de Completitud
* Conclusión

### Historia

La tecnología Blockchain fue introducida en el 2008 con el lanzamiento de la moneda bitcoin, y desde entonces los empresarios y programadores han estado tratando de generalizar la tecnología con el fin de admitir una gama más amplia de aplicaciones en una sola plataforma blockchain.

Mientras que varias plataformas blockchain han tenido dificultades para admitir aplicaciones funcionales descentralizadas, aplicaciones blockchains específicas como los intercambios descentralizado, BitShares \(2014\) y la plataforma de la red social, Steem \(2016\) se han convertido en blockchains muy utilizadas con decenas de miles de usuarios activos a diario. Han logrado esto aumentando el rendimiento a miles de transacciones por segundo, reduciendo la latencia a 1.5 segundos, eliminando las tarifas, y proporcionando una experiencia de usuario similar a las actualmente proporcionadas por los servicios centralizados existentes.

Las plataformas blockchain se ven agobiadas por grandes tarifas y capacidad computacional limitada que impiden la adopción extendida de blockchain.

### Requisitos para Aplicaciones Blockchain

Para obtener un uso extendido, las aplicaciones en blockchain requieren una plataforma que sea lo suficientemente flexible para cumplir los siguientes requisitos:

#### Apoyar a Millones de Usuarios

Negocios afectados como Ebay, Uber, AirBnB, y Facebook, requieren una tecnología blockchain capaz de manejar decenas de millones de usuarios diarios activos. En algunos casos, las aplicaciones pueden que no funcionen a menos que se alcance una masa crítica de usuarios y por lo tanto, una plataforma que pueda manejar el número de masa de usuarios es primordial.

#### Uso Gratuito

Los desarrolladores de aplicaciones necesitan la flexibilidad para ofrecer a los usuarios servicios gratuitos; Los usuarios no deben de tener que pagar para usar la plataforma o beneficiarse de sus servicios. Una plataforma blockchain que es de uso gratuito para los usuarios probablemente ganará adopción más extendida. Los desarrolladores y empresas pueden entonces crear estrategias efectivas de monetización.

#### Actualizaciones Sencillas y Correcciones de Fallos

Las empresas que crean aplicaciones basadas en blockchain necesitan la flexibilidad para mejorar sus aplicaciones con nuevas características.

Todo software no trivial está sujeto a errores, incluso con la más rigurosa verificación formal. La plataforma debe ser lo suficientemente fuerte como para corregir errores cuando ocurren inevitablemente.

#### Baja Latencia

Una buena experiencia de usuario exige un feedback fiable con un retraso de no más de unos segundos. Los retrasos más largos frustran a los usuarios y hacen que las aplicaciones creadas sobre un blockchain seas menos competitivas con las alternativas no-blockchain ya existentes.

#### Rendimiento Secuencial

Hay algunas aplicaciones que simplemente no se pueden implementar con algoritmos paralelos debido a pasos secuencialmente dependientes. Las aplicaciones como los intercambios necesitan un rendimiento secuencial suficiente como para manejar elevados volúmenes y por lo tanto, se requiere una plataforma con un rendimiento secuencial alto.

#### Rendimiento Paralelo

Las aplicaciones a gran escala necesitan dividir la carga de trabajo entre varias CPUs y ordenadores.

### Algoritmo de Consenso \(DPOS\)

El software EOS.IO utiliza el único algoritmo de consenso descentralizado capaz de satisfacer los requisitos de rendimiento de las aplicaciones en el blockchain, Prueba de Participación Delegada \(DPOS\). Bajo este algoritmo, aquellos que tienen tokens en un blockchain pueden seleccionar productores de bloques a través de un sistema de votación de aprobación continua y cualquiera puede elegir participar en la producción de un bloque y se les dará la oportunidad de producir bloques proporcionales al total de votos que recibieron en relación a todos los demás productores. Para los blockchains privados la administración usará los tokens para añadir o quitar personal de IT.

El software EOS.IO habilita que los bloques se produzcan exactatamente cada 3 segundos y exactamente un productor está autorizado para producir un bloque en cualquier momento dado. Si el bloque no se produce a la hora programada entonces el bloque para ese intervalo de tiempo es omitido. Cuando se omiten uno o más bloques, hay un intervalo de 6 o más segundos en el blockchain.

Usando el software EOS.IO, los bloques se producen en rondas de 21. Al inicio de cada ronda, se eligen 21 productores de bloques únicos. Los 20 primeros se eligen automáticamente por aprobación total en cada ronda y el último productor es elegido en proporción a su número de votos en relación con otros productores. Los productores seleccionados se reorganizan utilizando un número pseudoaleatorio derivado del tiempo del bloque. Esta reorganización se realiza para asegurar que todos los productores mantienen una conectividad equilibrada con todos los demás productores.

Si un productor pierde un bloque y no ha producido ningún otro bloque en las últimas 24 horas, es retirado de la consideración hasta que notifique el blockchain de su intención de empezar a producir bloques de nuevo. Esto garantiza que la red funcione con fluidez al minimizar el número de bloques perdidos al no programar a aquellos que han demostrado ser poco fiables.

Bajo condiciones normales, un blockchain DPOS no experimenta bifurcaciones porque los productores de bloques cooperan para producir bloques, en lugar de competir. En el caso de que haya una desviación, el consenso se cambiará automáticamente a la cadena más larga. Esta métrica funciona porque la velocidad a a la que los bloques se añaden a la cadena de bifurcación de blockchain está directamente correlacionada con el porcentaje de productores de bloques que comparten el mismo consenso. En otras palabras, una bifurcación de blockchain con más productores crecerá en longitud más rápido que uno con menos productores. Además, ningún productor de bloques debería producir bloques en dos horquillas al mismo tiempo. Si se encuentra a un productor de bloques haciendo esto, entonces, tal productor de bloques probablemente será eliminado. La evidencia criptográfica de esta doble producción también puede usarse para automáticamente eliminar a los abusadores.

#### Confirmación de la Transacción

Los blockchain DPOS típicos tienen un 100% de participación de productores de bloques. Una transacción puede considerarse confirmada con un 99.9% de certeza, después de un promedio de 1.5 segundos desde el momento de emisión.

Hay algunos casos extraordinarios donde un error de software, la congestión de internet o un productor de bloques maligno creará dos o más bifurcaciones. Para tener una certeza absoluta de que una transacción es irreversible, un nódulo puede elegir esperar la confirmación de 15 de los 21 productores de bloques. Basado en una configuración típica del software EOS.IO, esto tardará un promedio de 45 segundos en circunstancias normales. Por defecto todos los nódulos considerarán irreversible un bloque confirmado por 15 de 21 productores y no cambiarán a una bifurcación que excluya tal bloques, independientemente de su longitud.

Es posible que un nódulo advierta a los usuarios que hay una alta probabilidad de que estén en una bifurcación minoritaria, dentro de los 9 segundos del inicio de una bifurcación. Después de 2 bloques consecutivos perdidos, hay una probabilidad del 95% de que un nódulo está en una bifurcación minoritaria. Con 3 bloques consecutivos perdidos, hay una certeza del 99% de estar en una bifurcación minoritaria. Es posible generar un modelo predictivo fuerte que utilice información sobre los nódulos que fallaron, las tasas recientes de participación, y otros factores para rápidamente advertir a los operadores de que algo está mal.

La respuesta a tal advertencia depende completamente de la naturaleza de las transacciones comerciales, pero la respuesta más simple es esperar a 15/21 confirmaciones hasta que se detenga la advertencia.

#### Transacción Como Prueba de Participación \(TaPoS\)

El software EOS.IO requiere que cada transacción incluya el hash de un encabezado de bloque reciente. Este hash tiene dos propósitos:

evita la repetición de una transacción en bifurcaciones que no incluyen el bloque referenciado; y  
señala a la red de que un usuario particular y su stake \(participación\) están en una bifurcación específica.

Con el tiempo todos los usuarios acaban confirmando directamente el blockchain, lo que dificulta forjar cadenas falsificadas, ya que la falsificación no podría desplazar transacciones de la cadena legítima.

### Cuentas

El software EOS.IO permite que todas las cuentas sean referenciadas por un nombre único legible por humanos, de 2 a 32 caracteres de longitud. El nombre es elegido por el creador de la cuenta. Todas las cuentas deben ser financiadas con el saldo mínimo de la cuenta en el momento que se crean para cubrir el coste de almacenar los datos de la cuenta. Los nombres de cuenta también admiten namespaces \(espacio de nombres\) tales que el propietario de la cuenta [@domain](https://steemit.com/@domain), es el único que puede crear la cuenta [@user.domain](https://steemit.com/@user.domain).

En un contexto descentralizado, los desarrolladores de aplicaciones pagarán el coste nominal de la creación de la cuenta para inscribir a un nuevo usuario. Las empresas tradicionales ya gastan sumas significativas de dinero por cada cliente que adquieren, en forma de publicidad, servicios gratuitos, etc. El coste de financiar un nueva cuenta de blockchain debería de ser insignificante en comparación. Afortunadamente, no hay necesidad de crear cuentas para usuarios ya unidos por otra aplicación.

#### Mensajes & Manejadores

Cada cuenta puede enviar mensajes estructurados a otras cuentas y pueden definir scripts para manejar mensajes cuando se reciben. El software EOS.IO le da a cada cuenta su propia base de datos privada a la que solo pueden acceder sus propios manejadores de mensajes. Los scripts de manejo de mensajes también pueden enviar mensajes a otras cuentas. La combinación de mensajes y manejadores de mensajes automatizados es como EOS.IO define contratos inteligentes.

#### Gestión de Permisos Basada en Funciones

La gestión de permisos implica determinar si un mensaje está correctamente autorizado o no. La forma más simple de administración de permisos es comprobar que una transacción tiene las firmas requeridas, pero esto implica que las firmas requeridas ya sean conocidas. En general, la autoridad está ligada a individuos o grupos de individuos y a menudo está compartimentada. El software EOS.IO proporciona un sistema de gestión de permisos declarativo que ofrece a las cuentas un control detallado y de alto nivel sobre quién puede hacer qué y cuándo.

Es fundamental que la autenticación y administración de permisos sean normalizadas y separadas de la lógica de negocio de la aplicación. Esto permite que se desarrollen herramientas para administrar permisos de una manera de propósito general y también proporcionan oportunidades significativas para la optimización del rendimiento.

Cada cuenta puede ser controlada por cualquier combinación ponderada de otras cuentas y claves privadas. Esto crea una estructura de autoridad jerárquica que refleja cómo se organizan los permisos en la realidad, y hace que el control multiusuario sobre los fondos sea más fácil que nunca. El control multiusuario es el mayor contribuyente a la seguridad, y cuando se utiliza correctamente, puede eliminar enormemente el riesgo de robo debido a la piratería.

El software EOS.IO permite a las cuentas definir qué combinación de claves y/u otras cuentas pueden enviar un tipo de mensaje en particular a otra cuenta. Por ejemplo, es posible tener una clave para la cuenta de una red social de un usuario y otra para el acceso al intercambio. Es incluso posible dar permiso a otras cuentas para actuar a nombre de la cuenta de un usuario sin asignarles unas claves.

#### Niveles de Permiso Nombrado

![](https://steemitimages.com/0x0/http://eos.io/wpimg/diagram3.png)  
Utilizando el software EOS.IO, las cuentas pueden definir niveles de permisos nombrados, cada uno de los cuales puede derivarse de permisos nombrados con un nivel superior. Cada nivel de permiso nombrado define una autoridad; una autoridad es un control de multi-firma de umbral que consiste en claves y/o niveles de permisos nombrados de otras cuentas. Por ejemplo, el nivel de permiso "Amigo" de una cuenta puede establecerse para que la cuenta sea igualmente controlada por cualquiera de los amigos de la cuenta.

Otro ejemplo es el blockchain de Steem que tiene tres niveles de permisos nombrados con codificado: propietario, activo y publicación. El permiso de publicación solo puede realizar acciones sociales como votar y publicar, mientras que el permiso activo puede hacer todo excepto cambiar el propietario. El permiso del propietario es para el cold storage y es capaz de hacer todo. EOS.IO generaliza este concepto al permitir que cada titutar de cuenta defina su propia jerarquía así como la agrupación de acciones.

#### Grupos de Manejadores de Mensajes Nombrados

El software EOS.IO permite que cada cuenta organice sus propios manejadores de mensajes en grupos nombrados y anidados. Estos grupos de manejadores de mensajes nombrados pueden ser referenciados por otras cuentas cuando configuran sus niveles de permiso.

El nivel más alto del grupo de manejadores de mensajes es el nombre de cuenta, y el nivel más bajo es el tipo de mensaje individual que recibe la cuenta. Estos grupos se pueden referenciar del siguiente modo: @nombredecuenta.grupoa.subgrupob.TipodeMensaje.

Bajo este modelo, es posible un contrato de intercambio para agrupar la creación de orden y cancelar por separado desde depósito y retirada. Esta agrupación por el contrato de intercambio es una ventaja para los usuarios del intercambio.

#### Mapeo de Permisos

El software EOS.IO permite que cada cuenta defina un esquema entre un Grupo de Controladores de Mensaje Nombrado de cualquier cuenta y su propio Nivel de Permiso Nombrado. Por ejemplo, un titular de cuenta podría asignar la aplicación de la red social del titular de la cuenta al grupo de permiso "Amigo" del titular de la cuenta. Con este esquema, cualquier amigo podría publicar como titular de la cuenta en las redes sociales del titular de la cuenta. A pesar de que se publicaría como titular de la cuenta, todavía usarían sus propias claves para firmar el mensaje. Esto significa que siempre es posible identificar qué amigos usaron la cuenta y de qué manera.

#### Evaluación de Permisos

Al enviar un mensaje de tipo "Acción", de [@alice](https://steemit.com/@alice) a [@bob](https://steemit.com/@bob), el software EOS.IO verificará primero si [@alice](https://steemit.com/@alice) ha definido un mapeo de permiso para @bob.grupoa.subgrupo.Acción. Si no se encuentra nada entonces un mapeo para @bob.grupoa.subgrupo, luego para [@bob.grupoa](https://steemit.com/@bob.grupoa), y por último [@bob](https://steemit.com/@bob), serán verificados. Si no se encuentra ningun parecido adicional, entonces el mapeo asumido será para el grupo de permisos nombrado [@alice.activo](https://steemit.com/@alice.activo).

Una vez que se identifica un mapeo, la autoridad de firma es validada utilizando el proceso de multi-firma de umbral y la autoridad asociada con el permiso nombrado. Si eso falla, entonces se transversa hasta el permiso de los padres y finalmente, al permiso de propietario, @alice.propietario.  
![](https://steemitimages.com/0x0/http://eos.io/wpimg/diagram2grayscale2.jpg)

#### Grupos de Permisos Predeterminados

La tecnología también permite que todas las cuentas tengan un grupo "propietario" que puede hacer todo, y un grupo "activo" que puede hacer todo menos cambiar el grupo propietario. Todos los demás grupos de permisos son derivados de "activo".

#### Evaluación Paralela de Permisos

El proceso de evaluación de permiso es "de sólo lectura" y los cambios en los permisos hechos por transacciones no hacen efecto hasta el final del bloque. Esto significa que todas las claves y evaluación de permisos para todas las transacciones pueden ser ejecutadas en paralelo. Además, esto significa que es posible la rápida validación del permiso sin iniciar la costosa lógica de aplicación que tendría que ser revertida. Por último, significa que los permisos de transacción pueden ser evaluados ya que se reciben transacciones pendientes y no es necesario reevaluarlos a medida que se aplican.

A fin de cuentas, la verificación de permisos representa un porcentaje significativo del cálculo requerido para validar las transacciones. Haciendo de esto un proceso de solo lectura y trivialmente paralelizable, permite un aumento dramático en el rendimiento.

Cuando se repite la cadena de blockchain para regenerar el estado determinista a partir del registro de mensajes, no hay necesidad de evaluar de nuevo los permisos. El hecho de que una transacción es incluída en un bloque conocido bueno, es suficiente para saltarse este paso. Esto reduce la carga computacional asociada con la repetición de un blockchain cada vez mayor.

#### Mensajes con Retardo Obligatorio

El tiempo es un componente crítico de la seguridad. En la mayoría de los casos, no es posible saber si una clave privada ha sido robada hasta que se haya utilizado. La seguridad basada en el tiempo es aún más crítica cuando las personas tienen las aplicaciones que requieren que las claves se mantengan en ordenadores conectados a internet para uso diario. El software EOS.IO habilita a los desarrolladores de aplicaciones indicar que ciertos mensajes deben esperar un período mínimo de tiempo después de haber sido incluidos en un bloque antes de que puedan ser aplicados. Durante este tiempo pueden cancelarse.

Los usuarios pueden entonces recibir un aviso por correo electrónico o por mensaje de texto cuando se emite uno de estos mensajes. Si no lo autorizan, pueden entonces utilizar el proceso de recuperación de cuentas para recuperar su cuenta y retirar el mensaje.

El retardo requerido depende de lo sensible que sea una operación. Pagar por un café no puede tener un retraso y puede ser irreversible en segundos, mientras que comprar una casa puede requerir un período de compensación de 72 horas. Transferir una cuenta entera a un nuevo control puede tardar hasta 30 días. Los retrasos exactos elegidos corresponden a los desarrolladores de aplicaciones y a los usuarios.

#### Recuperación de las Claves Robadas

El software EOS.IO proporciona a los usuarios una forma de restaurar el control de su cuenta cuando sus claves han sido robadas. El propietario de una cuenta puede utilizar cualquier clave de propietario que estuviese activa en los últimos 30 días junto con lo aprobación de su designado socio de recuperación de cuentas para restablecer la clave del propietario en su cuenta. El socio de recuperación de cuenta no puede restablecer el control de la cuenta sin la ayuda del propietario.

No hay nada que el hacker gane tratando de pasar por el proceso de recuperación porque ya "controlan" la cuenta. Además, si pasaran por el proceso, el socio de recuperación probablemente exigiría identificación y autenticación de múltiples factores \(teléfono y correo electrónico\). Esto probablemente comprometería al hacker o el hacker no ganaría nada en el proceso.

Este proceso es también muy diferente de un simple acuerdo de multi-firma. Con una transacción multi-firma, hay otra compañía que es parte de cada transacción que se ejecuta, pero con el proceso de recuperación el agente es solo parte del proceso de recuperación y no tiene poder sobre las transacciones diarias. Esto reduce drásticamente los costes y las responsabilidades legales de todos los involucrados.

### Ejecución Determinística Paralela de Aplicaciones

El consenso blockchain depende de la conducta determinista \(reproducible\). Esto significa que toda ejecución paralela debe de estar libre de uso de mutexes u otras primitivas de bloqueo. Sin seguros debe haber alguna manera de garantizar que todas las cuentas solo pueden leer y escribir su propia base de datos. También significa que cada cuenta procesa los mensajes secuencialmente y que el paralelismo estará a nivel de cuenta.

Utilizando el software EOS.IO, es el deber del productor de bloques organizar la entrega de mensajes en hilos de ejecución independientes para que puedan ser evaluados en paralelo. El estado de cada cuenta depende únicamente de los mensajes que se le envían. El programa es la salida de un productor de bloques y será ejecutado de forma determinista, pero el proceso para generar el programa no necesita ser determinista. Esto significa que los productores de bloques pueden utilizar algoritmos paralelos para programar transacciones.

Parte de la ejecución paralela significa que cuando un script genera un mensaje nuevo, no se entrega inmediatamente, sino que está programado para ser entregado en el siguiente ciclo. La razón por la que no se puede entregar inmediatamente es porque el receptor puede estar modificando activamente su propio estado en otro hilo de ejecución.

#### Minimizar la Latencia de las Comunicaciones

Latencia es el tiempo que tarda una cuenta en enviar un mensaje a otra cuenta y luego recibir una respuesta. El objetivo es habilitar que dos cuentas intercambien mensajes de un lado a otro dentro de un solo bloques sin tener que esperar 3 segundos entre cada mensaje. Para permitir esto, el software EOS.IO divide cada bloques en ciclos. Cada ciclo se divide en subprocesos y cada subproceso contiene una lista de transacciones. Cada transacción contiene un conjunto de mensajes para ser entregados. Esta estructura puede ser visualizada como un árbol donde las capas alternas se procesan secuencialmente y en paralelo.

Bloques

```text
Ciclos (secuencial)

  Hilos de ejecución o subprocesos (paralelo)

    Transacciones (secuencial)

      Mensajes (secuencial)

       Receptor y Cuentas Notificadas (paralelo) 
```

Las transacciones generadas en un ciclo pueden ser entregadas en cualquier ciclo posterior o bloque. Los productores de bloques seguirán añadiendo ciclos a un bloques hasta que haya transcurrido el tiempo máximo del reloj o que no hayan nuevas transacciones generadas para enviar.

Es posible utilizar el análisis estático de un bloque para verificar que dentro de un ciclo determinado no hay dos subprocesos que contengan transacciones que modifiquen la misma cuenta. Mientras que se mantenga ese invariante, se puede procesar un bloque ejecutando todos los subprocesos en paralelo.

#### Manejadores de Mensajes de Solo Lectura

Algunas cuentas pueden ser capaces de procesar un mensaje en una base de aprobado/fallado sin modificar su estado interno. Si este es el caso, entonces estos manejadores pueden ser ejecutados e n paralelo, siempre y cuando los manejadores de mensajes de solo-lectura para una cuenta particular se incluyan en uno o más subprocesos dentro de un ciclo particular.

#### Transacciones Atómicas con Cuentas Múltiples

A veces es conveniente asegurar que los mensajes son entregados y aceptados por múltiples cuentas de forma atómica. En este caso, ambos mensajes se colocan en una transacción y a ambas cuentas se les asignará el mismo subproceso y los mensajes se aplicarán secuencialmente. Esta situación no es ideal para el rendimiento, y cuando se trata de "facturar" a los usuarios por su uso, se les facturará por el número de cuentas únicas referenciadas por una transacción.

Por razones de rendimiento y costo, es mejor minimizar las operaciones atómicas que involucren dos o más cuentas altamente utilizadas.

#### Evaluación Parcial del estado del Blockchain

La escalada tecnología de blockchain necesita que los componentes sean modulares. Todo el mundo no debería de tener que ejecutar todo, especialmente si solo necesitan utilizar un pequeño subconjunto de las aplicaciones.

Un desarrollador de aplicaciones de intercambio ejecuta nódulos completos con el propósito de mostrar el estado de intercambio a sus usuarios. Esta aplicación de intercambio no tiene necesidad del estado asociado con las aplicaciones de redes sociales. El software EOS.IO permite que cualquier nódulo completo elija cualquier subconjunto de aplicaciones para ejecutarse. Los mensajes enviados a otras aplicaciones son ignorados con seguridad porque el estado de una aplicación se deriva totalmente de los mensajes que se le entregan.

* Esto tiene algunas implicaciones significativas en la comunicación con otras cuentas. Lo más importante es que no se puede suponer que el estado de la otra cuenta es accesible en la misma máquina. También significa que, aunque sea tentador habilitar "bloqueos" que permiten a una cuenta llamar de forma síncrona a otra cuenta, este patrón de diseño se avería si la otra cuenta no es residente en la memoria.

Toda comunicación de estado entre cuentas debe ser transmitida a través de mensajes incluidos en el blockchain.

#### Mejor Planificación Subjetiva del Esfuerzo

El software EOS.IO no puede obligar a los productores de bloques a entregar ningún mensaje a cualquier otra cuenta. Cada productor de bloques realiza su propia medición subjetiva de la complejidad computacional y del tiempo requerido para procesar una transacción. Esto se aplica si una transacción es generada por un usuario o automáticamente por un script.

El software EOS.IO proporciona que a nivel de red todas la transacciones se facturan un coste fijo de ancho de banda computacional independientemente de si tardó .01ms o un total de 10ms para ejecutarlo. Sin embargo, cada productor de bloques individual que utiliza el software puede calcular el uso de recursos utilizando su propio algoritmo y mediciones. Cuando un productor de bloques concluye que una transacción o cuenta ha consumido una cantidad desproporcionada de la capacidad computacional, simplemente rechaza la transacción al producir su propio bloque; sin embargo, seguirá procesando la transacción si otros productores de bloques la consideran válida.

En general, siempre y cuando un productor de bloques considere una transacción como válida y bajo los límites se uso de recursos, entonces todos los demás productores de bloques también lo aceptarán, pero puede tardar hasta un minuto para que la transacción encuentre a ese productor.

En algunos casos, un productor puede crear un bloque que incluya transacciones que sean de un orden de magnitud fuera de rangos aceptables. En este caso, el siguiente productor de bloques puede optar por rechazar el bloque y el empate se rompería por el tercer productor. Esto no es diferente de lo que ocurriría si un bloque grande causara retrasos en la propagación de la red. La comunidad se daría cuenta de un patrón de abuso y finalmente, eliminaría los votos del productor canalla.

Esta evaluación subjetiva del coste computacional libera al blockchain de tener que medir con precisión y determinismo cuánto tiempo tarda algo en ejecutarse. Con este diseño no hay necesidad de contar con precisión las instrucciones que aumenta dramáticamente las oportunidades de optimización sin romper el consenso.

### Modelo de Token y Uso de Recursos

Todos los blockchains están limitados por recursos y requieren un sistema para prevenir el abuso. Con el software EOS.IO, hay tres clases amplias de recursos que son consumidos por las aplicaciones:

Ancho de Banda y Almacenamiento de Registros \(Disk\);  
Computación y Backlog Computacional \(CPU\); y  
Almacenamiento de Estado \(RAM\).

El ancho de banda y la computación tienen dos componentes, el uso instantáneo y el uso a largo plazo. Un blockchain mantiene un registro de todos los mensajes y este registro es finalmente almacenado y descargado por todos los nódulos completos. Con el registro de los mensajes es posible reconstruir el estado de todas las aplicaciones.

La deuda computacional es un cálculo que debe realizarse para regenerar el estado desde el registro de mensajes. Si la deuda computacional crece demasiado entonces es necesario tomar instantáneas del estado del blockchain y descartar la historia del blockchain. Si la deuda computacional crece demasiado rápido entonces puede tardar 6 meses para reproducir el valor de 1 año de transacciones. Es crítico, por lo tanto, la deuda computacional debe ser manejada cuidadosamente.

El almacenamiento de estado de blockchain es información que es accesible desde la lógica de la aplicación. Incluye información como libros de pedidos y saldos de cuentas. Si el estado nunca es leído por la aplicación, entonces no debe ser almacenado. Por ejemplo, el contenido de la publicación de blog y los comentarios, no son leídos por la lógica de la aplicación por lo que no deberían de almacenarse en el estado del blockchain. Mientras tanto, la existencia de una publicación/comentario, el número de votos y otras propiedades se almacenan como parte del estado del blockchain.

Los productores de bloques publican su capacidad disponible de ancho de banda, computación y estado. El software EOS.IO permite que cada cuenta consuma un porcentaje de la capacidad disponible proporcional a la cantidad de tokens mantenidos en un contrato de inversión de 3 diás. Por ejemplo, si se lanza un blockchain basado en el software EOS.IO y si una cuenta contiene el 1% del total de tokens distribuibles de acuerdo con esa cadena de blockchain, entonces esa cuenta tiene el potencial de utilizar el 1% de la capacidad de almacenamiento del estado.

Utilizando el software EOS.IO, el ancho de banda y la capacidad computacional se asignan sobre una base de reserva fraccionada porque son transitorios \(la capacidad no utilizada no puede ser guardada para uso posterior\). El algoritmo utilizado por EOS.IO es similar al algoritmo utilizado por Steem para limitar el uso del ancho de banda.

#### Medidas Objetivas y Subjetivas

Como se comentó anteriormente, la instrumentación del uso computacional tiene un impacto significativo en el rendimiento y la optimización; por lo tanto, todas las coacciones de uso de recursos son fundamentalmente subjetivas y es ejecutado por los productores de bloques de acuerdo con sus algoritmos y estimaciones individuales.

Dicho esto, hay ciertas cosas que son triviales para medir objetivamente. El número de mensajes entregados y el tamaño de los datos almacenados en la base de datos interna son fáciles de medir objetivamente. El software EOS.IO permite a los productores de bloques aplicar el mismo algoritmo sobre estas medidas objetivas pero pueden optar por aplicar algoritmos subjetivos más estrictos sobre las mediciones subjetivas.

#### El Receptor Paga

Tradicionalmente, es la empresa que paga por el espacio de oficina, la potencia computacional y otros costes necesarios para administrar el negocio. El cliente compra productos específicos de la empresa y los ingresos de esas ventas de productos se usan para cubrir gastos de operación de la empresa. Similarmente, ninguna página web obliga a sus visitantes a hacer micropagos por visitar su página web para cubrir sus gastos de alojamiento. Por lo tanto, las aplicaciones descentralizadas no deben forzar a sus clientes a pagar el blockchain directamente para el uso del blockchain.

El software EOS.IO no requiere que sus usuarios paguen directamente al blockchain por su uso y por lo tanto, no restringe o impide que una empresa determine su propia estrategia de monetización para sus productos.

#### Delegación de Capacidad

Si se lanza un blockchain utilizando el software EOS.IO y los tokens están en poder de un titular que puede no tener una necesidad inmediata de consumir todo o parte del ancho de banda disponible, dicho titular puede optar por dar o alquilar el ancho de banda sin consumir a otros; los productores de bloques que ejecutan el software EOS.IO reconocerán esta delegación de capacidad y asignarán el ancho de banda como corresponde.

#### Separar los costos de Transacción por Valor de Token

Uno de los principales beneficios del software EOS.IO es que la cantidad de ancho de banda disponible para una aplicación es totalmente independiente de cualquier precio del token. Si un propietario de aplicación tiene un número relevante de tokens, entonces la aplicación puede ejecutarse indefinidamente dentro de un estado fijo y el uso de ancho de banda. Los desarrolladores y los usuarios no se ven afectados por cualquier volatilidad de los precios en el mercado de tokens, y por lo tanto no dependen de un precio de alimentación. El software EOS.IO habilita a los productores de bloques aumentar naturalmente el ancho de banda, la computación y almacenamiento disponibles por tokens, independientemente del valor del token.

El software EOS.IO premia a los productores de bloques cada vez que producen el bloque. El valor de los tokens afectará la cantidad de ancho de banda, almacenamiento y computación que un productor pueda permitirse comprar; este modelo aprovecha naturalmente los valores crecientes del token para aumentar el rendimiento de la red.

#### Costes de Almacenamiento del Estado

Mientras que el ancho de banda y la computación pueden ser delegados, el almacenamiento del estado de la aplicación requerirá que un desarrollador de aplicaciones tenga tokens hasta que se elimine ese estado. Si el estado nunca se elimina entonces los tokens serán eliminados efectivamente de la circulación.

Cada cuenta de usuario requiere una cierta cantidad de almacenamiento; por lo tanto, cada cuenta debe mantener un saldo mínimo. A medida que aumenta la capacidad de almacenamiento de la red, este saldo mínimo requerido disminuirá.

#### Recompensas por el bloque.

El software EOS.IO premia nuevos tokens a un productor de bloques cada vez que se produce un bloque. El número de tokens creados está determinado por la mediana de la paga deseada publicada para todos los usuarios de bloques. El software EOS.IO puede configurarse para imponer una limitación de los premios a los productores, de modo que el incremento anual total en el suministro de tokens no supere el 5%.

#### Aplicaciones de Beneficios Comunitarios

Además de elegir a los productores de bloques, basado en el software EOS.IO, los usuarios pueden elegir 3 aplicaciones de beneficio comunitario también conocidos como contratos inteligentes. Estas 3 aplicaciones recibirán tokens de hasta un porcentaje configurado del suministro de tokens por año menos los tokens que se han pagado a los productores de bloques. Estos contractos inteligentes recibirán tokens proporcionales a los votos que cada aplicación ha recibido de los titulares de tokens. Las aplicaciones elegidas o los contratos inteligentes pueden ser reemplazados por aplicaciones recién elegidas o contratos inteligentes por titulares de tokens.

### Gobernación

La gobernación es el proceso por el cual la gente alcanza el conseso en asuntos subjetivos que no pueden ser completamente capturados por algoritmos del software. El software EOS.IO implementa un proceso de gobernación que dirige eficientemente la influencia existente de los productores de bloques. A falta de un proceso de gobernación definido, los blockchains anteriores se basaban en ad hoc, informal, y a menudo polémicos procesos de gobernación que resultaron en consecuencias impredecibles.

El software EOS.IO reconoce que el poder se origina con los titulares de tokens que delegan ese poder a los productores del bloques. A los productores de bloques se les da autoridad limitada y controlada para congelar cuentas, actualizar aplicaciones defectuosas, y proponer cambios duros de bifurcación al protocolo subyacente.

Parte del software EOS.IO es la elección de productores de bloques. Antes de que se pueda hacer cualquier cambio al blockchain, estos productores de bloques deben aprobarlo. Si los productores del bloques se niegan a hacer cambios deseados por los titulares de tokens, entonces pueden ser eliminados. Si los productores de bloques realizan cambios sin el permiso de los titulares de tokens, entonces todos los demás validadores no productores de nódulos completos \(intercambios, etc.\) rechazarán el cambio.

#### Bloqueo de Cuentas

A veces un contracto inteligente se comporta de manera aberrante o impredecible y deja de funcionar como era previsto; otras veces, una aplicación o cuenta puede descubrir un exploit que le permite consumir una cantidad inaceptable de recursos. Cuando ocurren inevitablemente estos problemas, los productores de bloques tienen el poder de rectificar tales situaciones.  
Los productores de bloques en todos los blockchains tienen el poder de seleccionar qué transacciones se incluyen en bloques que les da la habilidad de bloquear cuentas. El software EOS.IO formaliza esta autoridad al someter el proceso de bloqueo de una cuenta a 17/21 votos de productores activos. Si los productores abusan del poder, pueden ser eliminados y una cuenta será desbloqueada.

#### Cambio de Código de la Cuenta

Cuando todo lo demás falla y una "aplicación imparable" actúa de una manera impredecible, el software EOS.IO permite a los productores de bloques reemplazar el código de la cuenta sin bifurcar el blockchain completo. Al igual que el proceso de bloqueo de una cuenta, esta sustitución del código requiere un 17/21 votos de los productores de bloques elegidos.

#### Constitución

El software EOS.IO habilita a blockchains establecer un acuerdo de términos de servicio peer to peer o un contrato vinculante entre los usuarios que lo firman, denominado "constución". El contenido de esta constitución define las obligaciones entre los usuarios que no pueden ser completamente aplicadas por código y facilita la resolución de disputas mediante el establecimiento de la jurisdicción y ley de preferencia junto con otras reglas mutuamente aceptadas. Cada transacción difundida en la red debe incorporar el hash de la constitución como parte de la firma y de este modo vincula explícitamente el firmante al contrato.

La constitución también define la intención legible por el ser humano del protocolo del código fuente. Esta intención se utiliza para identificar la diferencia entre un error y una característica cuando ocurren errores y guía a la comunidad sobre qué arreglos son apropiados o inapropiados.

#### Actualización del Protocolo y Constitución

El software EOS.IO define un proceso mediante el cual se puede actualizar el protocolo definido por el código fuente canónico y su constitución, mediante el siguiente proceso:

Los productores de bloques proponen un cambio a la constitución y obtienen la 17/21 de aprobación.  
Los productores de bloques mantienen la 17/21 de aprobación durante 30 días consecutivos.  
Todos los usuarios deben firmar las transacciones utilizando el hash de la nueva constitución.  
Los productores de bloques adoptan cambios en el código fuente para reflejar el cambio en la constitución y lo proponen al blockchain utilizando el hash de un git commit.  
Los productores de bloques mantienen la 17/21 de aprobación durante 30 días consecutivos.  
Los cambios en el código hacen efecto 7 días más tarde, dándole a todos los nódulos completos 1 semana para actualizarse después de la ratificación del código fuente.  
Todos los nódulos que no se actualizan al nuevo código, dejan de funcionar automáticamente.

Por la configuración predeterminada del software EOS.IO, el proceso de actualización del blockchain para añadir nuevas características tarda de 2 a 3 meses, mientras que las actualizaciones para corregir errores no críticos que no requieren cambios en la constitución pueden tardar de 1 a 2 meses.

#### Cambios Urgentes

Los productores de bloques pueden acelerar el proceso si se requiere un cambio de software para arreglar un error dañino o un exploit de seguridad que está activamente dañando a los usuarios. Generalmente hablando, podría estar en contra de la constitucion para que las actualizaciones aceleradas introduzcan nuevas características o arreglar errores inofensivos.

### Scripts y Máquinas Virtuales

El software EOS.IO será ante todo una plataforma para coordinar la entrega de mensajes autenticados a las cuentas. Los detalles del lenguaje de script y de la máquina virtual son detalles específicos de la implementación que en su mayoría son independientes del diseño de la tecnología EOS.IO. Cualquier lenguaje o máquina virtual que sea determinista y con un entorno de seguridad adecuado con un rendimiento suficiente puede integrarse con API del software EOS.IO.

#### Mensajes Definidos por Esquemas

Todos los mensajes enviados entre cuentas se definen mediante un esquema que forma parte del estado de consenso de blockchain. Este esquema permite la conversión sin interrupciones entre la representación binaria y JSON de los mensajes.

#### Base de Datos Definidos por Esquemas

El estado de la base de datos también se define utilizando un esquema similar. Esto asegura que todos los datos almacenados por todas la aplicaciones estén en un formato que puedan ser interpretado como JSON legible por el hombre, pero almacenado y manipulado con la eficiencia del binario.

#### Separando Autenticación de la Aplicación

Para maximizar las oportunidades de paralelización y minimizar la deuda computacional asociada con la regeneración del estado de la aplicación desde el registro de transacciones, EOS.IO separa la lógica de validación en tres secciones:

Validar que un mensaje es internamente consistente;  
Validar que todas las precondiciones son válidas; y  
Modificar el estado de la aplicación.

La validación de la consistencia interna de un mensaje es de solo lectura y no requiere acceso al estado de blockchain. Esto significa que puede realizarse con el máximo paralelismo. La validación de las condiciones previas, como el equilibrio requerido, es de solo lectura y por lo tanto, también puede beneficiarse del paralelismo. La única modificación del estado de la aplicación requiere acceso de escritura y debe procesarse secuencialmente para cada aplicación.

La autenticación es el proceso de sólo lectura para verificar que se puede aplicar un mensaje. La aplicación realmente está haciendo el trabajo. Se requiere realizar ambos cálculos en tiempo real, sin embargo, una vez que se incluye una transacción en el blockchain, ya no es necesario realizar las operaciones de autenticación.

### Virtual Machine Independent Architecture

Es la intención del software EOS.IO que múltiples máquinas virtuales puedan ser compatibles y añadir nuevas máquinas virtuales con el tiempo según sea necesario. Por esta razón, este documento no discutirá los detalles de ningún lenguaje en particular o máquina virtual. Dicho esto, hay dos máquinas virtuales que se están evaluando actualmente para su uso dentro del EOS.IO.

#### Web Assembly \(WASM\)

Web Assembly es un emergente patrón de web para crear aplicaciones web de alto rendimiento. Con algunas pequeñas modificaciones, el Web Assembly se puede hacer determinista y en condiciones de seguridad. El beneficio del Web Assembly es el amplio apoyo de la industria y permite que los contratos se desarrollen en lenguajes familiares como C o C ++.  
Los desarrolladores de Ethereum ya han comenzado a modificar el Web Assembly para proporcionar las condiciones adecuadas de seguridad y deteminismo en el Ethereum del Web Assembly \(WASM\). Esta estrategia puede ser fácilmente adaptada e integrada con el software EOS.IO.

#### Ethereum Virtual Machine \(EVM\)

Esta máquina virtual se ha utilizado para la mayoría de los contratos inteligentes existentes y podría adaptarse para funcionar dentro de un blockchain EOS.IO. Es concebible que los contratos de EVM se pueden ejecutar dentro de su propia configuración de seguridad dentro de un blockchain EOS.IO y que con alguna adaptación los contratos de EVM podrían comunicarse con otras aplicaciones blockchain de EOS.IO.

### Comunicación Inter-Blockchain

El software EOS.IO está diseñado para facilitar la comunicación inter-blockchain. Esto se consigue facilitando la generación de pruebas de existencia de mensajes y la prueba de secuencia de mensajes. Estas pruebas combinadas con una arquitectura de aplicación diseñada en torno al envío de mensajes permiten que los detalles de la comunicación inter-blockchain y la validación de pruebas, se oculten de los desarrolladores de aplicaciones.  
![](https://steemitimages.com/0x0/http://eos.io/wpimg/Diagram1.jpg)

#### Merkle Proofs for Light Client Validation \(LCV\)

La integración con otros blockchains es mucho más fácil si los clientes no necesitan procesar todas las transacciones. Después de todo, un intercambio sólo se preocupa por las transferencias dentro y fuera del intercambio, y nada más. También sería ideal si la cadena de intercambio pudiera utilizar lightweight merkle proofs de depósito en lugar de tener que confiar completamente en sus propios productores de bloques. Como mínimo, los productores de bloques desearían mantener la menor sobrecarga posible al sincronizar con otros blockchains.

El objetivo de LCV es permitir la generación relativa de light-weight proof of existence que puede ser validada por cualquier persona que sigue una relativa light-weight data set. En este caso, el objetivo es demostrar que una transacción particular fue incluída en un bloques particular y que el bloque está incluido en el historial verificado de un blockchain particular.

Bitcoin admite la validación de transacciones asumiendo que todos los nódulos tienen acceso al historial completo de los encabezados de bloques, lo que equivale a 4MB de encabezados de bloques por año. A 10 transacciones por segundo, una prueba válida requiere unos 512 bytes. Esto funciona bien para un blockchain con un intervalo de bloques de 10 minutos, pero ya no es "light" para blockchains con un intervalo de bloques de 3 segundos.

El software EOS.IO permite lightweight proofs para cualquier persona que tenga un encabezado del bloque irreversible después del punto en el que se había incluido la transacción. Usando la estructura de hash-linked mostrada abajo, es posible demostrar la existencia de cualquier transacción con una prueba de menos de 1024 bytes de tamaño. Si se supone que los nódulos de validación están siguiendo el ritmo de todos los encabezados de bloques en el día \(2MB de datos\), entonces muestra que estas transacciones solo requerirán pruebas de 200 bytes de largo.

Hay poca sobrecarga incremental asociada con la producción de bloques con la adecuada hash-linking para habilitar estas pruebas lo que significa que no hay razón para generar bloques de esta manera.

Cuando llega el momento de validar pruebas en otras cadenas hay una gran variedad de optimizaciones de tiempo/espacio/ancho de banda que se pueden hacer. El seguimiento de todos los encabezados de bloques \(420MB/año\) mantendrá los tamaños de prueba pequeños. El seguimiento de solo encabezados recientes puede ofrecer una compensación entre el mínimo almacenamiento a largo plazo y el tamaño de la prueba. Alternativamente, un blockchain puede usar un enfoque de evaluación donde recuerda los los hashes intermedios de las pruebas pasadas. Las pruebas nuevas solo tienen que incluir enlaces al sparse tree conocido. El enfoque exacto utilizado dependerá necesariamente del porcentaje de bloques externos que incluyan transacciones referenciadas por prueba merkle.

Después de una cierta densidad de interconexión se vuelve más eficiente simplemente tener una cadena que contenga todo el historial de bloques de otra cadena y en conjunto eliminar la necesidad de pruebas. Por razones de rendimiento, es ideal minimizar la frecuencia de pruebas inter-cadena.

#### Latencia de Comunicación Interchain

Cuando se comunica con un blockchain externo, los productores de bloques deben esperar hasta que haya una certeza del 100% de que una transacción ha sido confirmada irreversiblemente por el otro blockchain antes de aceptarla como entrada válida. Utilizando el software EOS.IO y DPOS con bloques de 3 segundos y 21 productores, esto tarda aproximadamente 45 segundos. Si los productores de bloques de una cadena no esperan a la irreversibilidad, sería como un intercambio que acepta un depósito que luego fue revertido y podría afectar la validez del consenso de una cadena.

#### Prueba de Completitud

Cuando se usan merkle proofs de blockchains externos, hay una diferencia significativa entre saber que todas las transacciones procesadas son válidas y saber que ninguna transacción ha sido saltada u omitida. Mientras que es imposible demostrar que se conocen todas las transacciones más recientes, es posible demostrar que no han habido interrupciones en el historial de transacciones. El software EOS.IO facilita esto asignando un número de secuencia a cada mensaje entregado a cada cuenta. Un usuario puede usar estos números de secuencia para demostrar que todos los mensajes destinados a una cuenta en particular han sido procesados y que fueron procesados en orden.

### Conclusión

El software EOS.IO está diseñado por experiencia con conceptos comprobados y por las mejores prácticas, y representa los avances fundamentales en la tecnología blockchain. El software es parte de un proyecto holístico para una sociedad de blockchain globalmente expansible en la que las aplicaciones descentralizadas pueden ser fácilmente implementadas y gobernadas.

Fuente original: [https://steemit.com/eos/@eosio/eos-io-technical-white-paper](https://steemit.com/eos/@eosio/eos-io-technical-white-paper)

