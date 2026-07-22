<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Threat Detection with GuardDuty

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-guardduty)

**Author:** olokunde.o@gmail.com  
**Email:** olokunde.o@gmail.com

---

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_v1w2x3y4)

---

## Introducing Today's Project!

### Tools and concepts

The services I used were Amazon GuardDuty, CloudFormation, EC2, S3, CloudShell, IAM, CloudFront, and VPC. Key concepts I learnt include threat detection, SQL injection, command injection, IAM credential theft, malware detection, S3 security, incident investigation, and using GuardDuty findings to identify and respond to security threats.

### Project reflection

This project took me approximately 3-4 hours to complete. The most challenging part was understanding and executing the simulated attacks while interpreting GuardDuty findings. It was most rewarding to see GuardDuty successfully detect the attacks and malware, reinforcing how AWS security services help protect cloud environments.

I completed this project to strengthen my hands-on AWS cloud security skills and gain practical experience with Amazon GuardDuty. It definitely met my goals by helping me understand real-world attack techniques, how GuardDuty detects threats, and how to investigate security findings—skills that are directly relevant to SOC Analyst, Cloud Security, and Cybersecurity Analyst roles.

---

## Project Setup

To set up for this project, I deployed a CloudFormation template that launches a secure AWS environment. The three main components are the web application infrastructure (EC2, VPC, CloudFront, and networking), an S3 bucket for storing application data, and AWS GuardDuty for continuous threat detection and security monitoring.

The web app deployed is called OWASP Juice Shop. To practice my GuardDuty skills, I will simulate attacks against the application, monitor GuardDuty for threat detections, investigate the generated findings, and learn how AWS identifies and responds to suspicious activity in a cloud environment.

GuardDuty is AWS's AI intelligent threat detection service that uses machine learning and threat intelligence to identify suspicious activity in an AWS environment. In this project, it will monitor the deployed infrastructure, detect simulated attacks against the web application, and generate security findings for investigation.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_n1o2p3q4)

---

## SQL Injection

The first attack I performed on the web app is SQL injection, which means I manipulated the login query to bypass authentication. SQL injection is a security risk because it can give attackers unauthorized access to sensitive data if user input is not properly validated.

My SQL injection attack involved entering ' or 1=1;-- into the login field. This means the login query always evaluated as true, allowing authentication to be bypassed without valid credentials.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_h1i2j3k4)

---

## Command Injection

In this step, I will exploit a command injection vulnerability to retrieve the EC2 instance's IAM credentials because it demonstrates how attackers can execute malicious commands on a vulnerable server and gain unauthorized access to cloud resources.

To run command injection, I entered a malicious script into the Username field and saved the changes. The script executed on the vulnerable server, retrieved the EC2 instance's IAM credentials, and stored them in a publicly accessible file, demonstrating the impact of unsanitized user input.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_t3u4v5w6)

---

## Attack Verification

To verify the attack's success, I opened the credentials.json file created by the injected script. The credentials page showed me temporary AWS IAM credentials, including the Access Key ID, Secret Access Key, session token, and expiration time, confirming that the command injection attack successfully exposed sensitive cloud credentials.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_x7y8z9a0)

---

## Using CloudShell for Advanced Attacks

The attack continues in CloudShell, because it lets me use the stolen AWS credentials to run CLI commands and simulate how an attacker could access cloud resources and sensitive data.

In CloudShell, I used wget to download the exposed credentials.json file from the vulnerable web application. Next, I ran a command using cat and jq to display and format the stolen AWS credentials, making them easy to read and verify.

I then set up a profile, called stolen, to use the compromised AWS credentials for authentication. I had to create a new profile because it allowed me to simulate an attacker accessing AWS resources with the stolen credentials instead of my own account permissions.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_j9k0l1m2)

---

## GuardDuty's Findings

After performing the attack, GuardDuty reported a finding within about 15 minutes. Findings are security alerts that identify suspicious or potentially malicious activity in an AWS environment, helping security teams investigate and respond quickly.

GuardDuty's finding was called UnauthorizedAccess:IAMUser/InstanceCredentialExfiltration.InsideAWS, which means the EC2 instance's IAM credentials were used suspiciously from another AWS account. Anomaly detection was used because GuardDuty identified this activity as unusual compared to the instance's normal behavior.

GuardDuty's detailed finding reported that an EC2 instance's IAM credentials were used from another AWS account to access an S3 bucket and retrieve a sensitive file. It also identified the affected resource, the suspicious action, and the attack's source location, helping with investigation and response.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_v1w2x3y4)

---

## Extra: Malware Protection

For my project extension, I enabled Amazon GuardDuty Malware Protection for S3 to automatically scan files uploaded to my S3 bucket for malicious content. Malware is harmful software designed to steal data, damage systems, or disrupt normal operations, and GuardDuty helps detect it before it can cause harm.

To test Malware Protection, I uploaded an EICAR test file to my protected S3 bucket. The uploaded file won't actually cause damage because it's a harmless test file designed to safely verify that GuardDuty can detect malware.

Once I uploaded the file, GuardDuty instantly triggered an Object:S3/MaliciousFile finding. This verified that Malware Protection successfully scanned the S3 object and detected the EICAR test file as a simulated malware threat.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-guardduty_sm42x3y4)

---
