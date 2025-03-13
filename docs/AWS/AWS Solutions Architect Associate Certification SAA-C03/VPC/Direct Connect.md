# Direct Connect(DX)
- A cloud service solution that makes it easy to establish a dedicated network connection from your premises to AWS. AWS Direct Connect lets you establish a dedicated network connection between your network and one of the AWS Direct Connect locations.
- Provides a dedicated private connection from a remote network to your VPC.  
- Dedicated connection must be setup between your DC and AWS Direct Connect locations. 
- You need to setup a Virtual Private Gateway on your VPC. 
- Access public resources (S3) and private (EC2) on same connection.
- Use Cases: 
	- Increase bandwidth throughput - working with large data sets – lower cost. 
	- More consistent network experience - applications using real-time data feeds.
	- Hybrid Environments (on prem + cloud).
- Supports both IPv4 and IPv6.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250109093331.png]]


## Direct Connect Gateways
- If you want to setup a Direct Connect to one or more VPC in many different regions (same account), you must use a Direct Connect Gateway.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250109093439.png]]

## Encryption
- Data in transit is not encrypted but is private.  
- AWS Direct Connect + VPN provides an IPsec-encrypted private connection.  
- Good for an extra level of security, but slightly more complex to put in place.
- With AWS Direct Connect + VPN, you can combine one or more AWS Direct Connect dedicated network connections with the Amazon VPC VPN. This combination provides an IPsec-encrypted private connection that also reduces network costs, increases bandwidth throughput, and provides a more consistent network experience than internet-based VPN connections

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250109093718.png]]