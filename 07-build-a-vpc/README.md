[README (1).md](https://github.com/user-attachments/files/31065477/README.1.md)
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-vpc)

**Author:** Olaoluwa Olayinka Olokunde   
**Email:** olokunde.o@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create and configure an Amazon Virtual Private Cloud (VPC), set up a public subnet, and attach an internet gateway. I'm doing this project to learn the fundamentals of AWS networking, understand how to build secure and isolated cloud networks, and gain hands-on experience with configuring network infrastructure in AWS.

### What is Amazon VPC?

### Personal reflection

---

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will access the Amazon VPC console and create a new Virtual Private Cloud (VPC) because it provides a secure and isolated virtual network where I can deploy and manage AWS resources. Creating the VPC is the foundation for configuring networking components such as subnets, route tables, and internet gateways.

### How VPCs work

VPCs are logically isolated virtual networks within AWS that allow you to securely launch and manage cloud resources. They provide control over networking by enabling you to define IP address ranges, create subnets, configure routing, and manage access, ensuring your resources communicate securely and remain isolated from other AWS customers.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my account ever since my AWS account was created. This is because AWS automatically provisions a default VPC to provide a ready-to-use network environment, allowing users to launch and connect resources like EC2 instances without first creating and configuring a custom VPC. This makes it easier to get started with AWS services while learning the platform.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To set up my VPC, I had to define an IPv4 CIDR block, which is a range of IP addresses that the VPC can use for its resources. The CIDR block determines the size of the network and the number of available IP addresses, allowing me to organize and allocate addresses for subnets and other AWS resources within the VPC.


---

## Subnets

### What I did in this step

In this step, I will create a subnet within my VPC because subnets divide the VPC into smaller network segments, allowing me to organize AWS resources and control how they communicate. Creating a subnet is an essential step in designing a secure and well-structured network.


### Creating and configuring subnets

Subnets are smaller network segments within a VPC that allow me to organize AWS resources and control how they communicate. There are already subnets existing in my account, one for every Availability Zone in my AWS Region, because AWS automatically creates default subnets when it provisions the default VPC.


### Public vs private subnets

The difference between public and private subnets is that public subnets can communicate with the internet, while private subnets are isolated from direct internet access. For a subnet to be considered public, it has to be associated with a route table that contains a route to an internet gateway, allowing resources in the subnet to access the internet.


![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

Once I created my subnet, I enabled auto-assign public IPv4 addresses. This setting makes sure that any EC2 instance launched in the subnet automatically receives a public IP address, so that it can communicate with the internet without requiring a public IP address to be assigned manually.

---

## Internet gateways

### What I did in this step

In this step, I will create and attach an internet gateway to my VPC because it provides a connection between my VPC and the public internet. This allows resources in my public subnet, when properly configured, to send and receive internet traffic.


### Setting up internet gateways

Internet gateways are AWS networking components that connect a Virtual Private Cloud (VPC) to the public internet. They enable resources in public subnets to send and receive internet traffic when the appropriate route table and public IP address configurations are in place.


Attaching an internet gateway to a VPC means the VPC can communicate with the public internet, allowing resources in public subnets to send and receive internet traffic when they have the appropriate route table and public IP address. If I missed this step, resources in my VPC would not be able to access the internet or be accessible from the internet, even if they were launched in a public subnet.


![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will use AWS CloudShell and the AWS CLI to create a VPC, subnet, and internet gateway instead of using the AWS Management Console. I'm doing this because it helps me learn how to automate AWS networking tasks, work more efficiently, and gain hands-on experience with command-line tools commonly used by cloud engineers and system administrators.


### Exploring CloudShell and CLI

VPC resources could also be created with CloudShell, which is a browser-based shell environment in the AWS Management Console that allows me to run commands directly in AWS. CLI is the Command Line Interface, which allows me to create, manage, and update AWS resources using commands instead of navigating through the AWS Console.

### Debugging my setup

To set up a VPC or a subnet, you can use the AWS CLI command with the appropriate parameters. Make sure to avoid errors by including the required VPC ID and a valid CIDR block that falls within the VPC's CIDR range. In this case, the error occurred because the subnet command was missing the `--cidr-block` parameter, which tells AWS which IP address range to allocate to the subnet.


![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-networks-vpc_9b2465411)

### Comparing CloudShell vs AWS Console

Compared to using the AWS Console, an advantage of using commands is that CloudShell is faster and makes it easier to automate and repeat tasks. An advantage of using the Console is that it provides a visual interface that makes it easier to understand and verify the resources being created. Overall, I preferred using the AWS Console because it was easier to follow as I learned the different VPC components.

---

---
