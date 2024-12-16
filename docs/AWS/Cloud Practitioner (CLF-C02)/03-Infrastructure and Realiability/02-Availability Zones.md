
> [!IMPORTANT] Availability Zones
> - Single data center or a group of data centers within a Region. -> Collection of data centers.
> - Data center -> Contains multiple **servers**: physical compute hardware running in a data center.
> - Availability Zones are located tens of miles apart from each other. This is close enough to have low latency (the time between when content requested and received) between Availability Zones. 
> - If a disaster occurs in one part of the Region, they are distant enough to reduce the chance that multiple Availability Zones are affected.
> - **Fault Tolerant**: Enables a system to continue operating properly in the event of the failure of one or more components.
> - Allows for **high availability**.
> - Best practice: Run applications across at least two Availability Zones in a Region -> High availability.


![availability_zones 1](../img/availability_zones%201.png)


![ec2-instance-availability_zone1](../img/ec2-instance-availability_zone1.png)

![ec2-instance-availability_zone1](../img/ec2-instance-availability_zone2.png)

![ec2-instance-availability_zone1](../img/ec2-instance-availability_zone3.png)