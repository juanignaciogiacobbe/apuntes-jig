> [!IMPORTANT] Canales
> Conectan un proceso emisor con un proceso receptor. Son sincronicos o asincronicos.
> Tienen un nombre, son tipados y unidireccionales.

![](Programación%20Concurrente/img%20concu/Pasted%20image%2020241004161230.png)


> [!IMPORTANT] Selective Input
> Es una sintaxis permitida por los lenguajes que soportan canales.
> Permite escuchar en varios canales de forma bloqueante y desbloquearse con el primero que recibe un mensaje.



> [!IMPORTANT] Remote Procedure Calls
> Permiten al cliente ejecutar funciones en un servidor localizado en otro procesador.
> - Se requiere la implementación de stubs en ambos extremos.
> - Los stubs conforman interfaces remotas utilizadas para compilar cliente y servidor.
> - Localización de servicios.
> - Parameter marshalling.


> [!WARNING] Diferencia con otros modelos de concurrencia
> "Do not communicate by sharing memory; instead, share memory by communicating" -> Básicamente con este modelo compartimos datos, y así nos comunicamos.


> [!IMPORTANT] Canales en Unix
> Unix provee Pipes y FIFOs para conectar dos procesos independientes, orientados a bytes.
> 	- Los FIFOs poseen una representación en el [File System](Sistemas%20Operativos/File%20System.md).
> Unix también provee colas de mensajes orientados a mensajes como unidades independientes.


## Canales en Rust
- Un canal tiene dos extremos: un emisor y un receptor.
- Una parte del código invoca métodos sobre el transmisor, con los datos que se quiere enviar.
- Otra parte chequea el extremo de recepción por la existencia de mensajes.
- Multiples productores, un consumidor.
- Transfieren el ownership del elemento enviado.
- Para crear multiples productores, se clona el extremo de envío.

![](Programación%20Concurrente/img%20concu/Pasted%20image%2020241004162039.png)