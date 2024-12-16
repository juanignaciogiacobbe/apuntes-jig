# The PPP Triple-DES Encryption Protocol(3DESE)
[Link al trabajo](https://www.rfc-editor.org/rfc/rfc2420.html)  

## Introducción

### The Point-to-Point Protocol(PPP)
- Es un estándar para transportar datagramas a través de enlaces punto a punto. Está diseñado para enlaces sencillos que transportan paquetes entre dos pares, proporcionando un funcionamiento full-duplex, suponiendo que los paquetes se entregan en orden. Este protocolo se basa en 3 componentes principales:
- **Encapsulación**: Permite multiplexar múltiples protocolos de red simultáneamente en el mismo enlace.
- **Protocolo de Control de Enlace (LCP)**: Para acordar automáticamente opciones de formato de encapsulación, manejar límites de tamaño de paquetes, detectar errores comunes de configuración, y cerrar el enlace cuando sea necesario.
- **Protocolos de Control de Red (NCP)**: Los enlaces punto a punto presentan desafíos, como la asignación de direcciones IP. PPP resuelve estos problemas con NCPs específicos para cada protocolo de capa de red, que manejan sus necesidades específicas.

### PPP Encryption Protocol(ECP)
ECP permite que dos extremos de un enlace PPP negocien y habiliten algoritmos de cifrado para garantizar la privacidad de los datos en ambos extremos. Tiene las siguientes características:
1. **Negociación de Cifrado**: Antes de iniciar la transmisión cifrada, ambos extremos del enlace deben negociar un algoritmo de cifrado que ambos puedan usar. ECP funciona de manera similar a LCP para esta fase de la comunicación. Los extremos pueden acordar un único algoritmo o cancelar la conexión si no logran ponerse de acuerdo.
3. **Envío de Datos Cifrados**: Una vez que ECP completa la negociación, los datos se cifran y se encapsulan en el campo de información de PPP, asegurándose que solo el extremo receptor pueda descifrar y leer los datos.
4. **Detección de Fallos de Descifrado**: ECP incluye paquetes especiales llamados "Reset-Request" y "Reset-Ack" que ayudan a sincronizar y restablecer el cifrado en caso de errores de descifrado, sin interrumpir el flujo de datos en la otra dirección.


## Algoritmo DES
- Lo usamos para proteger datos transmitidos entre dos implementaciones de PPP. Nos provee un método estandarizado para cifrar datos en enlaces PPP debido a su implementación eficiente en hardware y su amplio uso.
- Utiliza el modo Cipher Block Chaining(CBC) para encriptar los datos.
- ECP permite utilizar este algoritmo.
- El algoritmo de encriptado funciona de la siguiente forma: Se toma un paquete de datos PPP, y se agrega un elemento de aleatoriedad usando un llamado Vector de Inicialización (IV) y un número de secuencia de 16 bits(esto es para asegurar el orden de llegada de los paquetes). Para encriptar usamos una clave de 56 bits, pero como el protocolo opera con bloques de 8 Bytes, agregamos un padding para completar los 64 bits.
- Para encriptar, la idea es dividir el texto plano a encriptar en bloques de 8 Bytes. Se toma al primer bloque, se le hace un XOR contra el vector de inicialización, y luego se encripta contra la clave de 56 bits. Para el siguiente bloque del texto original, se toma el primer bloque cifrado, y ahora va a hacer de "vector de inicialización": se hace un XOR entre ambos, y luego se encripta contra la clave. El proceso sigue hasta terminar de encriptar la cadena completa.
- Para desencriptar, hacemos el mismo proceso de encriptado, pero al revés: Desciframos con DES el bloque, y luego hacemos un XOR con el bloque anterior.

![](Pasted%20image%2020241114140417.png)

### The PPP Triple-DES Encryption Protocol(3DESE)

- Se basa en el algoritmo de cifrado DES, pero aumenta la seguridad aplicándolo tres veces. En este contexto, el protocolo especifica la implementación del modo **DES-EDE3-CBC** (Encipher-Decrypt-Encipher en modo de encadenamiento de bloques), una variante de DES que combina tres claves independientes y el modo de operación de CBC (Cipher Block Chaining, antes visto).
- Seguimos manteniendo la misma estructura propuesta por el algoritmo DES, pero ahora vamos a necesitar 3 claves de cifrado(siguen siendo de 56 bits cada una).
- Nos permite recuperarnos fácilmente ante la pérdida de paquetes: El número de secuencia en cada paquete permite identificar cualquier discontinuidad y detectar paquetes perdidos.
	- Si un paquete se pierde, los paquetes siguientes pueden descifrarse correctamente, ya que el proceso Triple-DES CBC solo necesita el último bloque de texto cifrado del paquete anterior para descifrar el siguiente.



## Consideraciones de Seguridad
- **Confidencialidad Únicamente**: Esta especificación se centra exclusivamente en la confidencialidad de los datos transmitidos. No ofrece protección adicional para asegurar la integridad, autenticación o no repudio de los mensajes.
- **Ausencia de Protección Contra Manipulación**: No garantiza que los mensajes no hayan sido modificados durante el tránsito. Esto significa que podrían estar sujetos a ataques como la repetición (replay), la manipulación de fragmentos del mensaje (cut-and-paste) o incluso alteraciones activas.
- **Sin Autenticación del Origen**: No se proporciona un método para verificar la identidad del emisor de cada paquete, ni para proteger contra situaciones en las que el emisor niegue haber enviado un mensaje.
- **Dependencia de Métodos Externos para la Gestión de Claves**: La propuesta no especifica un mecanismo para la distribución o protección de secretos compartidos (claves). Esto debe ser manejado externamente, fuera del alcance de este protocolo.
- **Limitaciones del Algoritmo 3DES**: Cualquier vulnerabilidad inherente al cifrado Triple-DES (3DES) impactará la seguridad de esta implementación. La especificación no propone nuevas tecnologías de privacidad, sino que describe cómo aplicar el cifrado 3DES en las comunicaciones entre implementaciones de PPP.