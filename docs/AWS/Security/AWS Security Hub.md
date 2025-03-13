# AWS Security Hub
- Central security tool to manage security across several AWS accounts and automate security checks.
- Integrated dashboards showing current security and compliance status to quickly take actions.
- Automatically aggregates alerts in predefined or personal findings formats from various AWS services & AWS partner tools:
	- Config
	- GuardDuty
	- Inspector
	- Macie
	- IAM Access Analyzer
	- AWS Systems Manager
	- AWS Firewall Manager
	- AWS Health
	- AWS Partner Network Solutions
- Must first enable the AWS Config Service.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221153349.png]]


## Services Integration
![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221154603.png]]

---

## Main Features
- Cross-Region Aggregation -> Aggregate findings, insights, and security scores from multiple Regions to a single aggregation Region.
- [[AWS/AWS Cloud Practitioner CLF-C02/06-Security/23-AWS Organizations|AWS Organizations]] Integration.
	- Manage all accounts in the Organization.
	- Security Hub automatically detects new accounts.
	- By default, Organization Management Account is the Security Hub Administrator. -> Ability to have a designated Security Hub administrator from member accounts.
- AWS Config must be enabled.
	- Security Hub uses AWS Config to perform its security checks.
	- Must be enabled on all accounts(Security Hub doesn't manage AWS Config).

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221153623.png]]

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250221160710.png]]


---

## Security Standards
- Security Hub generates findings and continuous checks against the rules in a set of supported security standards. -> It supports CIS AWS Foundations, PCI DSS, AWS Foundational Security Best Practices...
- Ability to enable/disable a security standard.

---

## Integration with [[AWS/Security/Amazon GuardDuty|Amazon GuardDuty]]
- Automatically enabled when Security Hub is enabled(can be disabled).
- GuardDuty will send findings to Security Hub. -> Findings are sent in AWS Security Finding Format(ASFF).
- Findings are usually sent within 5 minutes.
- Archiving a GuardDuty finding will NOT update the finding in Security Hub.

---

## Findings
- Security Hub consumes findings using AWS Security Finding Format(ASFF) format.
- Automatically updates and deletes findings.
- Findings past 90 days are automatically deleted.
- Filter by Region, Integration, Security Standard, Insights.

---

## Insights
- Collection of related findings that identifies a security area that requires attention and intervention.
- Example: Insight points out EC2 instances that are subject of findings that detect poor security practices.
- Brings findings from across finding providers.
- Each Insight defined by a Group By statement and optional Filters.
- Built-In Managed Insights -> Return results only if you enabled related product integration or security standard(can not edit of delete).
- Custom Insights -> Track issues specific to your environment.

---

## Custom Actions
- Helps you automate Security Hub with EventBridge.
- Allows you to create actions for response and remediation to selected findings within the Security Hub Console.
- EventBridge event type is Security Hub Findings - Custom Action.
