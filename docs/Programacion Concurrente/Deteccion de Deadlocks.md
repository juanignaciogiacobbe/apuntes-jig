## Algoritmos de Detección de Deadlocks


!!! note "Algoritmo Centralizado"
> - El proceso coordinador mantiene el grafo de uso de recursos.
> - Los procesos envian mensajes al coordinador cuando obtienen o liberan un recurso y el coordinador actualiza el grafo.
> - El problema esta en que los mensajes pueden llegar desordenados y generar falsos deadlocks. -> Se pueden utilizar timestamps globales para ordenar los mensajes(algoritmo de Lamport).



!!! note "Algoritmo Distribuido"
> - Cuando un proceso debe esperar por un recurso, envía un `probe message` al proceso que tiene el recurso. El mensaje contiene: id del proceso que se bloquea, id del proceso que envía el mensaje y id del proceso destinatario. 
> - Al recibir el mensaje, el proceso actualiza el id del proceso que envía y el id del destinatario y lo envía a los procesos que tienen el recurso que necesita.
> - Si el mensaje llega al proceso original, tenemos un ciclo en el grafo. -> Un deadlock.
