
!!! important Domain Name System(DNS)
> - Translates the human friendly hostnames into the machine IP addresses.
> - Is the backbone of the [[Redes/Chapter 1/01-Internet.md|Internet]].
> - It uses hierarchical naming structure.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202133240.png]]

!!! warning DNS Terminologies
- Domain Registrar: Amazon Route 53, GoDaddy, ...
- DNS Records: A, AAAA, CNAME, ...
- Zone File: Contains DNS Records.
- Name Server: Resolves DNS queries(Authoritative or Non-Autoritative).
- Top Level Domain(TLD): `.com`, `.us`, ...
- Second Level Domain(SLD): `amazon.com`, `google.com`, ...

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202133131.png]]



!!! important Amazon Route 53
> - Highly available, scalable, fully managed and Authoritative(You can update the DNS records) DNS.
> - Is also a Domain Registrar.
> - Ability to check the health of your resources.
> - **It gives developers and businesses a reliable way to route end users to internet applications hosted in AWS**.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202133844.png]]

## How Amazon Route 53 and Amazon CloudFront deliver content

![[../img/route53_and_cloudfront.png]]

1. A customer requests data from the application by going to AnyCompany’s website.
2. Amazon Route 53 uses DNS resolution to identify AnyCompany.com’s corresponding IP address, 192.0.2.0. This information is sent back to the customer.
3. The customer’s request is sent to the nearest edge location through Amazon CloudFront.
4. Amazon CloudFront connects to the Application Load Balancer, which sends the incoming packet to an Amazon EC2 instance.