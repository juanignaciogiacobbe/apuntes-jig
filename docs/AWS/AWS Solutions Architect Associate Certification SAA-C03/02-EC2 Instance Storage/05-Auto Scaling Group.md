# Auto Scaling Groups

!!! note "Scalability"
> Involves beginning with only the resources you need and designing your architecture to automatically respond to changing demand by scaling out or in. 
> You don’t have to worry about a lack of computing capacity to meet your customers’ needs.

!!! warning "Kinds of Scalability"
> - Vertical Scalability -> Increasing the size of the instance. There's usually a limit to how much you can vertically scale(hardware limit).
> - Horizontal Scalability -> Increasing the number of instances/systems for your application. It's easy to horizontally scale thanks the Cloud offerings.


!!! note "High Availability"
> Running your application/system in at least 2 Data Centers(== [[AWS/AWS Cloud Practitioner CLF-C02/03-Infrastructure and Realiability/02-Availability Zones|Availability Zones]]) -> It's goal is to survive a data center loss.


!!! note "Auto Scaling"
> Enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. -> You can maintain a greater sense of application availability.


!!! note "Auto Scaling Group"
> - Scale out to match an increased load.
> - Scale in to match a decreased load.
> - Ensure we have a minimum and a maximum number of EC2 instances running.
> - Automatically register new instances to a load balancer.
> - Re-create an EC2 instance in case a previous one is terminated.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202122835.png]]


!!! warning "Auto Scaling Group Attributes"
- Launch Template:
	- [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI|AMI]] + Instance Type.
	- EC2 User Data.
	- [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS|EBS]] Volumes.
	- Security Groups.
	- SSH Key Pair.
	- IAM Roles for the EC2 instances.
	- Network + Subnets Information.
	- [[02-Elastic Load Balancing ELB|Load Balancer]] Information.
- Min Size / Max Size / Initial Capacity.
- Scaling Policies.

> [[AWS/Slides/AWS Certified Solutions Architect Slides v39.pdf#page=155&selection=8,0,12,27&color=yellow]]
> > Auto Scaling - CloudWatch Alarms & Scaling

---

## [[AWS/AWS Cloud Practitioner CLF-C02/07-Monitoring and Analytcs/27-Amazon CloudWatch|CloudWatch]] Alarms & Scaling
- It is possible to scale an ASG based on CloudWatch alarms.
- An alarm monitors a metric(such as Average CPU, or a custom metric). -> Those metrics are computed for the overall ASG instances.
- Based on the alarm:
	- We can create scale-out policies(increase the number of instances).
	- We can create scale-in policies(decrease the number of instances).

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220091153.png]]

### Scaling Policies
- Dynamic Scaling
	- Target Tracking Scaling:
		- Simple to set-up.
		- Example: I want the average ASG CPU to stay at around 40%.
	- Simple/Step Scaling:
		- When a CloudWatch alarm is triggered(example CPU > 70%), then add 2 units.
		- When a CloudWatch alarm is triggered(example CPU < 70%), then remove 2 units.
- Scheduled Scaling
	- Anticipate a scaling based on known usage patterns.
	- Example: Increase the min capacity to 10 at 5pm on fridays.
- Predictive Scaling
	- Continuously forecast load and schedule scaling ahead.
	![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220091534.png]]

### Good Metrics to Scale on
- CPUUtilization: Average CPU utilization across your instances.
- RequestCountPerTarget: To make sure the number of requests per EC2 instances is stable.
- Average Network In/Out if your application is network bound.
- Any custom metric that you push using CloudWatch.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220091809.png]]

### Scaling Cooldowns
- After scaling activity happens, you are in the cooldown period(default 300 seconds).
- During the cooldown period, the ASG will not launch or terminate additional instances(to allow for metrics to stabilize).
- Advice: Use a ready-to-use [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI|AMI]] to reduce configuration time in order to be serving request fasters and reduce the cooldown period.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220093125.png]]


!!! note "Auto Scaling Instance Refresh"
> Update launch template and then re-creating all EC2 instances.
> - Setting of minimum healthy percentage.
> - Specify warm-up time(how long until the instance is ready to use).

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241204092509.png]]