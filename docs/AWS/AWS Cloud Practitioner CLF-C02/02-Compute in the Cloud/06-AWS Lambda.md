# AWS Lambda

!!! note "AWS Lambda"
> - Is a [[04-Serverless Computing|Serverless Computing]] service that lets you run code without managing servers.
> - **Lets you run code without needing to provision or manage servers**.
> - You author application code, called functions, using many popular languages.
> - Scales automatically.
> - **You pay only for the compute time that you consume**. Charges apply only when your code is running. 
> - Integrated with the whole AWS suite of services and with many programming languages.
> - Easy monitoring through [[AWS/AWS Cloud Practitioner CLF-C02/07-Monitoring and Analytcs/27-Amazon CloudWatch|AWS CloudWatch]].
> - Easy to get more resources per functions.

![[aws_lambda.png]]

- Lambda is a building block for many serverless applications:

	![[lambda.png]]


---
## Lambda SnapStart
- Improves your Lambda functions performance up to 10x at no extra cost for Java 11 and above.
- When enabled, function is invoked from a pre-initialized state(no function initialization from scratch).
- When you publish a new version:
	- Lambda initializes your function.
	- Takes a snapshot of memory and disk state of the initialized function.
	- Snapshot is cached for low-latency access.


![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241227140109.png]]


---

## Lambda by Default
- Your Lambda function is launched outside your own [[AWS/AWS Cloud Practitioner CLF-C02/04-Networking/01-Amazon Virtual Private Cloud VPC|VPC]](in an AWS-owned VPC).
- Therefore, it cannot access resources in your VPC.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241227141109.png]]


## Lambda in VPC
- You must define the VPC ID, the Subnets and the Security Groups. -> Lambda will create and [[AWS/AWS Solutions Architect Associate Certification SAA-C03/01-EC2/03-Elastic Network Interfaces ENI|ENI]] in your subnets.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241227141409.png]]

---

## Customization at the Edge
- Many modern applications execute some form of the logic at the edge.


!!! note "Edge Function"
> - A code that you write and attach to [[AWS/AWS Solutions Architect Associate Certification SAA-C03/07-CloudFront & Global Accelerator/01-Amazon CloudFront|CloudFront]] distributions.
> - Runs close to your users to minimize latency.
> - CloudFront provides CloudFront Functions and Lambda@Edge.
> - Pay only for what you use.
> - Fully [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/04-Serverless Computing|serverless]].


---

## CloudFront Functions
- Lightweight functions written in JavaScript.
- For high-scale, latency sensitive CDN customizations.
- Sub-ms startup times, millions of requests/second.
- Used to change Viewer requests and responses:
	- Viewer Request: After CloudFront receives a request from a viewer.
	- Viewer Response: Before CloudFront forwards the response to the viewer.


![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241227140644.png]]

---

## Lambda@Edge
- Lambda functions written in NodeJS or Python.
- Scales to 1000s of requests/second.
- Used to change CloudFront requests and responses:
	- Viewer Request: after CloudFront receives a request from a viewer.
	- Origin Request: before CloudFront forwards the request to the origin.
	- Origin Response: after CloudFront receives the response from the origin.
	- Viewer Response: before CloudFront forwards the response to the viewer.
- Author your functions in one AWS Region (us-east-1), then CloudFront replicates to its locations.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241227140910.png]]


---

## Lambda with [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/02-Amazon Relational Database Service RDS|RDS]] Proxy
- If Lambda functions directly access your database, they may open too many connections under high load.
- RDS Proxy:
	- Improve scalability by pooling and sharing DB connections.
	- Improve availability by reducing by 66% the failover time and preserving connections.
	- Improve security by enforcing IAM authentication and storing credentials in Secrets Manager.
- The Lambda function must be deployed in your VPC, because RDS Proxy is never publicly accessible.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20241227142007.png]]
