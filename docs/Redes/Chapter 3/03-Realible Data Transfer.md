# Reliable Data Transfer(RDT)

![](Redes/Chapter%203/Pasted%20image%2020241014162606.png)

![](Redes/Chapter%203/Pasted%20image%2020241014162630.png)

- The complexity of reliable data transfer protocol will depend(strongly) on characteristics of the unreliable channel.  

![](Redes/Chapter%203/Pasted%20image%2020241014162951.png)


- Underlying channel may flip bits in packet(checksum to detect bit errors).
	- Acknowledgements(ACKs): Receiver explicitly tells sender that pkt received OK.
	- Negative Acknowledgements(NACKs): Receiver explicitly tells sender that pkt had errors.  -> Sender retransmits pkt on receipt of NACK.

- Stop & Wait: Sender sends one packet -> The waits for receiver response.
- The sender retransmits current pkt if ACK/NACK is corrupted -> The sender adds sequence number to each pkt. -> The receiver discards duplicate pkts.