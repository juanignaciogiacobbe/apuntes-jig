# User Datagram Protocol(UDP)
- Best-effort service -> UDP segments may be lost, or delivered out-of-order to apps.
- Connectionless:
	- No handshaking between UDP sender and receivers.
	- Each UDP segment is handled independently of others.


> [!WARNING] Why is there a UDP?
> - No connection establishment(which can add RTT delay).
> - Simple -> No connection state at sender and receiver.
> - Small header size.
> - No congestion control.


## UDP Segment Header

![](Redes/Chapter%203/Pasted%20image%2020241014161239.png)

### UDP Checksum
- Goal: Detect errors in transmitted segment.
- The checksum is the addition(one's complement sum) of segment content. -> Is sended by the sender.
- The receiver checks if computed checksum equals checksum field value:
	- If it's not equal -> Error detected.
	- If it's equal -> No error detected.

![](Redes/Chapter%203/Pasted%20image%2020241014161440.png)