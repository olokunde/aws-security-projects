<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Security Monitoring System

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-monitoring)

**Author:** Olaoluwa Olayinka Olokunde   
**Email:** olokunde.o@gmail.com

---

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_reghtjy)

---

## Introducing Today's Project!

In this project, I will demonstrate my ability to securely store sensitive information using AWS Secrets Manager, monitor access with AWS CloudTrail, and build a real-time monitoring and alerting solution using Amazon CloudWatch and Amazon SNS. I'm doing this project to learn cloud security best practices, improve my hands-on AWS skills, and gain practical experience in securing and monitoring cloud resources.

### Tools and concepts

Services I used were AWS Secrets Manager, AWS CloudTrail, Amazon S3, Amazon CloudWatch, and Amazon SNS. Key concepts I learnt include secure secret management, audit logging, log analysis, metric filters, CloudWatch alarms, and automated email notifications for real-time security monitoring.

### Project reflection

It took me approximately 2–3 hours to complete this project, including setting up the services, testing the monitoring workflow, troubleshooting notification issues, and validating the end-to-end alerting system.

---

## Create a Secret

Secrets Manager is a service that securely stores and manages sensitive information such as passwords, API keys, and database credentials. You could use Secrets Manager to protect application secrets, control who can access them with IAM permissions, and securely retrieve them when needed instead of hardcoding them into your applications.


To set up for my project, I created a secret called TopSecretInfo that contains the key The Secret is and a custom value (a random secret or hot take). This secret is securely stored and encrypted in AWS Secrets Manager, making it accessible only to authorized users and applications.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_o5p6q7r8)

---

## Set Up CloudTrail

CloudTrail is an AWS service that records everything that happens in your AWS account, such as who accessed a resource, what they did, and when they did it. I set up a trail to collect and save these activity logs in an S3 bucket so I can monitor access to my secret and review account activity whenever needed.

CloudTrail events include types like Management events, which record changes to AWS resources; Data events, which track actions on resources such as S3 objects; Insights events, which detect unusual account activity; and Network activity events, which monitor network-related changes.

### Read vs Write Activity

Read API activity involves viewing information without making any changes, such as listing or describing AWS resources. Write API activity involves creating, updating, deleting, or retrieving sensitive information like a secret value. For this project, we need both Read and Write activities enabled so CloudTrail records all access to our secret and any changes made to it.

---

## Verifying CloudTrail

I retrieved the secret in two ways: First through the AWS Secrets Manager console by selecting Retrieve secret value. Second using the AWS CLI in CloudShell with the aws secretsmanager get-secret-value command, which returned the secret in JSON format. Both methods generated CloudTrail events that can be used to monitor access to the secret.

To analyze my CloudTrail events, I visited the Event history page in CloudTrail and filtered the events by secretsmanager.amazonaws.com. I found GetSecretValue events, which showed that my secret had been accessed. This tells me that CloudTrail is successfully recording secret access, allowing me to monitor and audit who accessed the secret and when.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_s8t9u0v1)

---

## CloudWatch Metrics

CloudWatch Logs is an AWS service that collects and stores logs from AWS services and applications in one place. It's important for monitoring because it lets you analyze logs, track important events, create metrics, and set up alarms to notify you when activities such as secret access occur.

CloudWatch Logs is an AWS service that collects and stores logs from AWS services and applications in one place. It's important for monitoring because it lets you analyze logs, track important events, create metrics, and set up alarms to notify you when activities such as secret access occur.

A CloudWatch metric is a numerical value that tracks specific activities or performance over time. When setting up a metric, the metric value represents what is recorded when the filter finds a matching event. In this project, the value is 1, so the count increases each time someone accesses the secret. The default value is used when no matching event is found, and it is set to 0 so periods with no secret access are still recorded.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_a9b0c1d2)

---

## CloudWatch Alarm

A CloudWatch alarm is a monitoring tool that watches a metric and sends an alert when it reaches a defined limit. I set my CloudWatch alarm threshold to trigger when the SecretIsAccessed metric is greater than or equal to 1 within a 5-minute period, so the alarm will notify me whenever my secret is accessed.

I created an SNS topic along the way. An SNS topic is an AWS messaging channel that sends notifications to one or more subscribers when an event occurs. My SNS topic is set up to send an email alert whenever the CloudWatch alarm detects that my secret has been accessed.

AWS requires email confirmation because it needs to verify that the email address belongs to the person who wants to receive notifications. This helps prevent unauthorized subscriptions, spam, and unwanted emails from being sent to people without their permission.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_fsdghstt)

---

## Troubleshooting Notification Errors

To test my monitoring system, I retrieved the value of my TopSecretInfo secret again in AWS Secrets Manager to trigger the CloudWatch alarm. The results were that the secret access was recorded, but I did not receive the expected email notification. This indicated that the monitoring system needed additional troubleshooting to identify why the alarm or notification was not triggered.

When troubleshooting the notification issues I:

Checked that CloudTrail was recording GetSecretValue events in the Event History.
Verified that CloudWatch Logs were enabled for my CloudTrail trail and that logs were being sent successfully.
Confirmed the metric filter was correctly configured to match GetSecretValue events and update the SecretIsAccessed metric.
Reviewed the CloudWatch alarm settings, including the metric, threshold (Greater than or Equal to 1), evaluation period, and alarm state.
Verified the Amazon SNS topic and email subscription, making sure the subscription was confirmed and the alarm was configured to send notifications to the correct SNS topic.

I initially didn't receive an email because my monitoring configuration was not fully connected, so the CloudWatch alarm was not successfully triggering an SNS notification. The key solution was to verify the CloudTrail logs, ensure the CloudWatch metric filter and alarm were correctly configured, and confirm that my SNS email subscription was active. Once everything was configured correctly, the notification system worked as expected.

---

## Success!

To validate that my monitoring system works, I retrieved my secret again in AWS Secrets Manager and checked the CloudWatch alarm. After a few minutes, the alarm changed to the In alarm state, confirming that the secret access was detected. I also received an email notification from Amazon SNS with the subject ALARM: "SecretIsAccessedAlarm", which confirmed that my monitoring and notification system was working correctly.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_ageraergearge)

---

## Comparing CloudWatch with CloudTrail Notifications

In a project extension, I updated my CloudTrail configuration to send notifications directly to my existing Amazon SNS topic because I wanted to receive alerts whenever CloudTrail delivered new log files. This improves monitoring by keeping me informed about logging activity while my CloudWatch alarm continues to notify me when my secret is accessed.

After enabling CloudTrail SNS notifications, my inbox received several email notifications from AWS because CloudTrail sent a notification each time it delivered a new log file to my S3 bucket. In terms of usefulness, I thought these emails were helpful for confirming that logging was working, but they can quickly become overwhelming. For monitoring specific events like secret access, CloudWatch alarms are more useful because they only send alerts when the conditions I defined are met.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-monitoring_d7e8f9g0)

---

---
