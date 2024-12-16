
> [!IMPORTANT] Actor
> Es la primitiva principal del modelo. Son livianos, se pueden crear miles(en lugar de threads), encapsulan comportamiento y estado.
> El actor supervisor puede crear otros actores hijos.
> Esta compuesto por:
> - **Dirección**: A donde enviarle mensajes.
> - **Casilla de correo(mailbox)**: Un FIFO de los últimos mensajes recibidos.

![](Programación%20Concurrente/img%20concu/Pasted%20image%2020241004162414.png)

> [!WARNING] Más características de los Actores
> - Son aislados de otros actores -> No comparten memoria.
> - El estado privado solo puede cambiarse a partir de procesar mensajes.
> - Pueden manejar un mensaje por vez.
> - En un sistema distribuido, la dirección del actor puede ser una dirección remota.


> [!IMPORTANT] Mensajes
> Son estructuras simples inmutables.
> Los actores se comunican entre ellos solamente usando mensajes.
> Los mensajes son procesados por los actores de forma asincronica.


> [!IMPORTANT] Arbiter
> Provee el contexto de ejecución asincrónica para los actores, funciones y futures.
> Alojan el entorno donde se ejecuta el actor.
> Crean un nuevo thread del SO, ejecutan un event loop, y crean tareas asincrónicas en ese event loop.
