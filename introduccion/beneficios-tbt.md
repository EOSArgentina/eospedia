# Beneficios

## Soporte para Millones de Usuarios

Competir con negocios como eBay, Uber, AirBnB, y Facebook, requiere una tecnología de cadena de bloques capaz de manejar diariamente decenas de millones de usuarios activos. En ciertos casos, una aplicación puede no tener utilidad a menos que alcance una masa crítica de usuarios y por lo tanto, una plataforma que pueda manejar una gran cantidad de usuarios es requerida.

A través de la escala horizontal, EOSIO habilitará una red capaz de soportar millones de usuarios en aplicaciones de alta performance.

## Uso Gratuito

Tradicionalmente, los negocios son los que pagan por espacios de oficinas, poder de cómputo, y otros costos necesarios para operar un negocio. Los clientes compran productos específicos del negocio y la ganancia de esas ventas de productos es usada para cubrir los costos de operación. De manera similar, ningún sitio web obliga a sus visitantes a realizar micropagos al visitar el sitio para cubrir costos de mantenimiento.

Los desarrolladores de aplicaciones necesitan la flexibilidad para poder ofrecer a sus usuarios servicios gratuitos; los usuarios no deberían pagar para usar la plataforma o beneficiarse de sus servicios. Una plataforma de cadena de bloques de uso gratuito para sus usuarios es más propensa a lograr una mayor adopción. Desarrolladores y negocios pueden crear entonces estrategias de monetización efectivas.

Una cadena de bloques productiva que usa el software de EOSIO no requiere que sus usuarios paguen a la cadena de bloques de manera directa para usarla y por lo tanto, no limita o evita que un negocio determine su propia estrategia de monetización de sus productos.

Mientras que es verdad que el receptor puede pagar, EOSIO permite que el emisor pague por el ancho de banda, poder de cómputo y almacenamiento. Esto le da el poder a los desarrolladores de aplicaciones para seleccionar el método que mejor le siente a su aplicación. En muchos casos el pago por parte del emisor reduce muchísimo la complejidad para los desarrolladores que no quieren implementar su propio sistema de racionamiento. Los desarrolladores de aplicaciones pueden delegar ancho de banda y poder de cómputo a sus usuarios y luego dejar que el modelo de "pago por parte del emisor" imponga su uso. Desde la perspectiva del usuario final esto es gratuito, pero desde la perspectiva de la cadena de bloques el que paga es el emisor.

## Actualización Simple y Recuperación de Errores

Los negocios que construyen aplicaciones basadas en cadena de bloques necesitan la flexibilidad para mejorar sus aplicaciones con nuevas funcionalidades. La plataforma debe soportar actualizaciones en el software y en los contratos inteligentes.

Cualquier software no trivial está sujeto a errores, inclusive con la más rigurosa verificación formal. La plataforma tiene que ser lo suficientemente robusta para corregir errores cuando estos inevitablemente ocurren.

Cuando todo lo demás falla y una "aplicación imparable" actúa de una forma inesperada, una cadena de bloques que usa el software de EOSIO permite que los productores de bloques reemplacen el código de la cuenta sin tener que realizar un hard fork de toda la cadena de bloques. De manera similar al caso de congelar una cuenta, este reemplazo de código requiere una votación de por lo menos 15 de los 21 votos de los productores de bloques elegidos.

## Baja Latencia

Una buena experiencia de usuario requiere una respuesta confiable con una demora de no más que unos segundos. Demoras prolongadas frustan a los usuarios y hacen que las aplicaciones construidas sobre cadenas de bloques sean menos competitivas que las alternativas existentes que no corren sobre cadenas de bloques. La plataforma debe soportar transacciones con baja latencia.

Con bloques producidos por debajo de un segundo, EOSIO minimiza la latencia de las transacciones y mejora drásticamente la experiencia de usuario en las aplicaciones que corren sobre ella.

## Performance Secuencial

Algunas aplicaciones no pueden ser implementadas con algoritmos paralelos por la naturaleza secuencial de sus pasos dependientes. Aplicaciones tales como exchanges necesitan suficiente performance secuencial para manejar altos volúmenes.

EOSIO está construido para soportar una veloz performance secuencial satisfaciendo los requerimientos de aplicaciones de alta performance.

## Nombres de Cuenta de Fácil Lectura

El software de EOSIO permite que todas las cuentas sean referenciadas por un nombre único de fácil lectura de hasta 12 caracteres de longitud. El nombre es elegido por el creador de la cuenta.

## Constitución

El software de EOSIO permite a las cadenas de bloques establecer un acuerdo de términos de servicio entre pares o contratos entre aquellos usuarios que firman la "constitución". El contenido de esta constitución define obligaciones entre los usuarios que no pueden ser completamente aplicadas a través de código y facilita la resolución de disputas estableciendo una jurisdicción y la elección de las leyes junto con otras reglas aceptadas mutuamente. Cada transacción transmitida a la red debe incorporar el hash de la constitución como parte de la firma y de esa manera explícitamente obligan al firmante a cumplir con el contrato.

La constitución también define la declaración de la intención del código fuente en un formato de texto legible. Esta documentación de la intención es usada para diferenciar entre un error y una funcionalidad cuando un error ocurre y sirven como guía para que la comunidad sepa que correcciones son correctas o incorrectas.

## Comunicación Entre Cadenas de Bloques

El software de EOS.IO está diseñado para facilitar la comunicación entre cadenas de bloques. Esto es logrado haciendo que sea simple generar una prueba de la existencia de una Acción y de la prueba de una secuencia de Acciones. Estas pruebas combinadas con una arquitectura de aplicación diseñada alrededor del pasaje de Acciones permite que los detalles de la comunicación entre cadenas de bloques y pruebas de validación se encuentren ocultas para los desarrolladores de aplicaciones, permitiendo presentar a los desarrolladores un alto nivel de abstracción.

