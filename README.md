# ansible-aws-vpc
Create a VPC in AWS using Ansible

These ansible playbook creates a simple VPC.
The AWS VPC created will include the following components
1. vpc (vpc_net)
2. subnet (ec2_vpc_subnet)
3. router (ec2_vpc_router_table)
4. internet gateway (ec2_vpc_igw)
5. security group (ec2_group)
6. ec2 instance (ec2)

Prequisites:
* IAM User with the required permission
* Boto installed (Ansible uses the Boto Python library to handle AWS management)


1. VPC:
To create a VPC, we have to use the ec2_vpc_net module. We will register the module returned data in the “vpc” variable

2. Creating a subnet and associating it with an Internet Gateway
We need an IGW so that our public subnet can access the internet.
In our subnet, we have set map_public to “YES”. This means instances created in this subnet is associated with a public IP address.

3. Routing traffic to IGW and creating a security group
Here, we would need to route the traffic to the IGW via the route table and create a security group.

4. Creating an EC2 Key Pair and an EC2 instance
Create an EC2 Key Pair and an EC2 instance.
Key points:
* if you already have an EC2 key pair, skip the EC2 key pair and update the key_name with the name of the key pair
* exact_count is important! It determines the number of instances is created
* Image ID can be found on AWS Marketplace
