
> [!WARNING] Private VS Public IP
> When you have a public IP you're accessible over the [Internet](Redes/Chapter%201/01-Internet.md), and when you have a private IP you are only accessible within your private network.
 

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241104150235.png)


- **Public IP** means the machine can be identified on the Internet(WWW).
	- It must be unique across the whole web.
	- Can be geo-located easily.
- **Private IP** means the machine can only be identified on a private network only.
	- It must be unique across the private network.
	- Two different private networks can have the same IPs.
	- Machines connect to Internet using a NAT + Internet Gateway(a Proxy).
	- Only a specified range of IPs can be used as private IP.


> [!IMPORTANT] Elastic IPs
> - When you stop and then start an [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) instance, it can change its public IP.
> - If you need to have a fixed public IP for your instance, you need an Elastic IP.
> - An Elastic IP is a public IPv4 IP you own as long as you don't delete it.
> - You can attach it to one instance at a time.


> [!WARNING] Try to avoid using Elastic IP
> - With an Elastic IP address, you can mask the failure of an instance of software by rapidly remapping the address to another instance in your account.
> - They often reflect poor architectural decisions.
> - Instead, use a random public IP and register a DNS name to it.
