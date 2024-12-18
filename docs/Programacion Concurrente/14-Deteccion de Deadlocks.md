
!!! note "Deadlocks"
> Cuando dos o más procesos o hilos en un sistema no pueden continuar con su ejecución, debido a que cada uno de ellos se queda esperando a que otro libere un recurso que necesita. Aquí se genera un ciclo, ya que los procesos no pueden avanzar: Cada uno está esperando a que el otro libere el recurso requerido. Para que se produzca un deadlock tienen que cumplirse los siguientes 4 requisitos:

- Exclusión Mutua: Al menos un recurso debe ser retenido en modo exclusivo por un proceso en un momento dado.
- Espera y Retención: Un proceso debe retener al menos un recurso mientras espera la adquisición de recursos adicionales que actualmente están siendo retenidos por otros.
- No liberación voluntaria: Un proceso no puede liberar voluntariamente los recursos que tiene en su posesión.
- Espera circular: Debe haber una cadena circular de dos o más procesos, cada uno de los cuales están esperando un recurso que posee el siguiente proceso en la cadena.

## Algoritmos de Detección de Deadlocks


!!! note "Algoritmo Centralizado"
> - El proceso coordinador mantiene el grafo de uso de recursos.
> - Los procesos envian mensajes al coordinador cuando obtienen o liberan un recurso y el coordinador actualiza el grafo.
> - El problema esta en que los mensajes pueden llegar desordenados y generar falsos deadlocks. -> Se pueden utilizar timestamps globales para ordenar los mensajes(algoritmo de Lamport).



!!! note "Algoritmo Distribuido"
> - Cuando un proceso debe esperar por un recurso, envía un `probe message` al proceso que tiene el recurso. El mensaje contiene: id del proceso que se bloquea, id del proceso que envía el mensaje y id del proceso destinatario. 
> - Al recibir el mensaje, el proceso actualiza el id del proceso que envía y el id del destinatario y lo envía a los procesos que tienen el recurso que necesita.
> - Si el mensaje llega al proceso original, tenemos un ciclo en el grafo. -> Un deadlock.
