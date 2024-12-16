
!!! note Entidades
> Es la unidad de cómputo de ambiente informático distribuido.
> - Puede ser un [[Sistemas Operativos/Proceso|Proceso]], un procesador, etc.


!!! warning Capacidades de las Entidades
- Acceso de lectura y escritura a una memoria local(no compartida con otras entidades):
	- Registro de estado: `status(x)`.
	- Registro de valor de entrada: `value(x)`.
- Procesamiento Local.
- Comunicación: Preparación, transmisión y recepción de mensajes.
- Setear y resetear un reloj local.


!!! note Las entidades son reactivas -> Solamente responden a eventos externos
- Llegada de algún mensaje.
- Activación del reloj.
- Un impulso espontáneo.
	- A excepción del impulso espontáneo, los eventos se generan dentro de los límites del sistema.

---

!!! note Acción
> Secuencia finita e indivisible de operaciones. Es atómica porque se ejecuta sin interrupciones.


!!! note Regla
> Es la relación entre el evento que ocurre y el estado en el que se encuentra la entidad cuando ocurre dicho evento, de modo tal que:
> `estado x evento -> acción`
> - La entidad(que tiene un estado interno en cierto momento) recibe un evento externo(que dispara un cómputo dentro de ella). En base al estado interno y al evento, la regla va a determinar qué acción se ejecuta.


!!! note Comportamiento
> Es el conjunto `B(x)` de todas las reglas que obedece una entidad `x`. 
> - Para cada posible evento y estado debe existir una única regla `B(x)`. -> El algoritmo es determinístico, y cada acción es propia de la tupla `(estado, evento)`.
> - `B(x)` se llama también protocolo o algoritmo distribuido de `x`.
> 
> Comportamiento colectivo del ambiente distribuido:
> `B(E) = B(X) para todo x perteneciente a E`


!!! note Comportamiento Homogéneo
> El comportamiento colectivo es homogéneo si todas las entidades que lo componen tienen el mismo comportamiento.
> - Todas las entidades tienen el mismo protocolo.

!!! warning Propiedad
> Todo comportamiento colectivo se puede transformar en homogéneo.


!!! note Comunicación
> - Una entidad se comunica con otras entidades mediante mensajes(un mensaje es una secuencia finita de bits).
> - Puede ocurrir que una entidad sólo pueda comunicarse con un subconjunto del resto de las entidades.
> 	- Nout(x): Conjunto de entidades a las cuales x puede enviarles un mensaje directamente.
> 	- Nin(x): Conjunto de entidades de las cuales x puede recibir un mensaje directamente.


## Axiomas

!!! warning Delay de comunicación finitos
> En ausencia de fallas los delays en la comunicación tienen una duración finita.

!!! warning Orientación Local
> Una entidad puede distinguir entre sus vecinos Nout y entre sus vecinos Nin.
> - Puede distinguir qué vecino le envía un mensaje.
> - Puede enviar un mensaje a un vecino específico.


> [!DANGER] Restricciones de Confiabilidad
- Entrega garantizada -> Cualquier mensaje enviado será recibido con su contenido intacto.
- Confiabilidad Parcial -> No ocurrirán fallas.
- Confiabilidad Total -> No han ocurrido ni ocurrirán fallas.


> [!DANGER] Restricciones Temporales
- Delays de comunicación acotados -> Existe una constante $\Delta$ tal que en ausencia de fallas, el delay de cualquier mensaje en el enlace es a lo sumo $\Delta$.
- Delays de comunicación unitarios -> En ausencia de fallas, el delay de cualquier mensaje en un enlace es igual a una unidad de tiempo.
- Relojes sincronizados -> Todos los relojes locales se incrementan simultáneamente y el intervalo de incremento es constante.

---

!!! note Costo y Complejidad
> Son las medidas de comparación de los algoritmos distribuidos. Se tienen en cuenta:
> - Cantidad de actividades de comunicación: 
> 	- Cantidad de transmisiones o costo de mensajes M.
> 	- Carga de trabajo por entidad y carga de transmisión.
> - Tiempo:
> 	- Tiempo total de ejecución del protocolo.
> 	- Tiempo ideal de ejecución: Tiempo medido bajo ciertas condiciones, como delays de comunicación unitarios y relojes sincronizados.

---


!!! note Tiempo y Eventos
> Los eventos desencadenan acciones en un tiempo futuro. Los distintos delays resultan en distintas ejecuciones del protocolo con posibles resultados diferentes:
> - Los eventos disparan acciones que pueden generar nuevos eventos.
> - Si suceden, los nuevos eventos ocurrirán en un tiempo futuro: `Future(t)`.
> - Una ejecución se describe por la secuencia de eventos que ocurrieron.


!!! note Estados y Configuraciones
- Estado interno de $x$ en el instante $t$ -> $\sigma(x, t)$: Contenido de los registros de $x$ y el valor del reloj $c_x$ en el instante $t$.
- El estado interno de una entidad cambia con la ocurrencia de eventos.



!!! note Conocimiento
- Conocimiento Local -> Contenido de la memoria local de `x` y la información que se deriva. En ausencia de fallas, el conocimiento no puede perderse.


!!! note Tipos de Conocimiento
- Información métrica: Información numérica sobre la red. Ejemplo: el número de nodos del grafo, número de arcos del grafo, diámetro del grafo y demás.
- Propiedades topológicas: Conocimiento sobre propiedades de la topología. Ejemplo: El grafo es un anillo, el grafo es acíclico y demás.
- Mapas topológicos: Un mapa de la vecindad de la entidad hasta una distancia `d`. Ejemplo: Matriz de adyacencia de un grafo.