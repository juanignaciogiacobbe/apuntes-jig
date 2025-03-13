# AWS Global Accelerator

- Leverage the AWS internal network to route to your application.
- 2 [[AWS/AWS Solutions Architect Associate Certification SAA-C03/07-CloudFront & Global Accelerator/02-Global Users for our Application|Anycast IP]] are created for your application -> The anycast IP send traffic directly to Edge Locations -> The Edge Locations send the traffic to your application.
- Consistent Performance
	- Intelligent routing to lowest latency and fast regional failover.
	- No issue with client cache(the IP doesn't change).
	- Internal AWS network.
	- Improves performance for a wide range of applications over TCP or UDP.
	- Proxying packets at the edge to applications running in one or more AWS Regions.
- Health Checks
	- Performs a health check of your applications.
	- Helps make your application global(failover less than 1 minute for unhealthy).
	- Great for Disaster Recovery.
- Security
	- Only 2 external IP need to be whitelisted.
	- DDoS protection thanks to AWS Shield.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241227091903.png]]