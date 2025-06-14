
# VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment
The project architecture, illustrated in the diagram below, is built around a Virtual Private Cloud (VPC) with both public and private subnets strategically spread across two Availability Zones to enhance fault tolerance.

Each public subnet hosts a NAT gateway for outbound internet access and a load balancer node to efficiently manage incoming traffic.

The application servers are deployed within the private subnets and are managed by an Auto Scaling group, which handles their automatic provisioning and termination based on demand. These servers receive traffic from the load balancer and can initiate outbound internet connections through the NAT gateway when needed.

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/0a8929ac15c7f9611ff484f667e7fbc038ece160/Images/diagram.png)

## Steps :
### Step 1 :
#### Create the VPC :
1. Open the Amazon VPC console by visiting https://console.aws.amazon.com/vpc/.
2. On the dashboard, click on "Create VPC."
3. Under "Resources to create," select "VPC and more."
4. Configure the VPC:
   a. Provide a name for the VPC in the "Name tag auto-generation" field.
   b. For the IPv4 CIDR block, leave it as default suggestion.
5. Configure the subnets:
   a. Set the "Number of Availability Zones" to 2 for increased resiliency across multiple Availability Zones.
   b. Specify the "Number of public subnets" as 2.
   c. Specify the "Number of private subnets" as 2.
   d. For NAT gateways, choose "1 per AZ" to enhance resiliency.
   e. For VPC endpoints, you can choose "None" .
   f. Regarding DNS options, clear the checkbox for "Enable DNS hostnames."

Once you've configured all the settings, click "Create VPC."

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/1.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/2.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/3.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/4.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/5.png)

### Step 2:
#### Creating the Auto Scaling Group :

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/6.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/7.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/8.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/9.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/10.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/11.png)
Scroll dow and click next

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/12.png)
Scroll dow and click next


![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/13.png)
Scroll dow and click next


![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/14.png)


![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/15.png)







