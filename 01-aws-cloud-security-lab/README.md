# AWS Cloud Security Lab

## Overview

This project demonstrates the implementation of security controls within an AWS environment. The lab focuses on identity and access management, secure cloud storage, least-privilege permissions, security logging, and access analysis.

The environment was intentionally configured and tested to observe how AWS security controls respond to authorized and unauthorized actions.

## Technologies Used

- Amazon Web Services (AWS)
- AWS IAM
- Amazon S3
- AWS CloudTrail
- IAM Access Analyzer
- AWS CLI
- PowerShell
- JSON
- Git / GitHub

## Security Controls Implemented

### IAM & Least Privilege

Created IAM users and configured permissions to control access to AWS resources.

Tested least-privilege permissions by attempting actions that were not explicitly permitted and analyzing the resulting `AccessDenied` responses.

### Secure S3 Storage

Configured an Amazon S3 bucket with:

- Block Public Access
- Server-side encryption (SSE-S3)
- Bucket versioning
- Controlled IAM access

Uploaded sample data to test storage security and access controls.

### CloudTrail Logging

Configured an AWS CloudTrail trail to record activity within the AWS environment.

Created a dedicated S3 bucket for CloudTrail logs and configured the required bucket policy to allow CloudTrail log delivery.

Verified that CloudTrail logging was active and reviewed recorded events.

### IAM Access Analyzer

Configured IAM Access Analyzer to evaluate resource access and identify potential external access to AWS resources.

## Security Testing

The lab included intentional testing of security controls, including:

- Attempting an unauthorized S3 object upload
- Investigating `AccessDenied` errors
- Reviewing IAM permissions
- Reviewing CloudTrail events
- Testing S3 resource policies
- Analyzing external access configurations

## What I Learned

This project provided hands-on experience with AWS security beyond simply deploying cloud resources. It demonstrated how IAM policies, resource policies, logging, encryption, and access analysis work together to protect cloud environments.

It also provided practical experience troubleshooting permission issues and investigating AWS activity using security logs.

## Project Status

🚧 In Progress