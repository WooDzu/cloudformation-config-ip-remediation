# AWS CloudFormation for SSM - AutomationDisableIncomingSSH

## What does this template do?

This document automates revoking incoming SSH access on port 22 for EC2 security groups.
It can be deployed on a standalone AWS account as well as across AWS Organization via Stack Sets.
It creates a Config Rule which evaulates changes to Security Groups via Lambda Function which
decides if the Secuirity Group is complient with the rule. Non-compliant groups can be automatically
remediated via Systems Manager Automation that will update the security group to remove any rules
that allow SSH traffic (TCP/22).

If any of these ingress rules should be persistemd, simply add "keep" to the description of that rule.

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
