> [!WARNING] Delay
> A packet starts in a host, passes through a series of routers, and ends its journey in another host. 
> As a packet travels from one node to the subsequent node along this path, the packet suffers from several types of delays at each node along the path.


> [!IMPORTANT] Round-Trip Time(RTT)
> Tiempo que tarda un paquete de datos enviado desde un emisor en volver al mismo emisor habiendo pasado por el receptor de destino.


## Types of Delay


> [!IMPORTANT] Processing Delay
> The time required to examine the packet's header and determine where to direct the packet. It can include other factors, such as the time needed to check for bit-level errors in the packet that occurred in transmitting the packet's bits from the upstream node to router A.


> [!IMPORTANT] Queuing Delay
> At the Queue, the packet experiences a queuing delay as it waits to be transmitted onto the link. The length of the queuing delay of a specific packet will depend on the number of earlier-arriving packets that are queued and waiting for transmission onto the link.


> [!WARNING] Packet Loss
> The queuing capacity greatly depends on the router design and cost -> With no place to store such a packet, a router will drop that packet -> The packet will be lost.
> A packet loss will look like a packet having been transmitted into the network core but never emerging from the network at the destination -> The fraction of lost packets increases as the traffic intensity increases.


> [!IMPORTANT] Transmission Delay
> Our packet can be transmitted only after all the packets that have arrived before it have been transmitted.

$$t_{delay} = L/R$$


> [!IMPORTANT] Propagation Delay
> The amount of time required for the router to push out the packet. It's a function of the packet's length and the transmission rate of the link, but has nothing to do with the distance between the two routers.
> Is the time it takes a bit to propagate from one router to the next.

---


> [!IMPORTANT] Throughput
> The rate(in bits/sec) at which host B is receiving a file.
> Cantidad de datos que se pueden transmitir a través de una red en un período de tiempo determinado.
> Tasa a la que se transfieren bits entre transmisor/receptor [b/s].

