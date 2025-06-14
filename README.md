
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
4. Configure the VPC:<br>
   a. Provide a name for the VPC in the "Name tag auto-generation" field.<br>
   b. For the IPv4 CIDR block, leave it as default suggestion.<br>
5. Configure the subnets:<br>
   a. Set the "Number of Availability Zones" to 2 for increased resiliency across multiple Availability Zones.<br>
   b. Specify the "Number of public subnets" as 2.<br>
   c. Specify the "Number of private subnets" as 2.<br>
   d. For NAT gateways, choose "1 per AZ" to enhance resiliency.<br>
   e. For VPC endpoints, you can choose "None" .<br>
   f. Regarding DNS options, clear the checkbox for "Enable DNS hostnames."<br>


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
Scroll dow and click skip


![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/14.png)


![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/15.png)


## Step 3 :
#### Creating the Bastion Host :

1. Launch Instance as Specified below .

   
![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/e6a86965a90490a7a1c3001120ad4ef55e533b16/Images/28.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/07d750c51a3e148dd4228d0349670162189ad1ba/Images/26.png)


![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/07d750c51a3e148dd4228d0349670162189ad1ba/Images/27.png)

### Step 4: 
#### SSH into Private Instance:
1.Start SSH agent (Linux/macOS)
        ssh-add /path/to/bastion-key.pem
2.SSH into Bastion and hop to private instance
        ssh -A ec2-user@<Bastion-Public-IP>
        ssh ec2-user@<Private-Instance-Private-IP>
        
Replace ec2-user with appropriate username (e.g., ubuntu, admin, etc.).

a. We will deploy our application on one of the private instances to test the load balancer. <br>
b. After successfully SSHing into the private instance, create an HTML file using the Vim text editor:

               vim demo.html

             
. This will open the Vim editor. Copy and paste any HTML content you like into the editor.
     For example:
     
          html
          <!DOCTYPE html>
          <html>
          <head>
          <title>Page Title</title>
          </head>
          <body>

          <h1>Hello world</h1>
          </body>
          </html>
      
      After pasting the content, save the file by pressing 'Esc' to exit insert mode and then entering `:w` to save.<br>
     Finally, start a Python HTTP server on port 8000 to deploy your application on the private instance:

                 python3 -m http.server 8000


   ### Step 4 :
#### Creating the Load Balancer :

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/16.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/17.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/18.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/19.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/20.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/21.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/22.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/23.png)

![image](https://github.com/Ahmed1337a/VPC-Architecture-with-Public-and-Private-Subnets-for-Production-Environment/blob/f4b351c1423d762ec35620cc5ce769676d8c3780/Images/24.png)




Now We Successfully deployed Application securely in Private instance , We can access it through Internet using Load Balancer Securely .



                 

      ```        











