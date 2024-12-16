
!!! important Scalability
> Involves beginning with only the resources you need and designing your architecture to automatically respond to changing demand by scaling out or in. 
> - You don’t have to worry about a lack of computing capacity to meet your customers’ needs.

!!! warning Kinds of Scalability
> - Vertical Scalability -> Increasing the size of the instance. There's usually a limit to how much you can vertically scale(hardware limit).
> - Horizontal Scalability -> Increasing the number of instances/systems for your application. It's easy to horizontally scale thanks the Cloud offerings.


!!! note High Availability
> Running your application/system in at least 2 Data Centers(== [Availability Zones](AWS/Cloud Practitioner (CLF-C02)/03-Infrastructure and Realiability/02-Availability Zones.md)).
> - It's goal is to survive a data center loss.


!!! important Amazon [EC2](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2).md) Auto Scaling
> - Enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. -> You can maintain a greater sense of application availability.


!!! important Auto Scaling Group
> - Scale out to match an increased load.
> - Scale in to match a decreased load.
> - Ensure we have a minimum and a maximum number of EC2 instances running.
> - Automatically register new instances to a load balancer.
> - Re-create an EC2 instance in case a previous one is terminated.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202122835.png)


!!! warning Auto Scaling Group Attributes
- Launch Template:
	- [AMI](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI.md) + Instance Type.
	- EC2 User Data.
	- [EBS](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md) Volumes.
	- Security Groups.
	- SSH Key Pair.
	- IAM Roles for the EC2 instances.
	- Network + Subnets Information.
	- [Load Balancer](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/02-Elastic Load Balancing(ELB).md) Information.
- Min Size / Max Size / Initial Capacity.
- Scaling Policies.

> [!PDF|yellow] [AWS Certified Solutions Architect Slides v39, p.155](AWS/Slides/AWS Certified Solutions Architect Slides v39.pdf#page=155&selection=8,0,12,27&color=yellow)
> > Auto Scaling - CloudWatch Alarms & Scaling



!!! important Auto Scaling Instance Refresh
> Update launch template and then re-creating all EC2 instances.
> - Setting of minimum healthy percentage.
> - Specify warm-up time(how long until the instance is ready to use).

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241204092509.png)