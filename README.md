# AWS CloudFormation for SSM - AutomationDisableIncomingSSH

## What does this template do?


ChatGPT
This document details an automated process for disabling incoming SSH (port 22) access in EC2 security groups. It is designed for both individual AWS accounts and broader AWS Organizations through Stack Sets implementation. The system establishes a Config Rule that monitors security group changes using a Lambda Function. This function assesses whether the security groups adhere to the specified rule. In cases of non-compliance, an automatic correction is executed using Systems Manager Automation, which adjusts the security group to block any SSH traffic (TCP/22).

To retain any specific inbound rules, add "keep" to the rule's description.


![description](https://github.com/WooDzu/cloudformation-config-ip-remediation/assets/2228236/e317360f-d2fe-4612-9dea-9da3755dc101)


## Input Parameters
* AutomaticallyRemediate: (boolean) Automates revoking SSH ingress from Security Groups as soon as it is created

## IAM permissions created and used:

- logs:CreateLogGroup
- logs:CreateLogStream
- logs:PutLogEvents
- ec2:DescribeSecurityGroups
- ec2:RevokeSecurityGroupIngress
- config:PutEvaluations
