# VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment
The project architecture, illustrated in the diagram below, is built around a Virtual Private Cloud (VPC) with both public and private subnets strategically spread across two Availability Zones to enhance fault tolerance.

Each public subnet hosts a NAT gateway for outbound internet access and a load balancer node to efficiently manage incoming traffic.

The application servers are deployed within the private subnets and are managed by an Auto Scaling group, which handles their automatic provisioning and termination based on demand. These servers receive traffic from the load balancer and can initiate outbound internet connections through the NAT gateway when needed.

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/0a8929ac15c7f9611ff484f667e7fbc038ece160/Images/diagram.png)
