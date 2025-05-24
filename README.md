AWS IAM Misconfiguration - Threat Hunting Toolkit

Overview
This repository contains threat intelligence and detection content related to recent findings on over-permissive default IAM roles in AWS services such as SageMaker, Glue, EMR, and Lightsail.

These default roles can unintentionally grant broad permissions—like AmazonS3FullAccess or PassRole—which attackers can exploit to move laterally, escalate privileges, and access sensitive data within the same AWS account.

Contents
2025-05-24-IOCs.txt
A list of key indicators related to IAM misconfiguration, including default role patterns, risky policies, API calls, and involved AWS services.

Sample KQL Queries.txt
Sample KQL queries to detect abuse of default IAM roles across AWS CloudTrail data via Microsoft Sentinel or other Kusto-compatible tools.
Example Threat Scenario
An EC2 instance running under a default SageMaker execution role.
The role has AmazonS3FullAccess and PassRole.
The attacker uploads a malicious ML model or Glue job.
Lateral movement occurs to other AWS services with minimal logging or alerts.
Mitigation Guidance
Audit existing IAM roles for excessive permissions.
Remove unnecessary default roles or limit their scope.
Apply least privilege across all IAM policies.
Monitor for unexpected use of sensitive API actions (PassRole, AssumeRole, GetSecretValue, etc).
References
The Hacker News Article
AWS IAM Documentation: https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html
