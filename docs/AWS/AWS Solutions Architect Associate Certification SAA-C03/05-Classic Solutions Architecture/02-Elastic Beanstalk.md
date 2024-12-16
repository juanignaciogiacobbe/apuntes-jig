
!!! note Elastic Beanstalk
> A developer centric view of deploying an application on AWS.
> - Managed Service:
> 	- Automatically handles capacity provisioning, load balancing, scaling, application health monitoring, instance configuration, ...
> 	- Just the application code is the responsibility of the developer.
> - We still have full control over the configuration.
> - You pay for the underlying instances.

## Components
- Application: Collection of Elastic Beanstalk components(environments, versions, configurations, ...).
- Application Version: An iteration of your application code.
- Environment:
	- Collection of AWS resources running an application version(only one application version at a time).
	- Tiers: Web Server Environment Tier & Worker Environment TIer.
	- You can create multiple environments(dev, test, prod, ...).

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241203092710.png]]
![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241203092923.png]]