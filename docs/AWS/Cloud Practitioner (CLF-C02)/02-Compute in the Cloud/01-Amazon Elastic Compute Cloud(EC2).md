
!!! important Amazon Elastic Compute Cloud(EC2)
> - Allows you to **rent and manage virtual servers in the Cloud**(Infrastructure as a Service). -> Provides secure, resizable compute capacity in the Cloud.
> 	- Provision and launch an Amazon EC2 instance within minutes.
> 	- Stop using it when you have finished running a workload.
> 	- Pay only for the compute time you use when an instance is running, not when it is stopped or terminated.
> 	- Save costs by paying only for server capacity that you need or want.
> 	- Deploy your applications directly to EC2 instances.
> 	- Use a preconfigured template called an  [[AMI)](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI.md|Amazon Machine Image(AMI)]] to launch your instance.
> 	- Highly flexible, cost-effective and quick when you compare it to running your own servers on premises in a data center that you own.


!!! note Multitenancy
> Sharing underlying hardware between Virtual Machines. EC2 runs on top of physical host machines managed by AWS using virtualization technology.

![[../img/EC2_example.png]]

1. **Launch**: Begin by selecting a template with basic configurations for your instance(operating system, application server, or applications). You also select the instance type, which is the specific hardware configuration of your instance. You also specify security settings to control the network traffic that can flow into and out of your instance.
2. **Connect**: Your programs and applications have multiple different methods to connect directly to the instance and exchange data. Users can also connect to the instance by logging in and accessing the computer desktop.
3. **Use**: You can run commands to install software, add storage, copy and organize files, and more.
## Storage

![[../img/ec2_storage.png]]

---

!!! important EC2 Instance Types
> - Each EC2 instance type is grouped under an instance family.
> - They offer varying combinations of CPU, memory, storage and networking capacity.

- **General purpose**: Balanced resources(compute, memory, and networking resources). Can be used for a variety of diverse workloads like web service or code repositories. For applications that does not require optimization in any single resource area.
- **Compute Optimized**: Ideal for compute-intensive tasks like gaming servers, high performance computing or HPC, and even scientific modeling
- **Memory Optimized**: Good for memory-intensive tasks. Memory optimized instances enable you to run workloads with high memory needs and receive great performance.
- **Accelerated Computing**: Are good for floating point number calculations, graphics processing, or data pattern matching, as they use hardware accelerators.
- **Storage Optimized**: For Workloads that require high performance for locally stored data.

!!! warning Naming Convention
> Example: `m5.2xlarge`
> - `m`: Instance class.
> - `5`: Generation.
> - `2xlarge`: Size within the instance class.

---

!!! warning EC2 Pricing
> You only pay for what you use.
## On-Demand Instances
- You only pay for the duration that your instance runs for.
- Ideal for short-term, irregular workloads that cannot be interrupted. No upfront costs or minimum contracts apply. The instances run continuously until you stop them, and you pay for only the compute time you use.  
  - Sample use cases for On-Demand Instances include developing and testing applications and running applications that have unpredictable usage patterns. On-Demand Instances are not recommended for workloads that last a year or longer because these workloads can experience greater cost savings using Reserved Instances.

## Reserved Instances
- There are suited for steady-state workloads or ones with predictable usage.
- Billing discount applied to the use of On-Demand Instances in your account.
- Standard Reserved Instances: Is a good fit if you know the EC2 instance type and size you need for your steady-state applications and in which AWS Region you plan to run them. Require you to state the instance type and size, the platform description(OS) and Tenancy.
- Convertible Reserved Instances: If you need to run your EC2 instances in different [[AWS/Cloud Practitioner (CLF-C02|02-Availability Zones]]/03-Infrastructure%20and%20Realiability/02-Availability%20Zones.md) or different instance types, then Convertible Reserved Instances might be right for you.

## Instance Saving Plans
- Reduce your EC2 instance costs when you make an hourly spend commitment to an instance family and Region for a 1-year or 3-year term.
- The EC2 Instance Savings Plans are a good option if you need flexibility in your Amazon EC2 usage over the duration of the commitment term.

## Spot Instances
- Ideal for workloads with flexible start and end times, or that can withstand interruptions. Spot Instances use unused Amazon EC2 computing capacity and offer you cost savings at up to 90% off of On-Demand prices.
- After you have launched a Spot Instance, if capacity is no longer available or demand for Spot Instances increases, your instance may be interrupted.

## Dedicated Host
- Are physical hosts dedicated for your use for EC2. These are usually for meeting certain compliance requirements and nobody else will share tenancy of that host.
- Physical servers with Amazon EC2 instance capacity that is fully dedicated to your use. 
- You can use your existing per-socket, per-core, or per-VM software licenses to help maintain license compliance. You can purchase On-Demand Dedicated Hosts and Dedicated Hosts Reservations. Of all the Amazon EC2 options that were covered, Dedicated Hosts are the most expensive.

---

!!! important EC2 User Data
> It is possible to bootstrap our instances using an EC2 User Data script.
> - That script is only run once at the instance first start(runs with the root user).
> - Is used to automate boot tasks such as installing updates and software, downloading common files from the [[Redes/Chapter 1/01-Internet.md|Internet]], ...

