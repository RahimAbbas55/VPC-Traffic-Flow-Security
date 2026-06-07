<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** irahimsindhu@gmail.com  
**Email:** irahimsindhu@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a virtual private network in the cloud that lets you isolate and control your networking environment; it’s useful because it provides secure, customizable networking for AWS resources.

### How I used Amazon VPC in this project

I used Amazon VPC to create and configure isolated subnets, control traffic with route tables and security groups, and manage how resources communicate with each other and the internet.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the absolute simplicity and clear guidance.

### This project took me...

This project took me 50 minutes to complete.

---

## Route tables

Route tables act like navigation instructions for network traffic. They contain rules that direct packets destined for specific IP address ranges to the appropriate destination, such as a subnet, gateway, or router.

Routes tables are needed to make a subnet public because the route table contains a route (typically 10.0.0.0/16) to an Internet Gateway, which allows the traffic to reach and return to internet.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Destination specifies the IP range where traffic is headed, while Target specifies the next hop (such as a router, gateway, or network interface) that the traffic should be sent to.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of of 10.0.0.0/16 and the target is my public subnet located inside my VPC.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are the rules that monitor the inbound and the outbound traffic that can access our instance and the data that can be sent over to any third-party service from our instance.

### Inbound vs Outbound rules

Inbound rules define what incoming traffic is allowed to reach our instance(such as a server or any other instance).
The inbound rule of my security group are:
- Protocol: TCP
- Type: HTTP
- Port: 80
- Sourcee: 10.0.0.0/0
- IP Version: Ipv4


Outbound rules define what outgoing traffic a resource is allowed to send to the other destinations like a server, third-party server or an instance.

Outbound rules of my security group are:
- Protocol: All
- Type: All traffic
- Port: All
- Source: 0.0.0.0/0
- IP Version: Ipv4

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are used to set broad traffic rules that apply to an entire subnet. For example, blocking incoming traffic from a particular range of IP addresses or denying all outbound traffic to certain ports.

### Security groups vs. network ACLs

Security Groups are attached to individual resources (such as EC2 instances), whereas Network ACLs are attached to subnets and apply to all resources within those subnets.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all traffic whether it be inbound or outbound. 
The details of the inbound and outbound rules is:
- Rule Number: 100
- Type: All Traffic
- Protocol: All
- Source: 0.0.0.0/0
- Allow/Deny: Allow

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all the traffic whether it be outbound or inbound.
The details of the inbound and outbound rules is:
- Rule Number: *
- Type: All Traffic
- Protocol: All
- Source: 0.0.0.0/0
- Allow/Deny: Deny

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPC, Internet Gateways. Instead of my usual region, I used "eu-west-3".  Teams would use multiple regions:
- To improve availability, 
- Reduce latency for users in different regions, 
- Ensure disaster recovery if one server goes down.

EC2 Global View is a tool where you can find all the available Amazon Web Services EC2 resources across regions. I could even narrow down my search by region, instance state, tags, or instance type. Without EC2 Global View, you'd have to switch between regions one by one manually to find and compare resources.

You would use Amazon Web Services EC2 Global View when you need a single, centralized view of EC2 resources across multiple regions, especially to find, compare, or audit instances quickly without switching regions manually.

![Image](http://learn.nextwork.org/affectionate_olive_majestic_marjoram/uploads/aws-networks-security_b03ea6162)

---
