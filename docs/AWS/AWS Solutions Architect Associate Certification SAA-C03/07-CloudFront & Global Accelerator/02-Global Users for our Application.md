# Global Users for our Application
- You have deployed an application and have global users who want access it directly -> They go over the public internet, which can add a lot of latency fue to many hops.
- We wish to go fast as possible through AWS network to minimize latency.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241227091306.png]]****

---


## Unicast IP
- One server holds one IP address.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241227091524.png]]


## Anycast IP
- All servers hold the same IP address and the client is routed to the nearest one.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241227091535.png]]