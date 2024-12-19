# Private IP VS Public IP VS Elastic IP

!!! warning "Private VS Public IP"
> When you have a public IP you're accessible over the [[Redes/Chapter 1/01-Internet|Internet]], and when you have a private IP you are only accessible within your private network.
 

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241104150235.png]]


- **Public IP** means the machine can be identified on the Internet(WWW).
	- It must be unique across the whole web.
	- Can be geo-located easily.
- **Private IP** means the machine can only be identified on a private network only.
	- It must be unique across the private network.
	- Two different private networks can have the same IPs.
	- Machines connect to Internet using a NAT + Internet Gateway(a Proxy).
	- Only a specified range of IPs can be used as private IP.


!!! note "Elastic IPs"
> - When you stop and then start an [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]] instance, it can change its public IP.
> - If you need to have a fixed public IP for your instance, you need an Elastic IP.
> - An Elastic IP is a public IPv4 IP you own as long as you don't delete it.
> - You can attach it to one instance at a time.


!!! warning "Try to avoid using Elastic IP"
> - With an Elastic IP address, you can mask the failure of an instance of software by rapidly remapping the address to another instance in your account.
> - They often reflect poor architectural decisions.
> - Instead, use a random public IP and register a DNS name to it.
