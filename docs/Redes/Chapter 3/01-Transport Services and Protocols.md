# Transport Services and Protocols
- Provide **logical communication** between application [Processes](Redes/Chapter%202/02-Processes%20Communicating.md) running on **different hosts**.

![](Redes/Chapter%203/Pasted%20image%2020241014153653.png)

- In this example:
	- Transport Protocol = Ann and Bill(they demux to in-house siblings).
	- Network-Layer Protocol = Postal service.
- The Network Layer provide logical communication between hosts.


# Demultiplexing 
- The process by which the arriving payloads are directed to the appropriate application or the appropriate protocol.
- Demultiplexing at receiver: Uses header info to deliver received segments to the correct socket.

![](Redes/Chapter%203/Pasted%20image%2020241014154414.png)

## How Demultiplexing works
1. Host receives IP datagrams:
	- Each datagram has source IP address and destination IP address.
	- Each datagram carries one destination port number.
2. Host uses IP addresses & port numbers to direct segment to appropriate socket.

# Multiplexing
- The inverse of demultiplexing :D.
- Multiplexing at sender: Handles data from multiple sockets and adds transport header(later used for demultiplexing.).

![](Redes/Chapter%203/Pasted%20image%2020241014154622.png)