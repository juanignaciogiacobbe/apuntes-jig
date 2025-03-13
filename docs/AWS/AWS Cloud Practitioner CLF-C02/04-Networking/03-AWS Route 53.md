# AWS Route 53

## Domain Name System(DNS)

!!! note "Domain Name System(DNS)"
> - Translates the human friendly hostnames into the machine IP addresses.
> - Is the backbone of the [[Redes/Chapter 1/01-Internet|Internet]].
> - It uses hierarchical naming structure.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202133240.png]]

!!! warning "DNS Terminologies"
- Domain Registrar: Amazon Route 53, GoDaddy, ...
- DNS Records: A, AAAA, CNAME, ...
- Zone File: Contains DNS Records.
- Name Server: Resolves DNS queries(Authoritative or Non-Authoritative).
- Top Level Domain(TLD): `.com`, `.us`, ...
- Second Level Domain(SLD): `amazon.com`, `google.com`, ...

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202133131.png]]


---

## AWS Route 53

!!! note "Amazon Route 53"
> - Highly available, scalable, fully managed and Authoritative(You can update the DNS records) DNS.
> - Is also a Domain Registrar.
> - Ability to check the health of your resources.
> - **It gives developers and businesses a reliable way to route end users to internet applications hosted in AWS**. -> Is the only AWS service which provides 100% availability SLA.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202133844.png]]

## How Amazon Route 53 and Amazon CloudFront deliver content?

![[route53_and_cloudfront.png]]

1. A customer requests data from the application by going to AnyCompany’s website.
2. Amazon Route 53 uses DNS resolution to identify AnyCompany.com’s corresponding IP address, 192.0.2.0. This information is sent back to the customer.
3. The customer’s request is sent to the nearest edge location through Amazon CloudFront.
4. Amazon CloudFront connects to the [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/02-Elastic Load Balancing ELB|Application Load Balancer]], which sends the incoming packet to an Amazon EC2 instance.


---

## Route 53 Record Types
- A -> Maps a hostname to IPv4.
- AAAA -> Maps a hostname to IPv6.
- CNAME -> Maps a hostname to another hostname
	- The target is a domain name which must have an A or AAAA record.
	- Can't create a CNAME record for the top node of a DNS namespace(Zone Apex)
- NS -> Name Servers for the Hosted Zone
	- Control how traffic is routed for a domain.

---


## Route 53 Hosted Zones


!!! note "Route 53 Hosted Zones"
> A container for records that define how to route traffic to a domain and its subdomains.


- Public Hosted Zones -> Contains records that specify how to route traffic on the Internet(public domain names).

	![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241220100459.png]]

- Private Hosted Zones -> Contains records that specify how to route traffic within one or more [[AWS/AWS Cloud Practitioner CLF-C02/04-Networking/01-Amazon Virtual Private Cloud VPC|VPC]] (private domain names).

	![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241220100517.png]]


---

## Alias Records
- Maps a hostname to an AWS resource. -> It's an extension to DNS functionality.
- Automatically recognizes changes in the resource's IP address.
- It can be used for the top node of a DNS namespace.
- Is always of type A/AAAA for AWS resources.
- You can't set the TTL.

	![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241220100844.png]]

> [!PDF|red] [[AWS/Slides/AWS Certified Solutions Architect Slides v39.pdf#page=205&selection=0,17,12,16&color=red|AWS Certified Solutions Architect Slides v39, p.205]]
> > © Stephane Maarek NOT FOR DISTRIBUTION © Stephane Maarek www.datacumulus.com Route 53 – Routing Policies
> 
> 