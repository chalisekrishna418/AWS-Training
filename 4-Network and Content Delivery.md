# Network and Content Delivery

## Networking Concepts to know earlier

1.  Network
2.  Internet Protocol (IP)
3.  Static IPs and DHCP
4.  Classless Inter Domain Routing (CIDR)
5.  Subnetting
6.  Routing and Route Tables
7.  Public and Private Network
8.  Network Peering
9.  Virtual Private Network (VPN)
10. Firewalls
11. NAT
12. Domain Name System (DNS) (Public and Private DNS)
13. CDN

### 1. Network

- Interconnected computing devices (aka Nodes) that can exchange data and share resources with each other using common protocols.
- The nodes of a computer network may include personal computers, servers, networking hardware, or other specialized or general-purpose hosts.
- The nodes in a network identified is by network addresses (Telephone Number, IP, Mac Address), and may also have hostnames.

### 2. Internet Protocol (IP)

- IP address serves two main functions: network interface identification and location addressing.
- There are two different variants of IP: IPv4 and IPv6.
- IPv4 defines an IP address as a 32-bit number (Eg: 192.168.0.1) whereas IPv6 defines an IP address as a 128-bit hexadecimal address (Eg: )
- IPV4 has 3 classes (i.e. A,B, C) but IPV6 is classless.

> IPv4 has limited number of addresses i.e. ~4.294 x 10<sup>9</sup> Addresses where as IPV6 has 3.4 x 10<sup>38</sup> unique IP addresses. IPv6 was introduced in 1998 because IPv4 would not be sufficient for allocating unique IP Address to devices in the future and will eventually run out.

- We will continue this training with IPv4 as it will serve our purpose. IP will refer to IPv4 from now on. But please please please also learn about IPv6 if you want to evolve in the future. Its very important.

![640px-IPv4_address_structure_and_writing_systems-en.svg.png](:/3742186e1b3444fb8925ed4207a917a1)

### 3. Static IPs and DHCP

- With a static IP address, this unique number stays the same.
- With a DHCP (dynamic host configuration protocol) address, this number is automatically assigned to each device from a pool of available numbers on the network.
- Static is permanent; Dynamic is temporary.

### 4. Classless Inter Domain Routing (CIDR)

- CIDR was introduced with the goal of slowing down the growth of routing tables on routers across the Internet, and to help slow the rapid exhaustion of IPv4 addresses.
- IP addresses are described as two groups of bits splitted by Subnet Mask in the address:
    - **Most Significant Bits (MSB):** These are the network prefix, which identifies a whole network or subnet, and
    - **Least Significant (LSB):** This identifies the host, which specifies a particular interface of a host on that network.

> A subnet mask determines which part of IP defines the network prefix and which defines the host interface of a network. It is a 32 bit number like 255.255.255.0

> A CIDR Block functions same as Subnet Mask but it usually noted down as a number value than the 32-bit IP address like number.

### 5. Subnetting

- A subnet also called sub Network i.e. a network inside a network.
- Subnets make networks more efficient by:
    - Making more IP address available within a network
    - Making the traffic travel shorter distance without passing through unnecessary routers to reach its destination.
- Subnet Masks or CIDR blocks are used to create and define subnets.
- As Subnet is like a network except it is smaller in size than the main network, you can also create routes for subnets.

### 6. Routing and Route Tables

- Routing is the process of selecting a path for traffic in a network or between or across multiple networks.
- A route table determines which way a network packet will travel through/in a network.
- **A default route** is the route that takes effect when no other route is available for an IP destination address.

### 7. Public and Private Network

- A public network is a network to which anyone can connect i.e. IP for a device in a network can be included in the route table of any device no matter of the type of network.
- A private network is the network which is accessible within a network i.e. IP for a network can be included only in the the route table of that particular network.

### 8. Network Peering

- Peering is a method that allows two networks to connect and exchange traffic directly without having to pay a third party to carry traffic across the Internet.
- For Peering, the participating network should not have a same or coinciding CIDR. It will create a condition called IP Conflict and the network packet wont route as expected.

### 9. Virtual Private Network (VPN)

- VPN enables us to establish a protected and secured network connection among two networks.
- You can setup VPN as the gateway to interact with another network by defining routes.
- To setup VPN, you need to avoid IP conflict i.e. the participating network should not have a same or coinciding CIDR.
- If devices in two different network want to connect using VPN, they must have atleast one network that is common among them or they have to use internet to establish a connection.

### 10. Firewalls

- **A firewall** is a network security device which monitors incoming and outgoing network traffic and decides whether to allow or block specific traffic based on a defined set of security rules.
- A firewall can be a software or hardware.
- Firewall is a crucial infrastructure that can be used to prevent security breaches.

### 11. Network Address Translation (NAT)

- Network Address Translation (NAT) is a process that enables one, unique IP address to represent an entire group of computers.
- NAT is used in private networks to access the internet.
- Although NAT is used for Private Networks but it should always be deployed in a public subnet.

### 12. Domain Name System (DNS)

- It is the phonebook of the Internet.
- DNS translates domain names to IP addresses so browsers can load Internet resources so it eliminate the need for humans to memorize IP addresses such as 8.8.8.8.
- There are 4 different Types of DNS Servers:
    a. DNS Recursor
    b. Root Nameserver
    c. TLD Nameserver
    d. Authoritative Nameserver

![DNS query journey.png](:/15e38bf74d8b4b91871970048e776bb2)

### 13. Content Delivery Network (CDN)

- CDN refers to a geographically distributed group of servers which work together to provide fast delivery of Internet content.
- CDN consists of networked compute resources attached storage.
- CDN can be used for serving both static and dynamic contents.

## Food for thought Question:

1.  What is an internet?
2.  What happens when you type google.com your browser?

## VPC

- VPC can be thought of as your private network within the AWS.
- Recommended CIDR block is of /16 for VPC and /24 for Subnets.
- You can enable VPC flow logs to enable logging for all the traffic that comes in and out of VPC.
- You can also use Network Access Control List (NACL) and Route Table (RTb) at the VPC level.
- You can either use AWS configured default VPC or create your own custom VPC.
    **1. Default VPC:**
    - When you start using Amazon VPC, you have a default VPC in each AWS Region but can modify the components of your default VPC as needed.
    - Default VPC comes with a public subnet in each Availability Zone, an internet gateway, and settings to enable DNS resolution i.e. It wont have private subnet.

	**2. Custom VPC:**
	- The custom VPC created creates: VPC, a default route table (allows only in-VPC network connectivity) and a default NACL (allows all inbound and outbound traffic ). 
	- You have create other components of VPC as per your use case (eg: Subnets, RouteTables, NACL, Internet Gateway, NAT Gateway etc.).

### Subnets
- Subnets are the smaller logical breakdown network of VPC. 
- You can leverage subnets for availability (through multi-AZ) and maintain security by segregating systems that are interconnect with each other (through network segregation).
- For creating a subnet, you need to specify the IPv4 CIDR block for the subnet, which needs to be a subset of the VPC CIDR block.
- You cannot create a subnet that spans across multiple AZs.
- Usually a route table determines whether a subnet is private or public.

### Route Tables
- Route Table contains rules for which the packets go where.
- A route table can be attached to one or more route tables.
- A default route table is created when a VPC is created but it contains rule for internal network connection only.
- You can attach route table to a VPC or a Subnet.
- The best practise is to attach Internet Gateway (IGW) for public route tables (to be associated with public subnets) and NAT Gateway for private route tables (to be associated with private subnets).
- Destination and target need to specified to setup a route. You can add various resources as target such as: Instance, IGW, NAT, EIP, Peering Connection etc.

### Internet Gateway (IGW)
- IGW allows communication between your VPC and the internet.
- IGW enables you to connect to an EC2 instance in AWS using your local computer.
- IGW serves two purposes: 
	- to provide a target in your VPC route tables for internet-routable traffic, 
	- works as NAT for instances that have been assigned public IPv4 addresses.

### NAT Gateway
- NAT gateway is used so that instances in a private subnet can connect to services outside your VPC but external services cannot initiate a connection with those instances.
- NAT gateway is created in a specific Availability Zone. Its good practise to create NAT on each AZs that your resource is hosted on for Availability.
- You can associate NACL to control the traffic to and from the subnet for your NAT gateway.
- There are two types of NAT Gateways:
	- **Public:** 
		- Used to connect to internet and other VPCs or your on-premises network from the EC2 instances created in private subnet.
		- You must associate an elastic IP address with the NAT gateway at creation and cannot be disassociated without deletion of NAT.
	- **Private:** 
		- Used to connect to other VPCs or your on-premises network from the EC2 instances created in private subnet.
		- You cannot associate an elastic IP address with a private NAT gateway and cannot be disassociated without deletion of NAT.

### Elastic IP (EIP)
- An Elastic IP address can be associated with a single instance or network interface at a time.
- You can move an Elastic IP address from one instance to another.
- You can have one Elastic IP (EIP) address associated with a running instance at no charge.
- AWS prices you when these EIP addresses are not associated with any resource or is associated with a stopped resourse. this is minimize unnecessary reservation of EIPs.

### Network Access Control Lists (NACLs)
- NACL is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets or VPC.
- A default NACL is created when you create a VPC. You can modify the default NACL to your use case.
- Default NACL allows all connection by default and a custom NACL denies all connection by default.
- You can associate a NACL with multiple subnets but you can attach only one NACL per subnet.
- Network ACLs are stateless, which means that responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).
- You must specify Rule number (Priority of rule), Traffic Type (HTTP/HTTPS/SSH/Custom), Protocol (TCP,UDP,ICMP), Port Range(0-65535, Source (Source IP), Allow or Deny status to create a NACL rule.

### Security Groups (SG)
- A security group acts as a virtual firewall, controlling the traffic that interacts with the resources that it is associated with.
- A default security group is also created when you create a VPC. You cannot delete a default Security group. It is best practise to not use this security group.
- You can only create allow rules in Security Groups.
- You can attach multiple SGs to a single resource. They are merged virtually and act as one single Security Group.

### VPC Peering Connection
- It is a networking connection between two VPCs that enables you to route traffic between them privately. 
- You can create a VPC peering connection between your own VPCs, with a VPC in another AWS account, or with a VPC in a different AWS Region.
- There is no single point of failure for communication or a bandwidth bottleneck.

## Cloudfront
- Cloudfront is a CDN (Content Delivery Network) service from AWS.
- It is useful when you want the site (specailly the static contents like images, videos, static HTML pages etc.) to load faster for the end users.
- Cloudfront leverages what AWS calls as edge locations for serving the static contents.
- Cloudfront can also speed up dynamic content.

## API Gateway
- API Gateway is a fully managed service that enables developers to create, publish, maintain, monitor, and secure APIs at any scale.
- An API gateway acts as a reverse proxy to accept all application programming interface (API) calls.
- Support for stateful (WebSocket) and stateless (HTTP and REST) APIs.
- You can use IAM, Lambda Authorizer functions and congnito user pools as authentication mechanisms.
- supports custom domain names like `example.com`
- You can use canary deployments for safe rollout.

## Route53
- Route53 is a DNS service from AWS that is highly available (100% availability in SLA).
- It is fully compliant with IPv4 and IPv6.
- You can also purchase and manage Domain names such as `awstraining.com` from Route53.
- Different types of routing handled by Route53 are as follows:
	- Simple Routing
	- Weighted Round Robin
	- Latency Based Routing, 
	- Geolocation
	- Geoproximity
	- Failover Routing

### Hosted Zone
- Hosted zone is a container of records, which include information about how you want to route traffic for a domain and its subdomains.
- A hosted zone has the same name as the domain.

### Routing Policies:
**1. Simple routing policy:** 
- It is used to route internet traffic to a single resource. for example, a web server that serves content for the `krishnachalise.com.np` website.
- It is the most simple routing policy and is widely used.

**2. Failover routing policy:** 
- It is used when we want to configure active-passive failover.
- This type of routing is useful for mission critical businesses which requires very high availbility.

**3. Geolocation routing policy:** 
- It is used when you want to route internet traffic to your resources based on the location of your users.
- It is used when you want different stores to be opened for users based on location.

**4. Geoproximity routing policy:** 
- It is used when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another.
- It is useful when you want to serve traffic for a user based on user proximity.

**5. Latency routing policy:**
- It is used when you have resources in multiple locations and you want to route traffic to the resource that provides the best latency.
- It is useful for latency cricital applications such as streaming, Online Gaming.

**6. Multivalue answer routing policy:** 
- It is used when you want Route 53 to respond to DNS queries with up to eight healthy records selected at random.
- It is used when you have multiple web servers running the same application but dont have a common gateway eg: loadbalancer for them.

**7. Weighted routing policy:** 
- It is used to route traffic to multiple resources in proportions that you specify.
- It is useful when you want to do a canary deployment manually.

### DNS resolution through Route53
- The major difference is that Route53 acts as your authoratice DNS nameserver.
![Screen Shot 2022-05-18 at 08.51.31.png](:/fa9b94975e8c4d0bb3569a47c6580e2d)

## Lab Task VPC:
### Launch Resources in your own VPC
1. Create a Custom VPC with CIDR block 10.20.0.0/16 and name it `aws-training-vpc`
2. Which of these resources are created as part of the default VPC?
	1. VPC
	2. Public Subnets
	3. Private Subnets
	4. Internet Gateway
	5. NAT Gateway
	6. Security Groups
	7. Elastic IPs
	8. DHCP Option Set
	9. Any other
3. If subnets are not created, then create 6 subnets in each Availability Zones with following details:
	1. private-AZ1: 10.20.1.0/24
	2. private-AZ2: 10.20.2.0/24
	3. private-AZ3: 10.20.3.0/24
	4. public-AZ1: 10.20.10.0/24
	5. public-AZ2: 10.20.11.0/24
	6. public-AZ3: 10.20.12.0/24
4. Create 2 route Tables `private-rtb` and `public-rtb`
5. Create Internet Gateway (IGW) if it doesnot exists. Attach IGW to the created VPC.
6. Add routes in `public-rtb`to route `0.0.0.0/0` to IGW.
7. Create a NAT gateway (Name Tag: aws-training-NAT). 
8. Add routes in `private-rtb`to route `0.0.0.0/0` to NAT.
9. Associate `private-rtb` to private-AZ1/private-AZ2/private-AZ3 subnets.
10. Associate `public-rtb` to public-AZ1/public-AZ2/public-AZ3 subnets.
11. Launch a EC2 instance named - public instance with following details:
	1.  In `aws-training-vpc`
	2.  Instance type: `t2.micro`
	3.  Use ubuntu-22.04 AMI (Amazon Machine Image)
	4.  In `public-AZ1` subnet with Public IP assigned.
	5.  Allow port 22 and Port 80 during creation.
	6.  Security group name: `public-instance-sg`
	7.  Description: `SG for public instance`
	8.  Add userdata from this link: https://gist.github.com/chalisekrishna418/763dca1af1142903f16854ae3db2dcb5
	9.  Hit the public IP of the instance browser (eg: http://111.222.123.123)
12. Launch a EC2 instance named- private instance with following details:
	1. in Private subnet 
	2. Instance type: `t2.micro`
	3. Use `ubuntu-22.04` AMI (Amazon Machine Image)
	4. In `private-AZ1` subnet. Donot assign public ip.
	5. Allow port 22 and Port 80 during creation.
	6. Security group name: `private-instance-sg`
	7. Description: `SG for private instance`
	8. Add userdata from this link: https://gist.github.com/chalisekrishna418/763dca1af1142903f16854ae3db2dcb5
14. Try to reach SSH or Web for private instance. Are you able to reach the instance? Private instances are used 
15. Now, Again Create a New VPC `aws-training-vpc2` with CIDR block `10.30.0.0/16`. Create public subnets only and a internet gateway for this VPC. Also create Public Route Table and add a route to public route table. Donot create private VPC.
16. Launch a EC2 instance named - `public instance2` with following details:
	1.  In `aws-training-vpc2`
	2.  Instance type: `t2.micro`
	3.  Use ubuntu-22.04 AMI (Amazon Machine Image)
	4.  In `public-AZ1` subnet with Public IP assigned.
	5.  Allow port 22 and Port 80 during creation.
	6.  Security group name: `public-instance-sg2`
	7.  Description: `SG for public instance2`
	8.  Add userdata from this link: https://gist.github.com/chalisekrishna418/763dca1af1142903f16854ae3db2dcb5
17. Now SSH into the `public instance` that was created in step-11 and try these commands in the terminal:
```bash
telnet <public IP of public-instance2> 22
telnet <private IP of public-instance2> 22
```
18. What was the output of both commands?
19. Now for the command to work with private IP, Lets Create VPC peering among the two VPCs. Set `aws-training-vpc2` as requester and the other one as accepter VPC.
20. Create a route in `public-AZ1` of first VPC to route `10.30.0.0/16` to peering connection.
21. Create a route in `public-AZ1` of second VPC to route `10.20.0.0/16` to peering connection.

**Deletion list:**
1. Delete three EC2 Instances (private and public instances)
2. Delete 3 Security Groups
3. Delete Peering Connection.
4. Delete Internet Gateway (This will require you to delete route of internet gateway in route tables and detach from VPC)
5. Delete NAT Gateway(This will require you to delete route of NAT gateway in route tables and detach from VPC)
6. Delete Route Tables (public and private)
7. Delete Subnets
8. Delete VPC
9. Delete 2 Elastic IPs

### Build a sample API gateway
1. Create lambda function `aws-training-lambda` that gives JSON response. Like:
 `{"msg": "Hello from AWS Training"}`
Runtime: python-3.x
Code URL: https://gist.github.com/chalisekrishna418/5bdc78fba3e9f36e27c72212fee12edf
2. Deploy and Test the lambda to see if it is functioning properly.
3. Create a API Gateway named `aws-training-lambda-API` with lambda integration and `GET` resource that returns the result of resource on `/` path.
4. Try entering the URL of API gateway in browser and see the result.

**Deletion List**
- Lambda: `aws-training-lambda`
- API Gateway: `aws-training-lambda-API`

## Useful Resources

- [IPv4 Vs IPv6](https://www.geeksforgeeks.org/differences-between-ipv4-and-ipv6)
- [Subnetting Calculator](https://www.calculator.net/ip-subnet-calculator.html)
- [CloudFlareBlog - What is DNS? | How DNS works](https://www.cloudflare.com/learning/dns/what-is-dns/)
- [AWSDocs - Default VPC](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html)
- [AWSPricing - VPC](https://aws.amazon.com/vpc/pricing/)
- [AWSDocs - VPC Routing](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
- [AWSDocs - NAT Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html)
- [Comaprision of NACL and SG](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison)