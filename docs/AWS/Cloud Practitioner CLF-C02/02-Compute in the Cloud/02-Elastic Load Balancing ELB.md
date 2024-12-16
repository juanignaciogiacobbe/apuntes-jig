
!!! note "Load Balancers"
> Servers that forward traffic to multiple servers downstream.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202103316.png]]


!!! note "Why use a Load Balancer?"
- Spread load across multiple downstream instances.
- Expose a single point of access(DNS) to your application.
- Seamlessly handle failures of downstream instances.
- Do regular health checks to your instances.
- Provide SSL termination(HTTPS) for your websites.
- Enforce stickiness across zones.
- High Availability across zones.
- Separate public traffic from private traffic.


!!! note "Health Checks"
> - Enable the Load Balancer to know if instances it forwards traffic to are available to reply to requests.
> - Is done on a port and a route(`/health` is common).
> - If the response is not 200(OK), then the instance is unhealthy.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202104321.png]]


---

!!! note "Directing Traffic with Elastic Load Balancing"
> Automatically distributes incoming application traffic across multiple resources, such as [[EC2)](AWS/Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2.md|Amazon Elastic Compute Cloud(EC2)]].
> - A load balancer acts as a single point of contact for all incoming web traffic to your Auto Scaling group.
> - As you add or remove Amazon EC2 instances in response to the amount of incoming traffic, these requests route to the load balancer first.

> [[AWS/Slides/AWS Certified Solutions Architect Slides v39.pdf#page=128&selection=8,0,8,29&color=yellow]]
> > Types of load balancer on AWS
> 
> 

![[AWS/Cloud Practitioner CLF-C02/img/elastic_load_balancing_example.png]]

- Suppose that a few customers have come to the coffee shop and are ready to place their orders. 
- If only a few registers are open, this matches the demand of customers who need service. The coffee shop is less likely to have open registers with no customers. In this example, you can think of the registers as Amazon EC2 instances.


![[AWS/Cloud Practitioner CLF-C02/img/elb_example_two.png]]

- Throughout the day, as the number of customers increases, the coffee shop opens more registers to accommodate them. 
- Additionally, a coffee shop employee directs customers to the most appropriate register so that the number of requests can evenly distribute across the open registers. You can think of this coffee shop employee as a load balancer.

---


!!! note "Sticky Sessions(Session Affinity)"
> The same Client is always redirected to the same instance behind a Load Balancer.
> - Works for Classic, Application and Network Load Balancers.
> - Use Case: Make sure the User doesn't lose his session data.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202122300.png]]