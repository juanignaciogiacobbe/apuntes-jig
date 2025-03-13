# AWS API Gateway
- Is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the front door for applications to access data, business logic, or functionality from your backend services. Using API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications.
- [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/06-AWS Lambda|AWS Lambda]] + API Gateway -> No infrastructure to manage.
- Support for the WebSocket Protocol.
- Handle API versioning, different environments and security.
- Create API keys, handle request throttling.
- Swagger / Open API import to quickly define APIs.
- Transform and validate requests and responses.
- Generate SDK and API specifications.
- Cache API responses.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250109083255.png]]



!!! warning "Amazon API Gateway creates RESTful APIs that:"

- Are HTTP-based.
- Enable stateless client-server communication.
- Implement standard HTTP methods such as GET, POST, PUT, PATCH, and DELETE.


!!! warning "Amazon API Gateway creates WebSocket APIs that:"

- Adhere to the WebSocket protocol, which enables stateful, full-duplex communication between client and server. Route incoming messages based on message content.
- So Amazon API Gateway supports stateless RESTful APIs as well as stateful WebSocket APIs.

---

## Endpoint Types
- Edge-Optimized(default) -> For global clients:
	- Requests are routed through the [[AWS/AWS Solutions Architect Associate Certification SAA-C03/07-CloudFront & Global Accelerator/01-Amazon CloudFront|CloudFront]] edge locations(improves latency).
	- The API Gateways still lives in only one region.
- Regional:
	- For clients within the same region.
	- Could manually combine with CloudFront(more control over the caching strategies and the distribution).
- Private:
	- Can only be accessed from your [[AWS/AWS Cloud Practitioner CLF-C02/04-Networking/01-Amazon Virtual Private Cloud VPC|VPC]] using an [[AWS/AWS Solutions Architect Associate Certification SAA-C03/01-EC2/03-Elastic Network Interfaces ENI|ENI]].
	- Use a resource policy to define access.
