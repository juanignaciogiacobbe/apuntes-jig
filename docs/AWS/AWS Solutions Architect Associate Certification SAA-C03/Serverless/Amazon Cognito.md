# Amazon Cognito
- Give users an identity to interact with our web or mobile application.
- Cognito User Pools:
	- Sign in functionality for app users.
	- Integrate with [[AWS/AWS Solutions Architect Associate Certification SAA-C03/Serverless/AWS API Gateway|API Gateway]] & [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/02-Elastic Load Balancing ELB|ALB]].
- Cognito Identity Pools(Federated Identity):
	- Provide AWS credentials to users so they can access AWS resources directly.
	- Integrate with Cognito User Pools as an identity provider.


---
## Cognito User Pools
- Create a serverless database of user for your web & mobile apps.
- Features: 
	- Simple login: Username(or email) / password combination.
	- Password reset.
	- Email & Phone Number Verification.
	- Multi-Factor Authentication(MFA).
	- Federated Identities: users from Facebook, Google, ...

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250113101811.png]]

---
## Cognito Identity Pools(Federated Identities)
- Get identities for "users" so they obtain temporary AWS credentials.
- Users can then access to AWS services directly or through API Gateway-
- The [[AWS/AWS Cloud Practitioner CLF-C02/06-Security/22- AWS Identity and Access Management IAM|IAM]] policies applied to the credentials are defined in Cognito.
- They can be customized based on the `user_id` for fine grained control.
- Default IAM roles for authenticated and guest users.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250113101745.png]]