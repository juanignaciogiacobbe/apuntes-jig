> [!IMPORTANT] [Process](Sistemas%20Operativos/Proceso.md)
> A program that is running within an end system.
> When processes are running on the same end system, they can communicate with each other with interprocess communication.
> Processes on two different end systems communicate with each other by exchanging messages across the computer network.  A sending process creates and send messages into the network, and a receiving process receives these messages and possibly responds by sending messages back.


> [!WARNING] Communication Session and Processes
> The process that initiates the communication is labeled as the client.
> The process that waits to be contacted to begin the session is the server.


> [!IMPORTANT] Sockets
> Any message sent from one process to another must go through the underlying network. A process sends messages into, and receives messages from the network through a software interface called Socket.
> Its the interface between the application process and the transport-layer [Protocol](Redes/Chapter%201/02-Protocols.md).
> When a process wants to send a message to another process on another host, it shoves the message through its door(socket).
> Once the message arrives at the destination host, the message passes through the receiving process's door(socket), and the receiving process then acts on the message.  
