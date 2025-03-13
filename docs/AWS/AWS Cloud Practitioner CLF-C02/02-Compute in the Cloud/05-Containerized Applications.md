# Containerized Applications

!!! note "Containerized Applications"
> **Containers**: **Provide you with a standard way to package your application's code and dependencies into a single object**. 
> They also can be use for processes and workflows in which there are essential requirements for security, reliability, and scalability.


![[containers1.png]]

![[containers2.png]]

---

## Amazon Elastic Container Service(Amazon ECS)
- Highly scalable, high-performance container management system that enables you to run and scale containerized applications on AWS. 
- Amazon ECS supports [[Ingenieria de Software I/17-Docker|Docker]] containers. -> You can use API calls to launch and stop Docker-enabled applications.
- Launch Docker containers on AWS = Launch ECS Tasks on ECS Clusters.
- AWS takes care of starting/ stopping containers.

### ECS Service Auto Scaling
- Automatically increase/decrease the desired numbers of ECS tasks.
- Amazon ECS Auto Scaling uses AWS Application Auto Scaling
	- ECS Service Average CPU Utilization.
	- ECS Service Average Memory Utilization -> Scale on RAM.
	- ALB Request Count Per Target -> Metric coming from the ALB.
- Target Tracking -> Scale based on target value for a specific [[AWS/AWS Cloud Practitioner CLF-C02/07-Monitoring and Analytcs/27-Amazon CloudWatch|CloudWatch]] metric.
- Step Tracking -> Scale based on a specified CloudWatch Alarm.
- Scheduled Scaling -> Scale based on a specified date/time(predictable changes).


---

## AWS Fargate
- [[04-Serverless Computing|Serverless Computing]] engine for containers. It works with both Amazon ECS and Amazon EKS. -> You do not provision the infrastructure, you just create task definitions.
- Allows you to manage containers, like Docker.
- Scales automatically.
- When using AWS Fargate, you do not need to provision or manage servers. AWS Fargate manages your server infrastructure for you. 
- **You can focus more on innovating and developing your applications, and you pay only for the resources that are required to run your container**s.

---

## Amazon Elastic Container Registry(Amazon ECR)
- Store and manage Docker images on AWS.
- Private and Public Repository(Amazon ECR Public Gallery).
- Fully integrated with ECS, backed by [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|Amazon S3]].
- Access is controlled through IAM(Permission errors -> Policy).
- Supports image vulnerability scanning, versioning, image tags, image lifecycle, ...


---

## AWS Lightsail
- Allows you to quickly launch all the resources you need for small projects.
- Deploy preconfigured applications, like WordPress websites.
- Simple screens for people with no Cloud experience.
- Includes a virtual machine, SSD-based storage, data transfer, DNS management and a static IP.

## AWS Outposts
- Run Cloud services in your internal data center.
- Support workloads that need to remain on-premises due to latency or data sovereignty needs.
- AWS delivers and installs servers in your internal data center.
- Used for a hybrid experience.
- Have access to the Cloud Services and APIs to develop apps on-premises.