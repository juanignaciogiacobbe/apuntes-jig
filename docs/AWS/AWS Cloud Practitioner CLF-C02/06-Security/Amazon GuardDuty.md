# Amazon GuardDuty
- Intelligent Threat discovery to protect your AWS account -> Uses ML algorithms, anomaly detection, 3rd party data.
- No need to install software.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250109092011.png]]

- Input data includes:
	- [[AWS/AWS Cloud Practitioner CLF-C02/07-Monitoring and Analytcs/28-AWS CloudTrail|CloudTrail]] Events Logs(unusual API calls, unauthorized deployments)
		- CloudTrail Management Events.
		- CloudTrail S3 Data Events
	- VPC Flow Logs
	- DNS Logs
	- Optional Features(EKS Audit Logs, RDS & Aurora, EBS, ...)
- Can setup [[AWS/AWS Solutions Architect Associate Certification SAA-C03/Monitoring, Audit and Performance/Amazon EventBridge|EventBridge]] rules(AWS Lambda or SNS) to be notified in case of findings.
- Can protect against CryptoCurrency attacks(has a dedicated "finding" for it).

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221150158.png]]

## Use cases
- **Detect suspicious activity in your generative AI workloads**.
- **Accelerate investigations and automate remediation**.
- **Protect against ransomware and other types of malware**.
- **Centralize threat detection for AWS container workloads**.
- **More easily meet compliance requirements, like PCI DSS**.

---

## Multi-Account Strategy
- You can manage multiple accounts in GuardDuty -> Associate the Member accounts within the Administrator account
	- Through an [[AWS/AWS Cloud Practitioner CLF-C02/06-Security/23-AWS Organizations|AWS Organization]]
	- Sending invitation through GuardDuty
- Administrator account can:
	- Add or remove member accounts.
	- Manage GuardDuty within the associated member accounts.
	- Manage findings, suppression rules, trusted IP lists, threat lists.
- In an Organization, you can specify a member account as the Organization's delegated administrator for GuardDuty.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221150641.png]]

---

## Findings Automated Response
- Findings are potential security issue for malicious events happening in your AWS account. -> Automate response to security issues revealed by GuardDuty findings using EventBridge. -> Send alerts to SNS(email, Lambda, Slack, ...).
- Events are published to both the administrator account and the member account that it is originated from.

### Findings
- GuardDuty pulls independent streams of data directly from CloudTrail Logs, VPC Flow Logs or EKS Logs.
- Each finding has a severity value between 0.1 to 8+(High, Medium, Low).
- Finding naming convention:

```
TheatPurpose:ResourceTypeAffected/ThreatFamilyName.DetectionMechanism!Artifcact
```
- ThreatPurpose: Primary purpose of the threat.
- ResourceTypeAffected: Which AWS resource is the target.
- ThreatFamilyName: Describes the potential malicious activity.
- DetectionMechanism: Method GuardDuty detecting the finding.
- Artifact: Describes a resource that is used in the malicious activity.

- You can generate sample findings in GuardDuty to test your automations.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221151734.png]]


---

## Trusted and Threat IP Lists
- Works only for public IP addresses.
- Trusted IP List
	- List of IP addresses and CIDR ranges that you trust.
	- GuardDuty doesn't generate findings for these trusted lists.
- Threat IP List
	- List of known malicious IP addresses and CIDR ranges.
	- GuardDuty generates findings based on these threat lists.
	- Can be supplied by 3rd party threat intelligence or created custom for you.
- In a multi-account GuardDuty setup, only the GuardDuty administrator account can manage those lists.

---

## Suppression Rules
- Set of criteria that automatically filter and archive new findings.
- Example: low-value findings, false-positive findings, or threats you don't intend to act on.
- Can suppress entire findings types or define more granular criteria.
- Suppressed findings are NOT sent to Security Hub, S3, Detective, or EventBridge.
- Suppressed findings can be still viewed in the Archive.







