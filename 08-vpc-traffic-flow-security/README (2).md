<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-security)

**Author:** olokunde.o@gmail.com  
**Email:** olokunde.o@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a virtual network in AWS that allows you to create and manage resources in an isolated and secure environment, and it is useful because it gives you control over networking, IP addresses, subnets, routing, and security for your AWS resources.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a secure virtual network with a public subnet, route table, internet gateway, security group, and network ACL, allowing me to control how traffic flows to and from my AWS resources.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how many different networking and security components, such as route tables, internet gateways, security groups, and network ACLs, work together to make a VPC secure and accessible.

### This project took me...

This project took me about 2–3 hours to complete, including the time I spent troubleshooting and understanding the different VPC components.

---

## Route tables

Route tables are sets of rules that control where network traffic goes within a VPC.

Routes tables are needed to make a subnet public because they provide a route from the subnet to an Internet Gateway, allowing resources in the subnet to communicate with the internet.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target, which mean the destination is the IP address range the traffic is trying to reach, while the target is where the traffic is sent to reach that destination.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of Internet Gateway (NextWork IG).

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are virtual firewalls that control inbound and outbound traffic to resources in a VPC based on rules such as IP addresses, protocols, and port numbers.

### Inbound vs Outbound rules

Inbound rules are rules that control the traffic allowed to enter a resource. I configured an inbound rule that allows HTTP traffic on port 80 from anywhere using IPv4 (0.0.0.0/0), allowing users on the internet to access web resources associated with the security group.

Outbound rules are rules that control the traffic allowed to leave a resource. By default, my security group's outbound rule allows all traffic to all destinations, meaning resources associated with the security group can communicate with the internet and other networks unless the outbound rules are specifically restricted.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are rules that control inbound and outbound traffic at the subnet level. They provide an additional layer of security by allowing or denying data packets entering or leaving a subnet based on defined rules.

### Security groups vs. network ACLs

The difference between a security group and a network ACL is that a security group controls traffic at the resource level, such as an EC2 instance, while a network ACL controls traffic at the subnet level. Security groups are stateful, meaning return traffic is automatically allowed, while network ACLs are stateless and require separate inbound and outbound rules.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all traffic from all destinations, unless the rules are specifically modified to restrict or deny certain traffic.

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all traffic until you add rules that explicitly allow specific types of traffic.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

---

---
