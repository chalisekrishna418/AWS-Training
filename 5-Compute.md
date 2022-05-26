# Compute

## Elastic Compute Cloud (EC2)
- EC2 is the broad collection of services in AWS that enables us to provision, create, manage and use Virtual Machines or popularly known as servers.
- EC2 provides of various features like EC2 instance (VMs), EBS Volumes (Storage), AMIs (Images), Security Groups, Key Pairs, Loadbalancers which can be leveraged for building the infrastructure.
- It is elastic by nature i.e. it can be scaled up (and down in some cases) based upon the need/demand.

### EC2 Instances
- This is the Virtual Machine provided by AWS.
- EC2 instances are like your computer in the Cloud.
- It provides VMs of different capabilities that can best fulfill your needs.
- There are 3 cost mechanisms for EC2 instances
	- Spot Instances
	- On-Demand Instances
	- Reserved Instances: (No/Partial/Whole upfront)
- The spec (CPU, memory and Bandwidth etc.) of EC2 instances is defined by its intance type. 
- You can create a backup of EC2 instances as AMIs and manage the lifecycle of AMI and snapshots with EC2 snapshot lifecycle manager.

#### Instance Types:
- AWS provides different categories and generation of EC2 instance. This is identified by the instance type name.
- For Eg:
	- For `t2.micro`,  `t` is the instance class which means instance family that determines the different compute capabilities like brustable, memory optimized or CPU optimized. The letter `4` represents the generation of instance type which determines the architecture of CPU and `micro` defines the CPU and memory size.

### EBS Volumes:
- EBS volume is a durable, block-level storage device that you can attach to your instances.
- You can create a backup of EBS volumes as snapshots and manage the lifecycle of AMI and snapshots with EC2 snapshot lifecycle manager.
- You can attach multiple EBS volumes to a single instance but the volumes and Instances should be in the same availability zone.
- EBS volumes are like Hard Drives to the EC2 instances which is like your computer in the cloud.
- Amazon EBS provides the following volume types:
	- **General Purpose SSD (gp2 and gp3):**
		- Provides a balance of price and performance.
		- Can be used as boot volumes for EC2 Instances
		- Volume Size: 1 GiB - 16 TiB
		- Max IOPS: 1600
		- Max throughput: 1000 MiB/s
	- **Provisioned IOPS SSD (io1 and io2):**
		- Provides high performance for mission-critical, low-latency, or high-throughput workloads.
		- Can be used as boot volumes for EC2 Instances.
		- Volume Size: 4 GiB - 16 TiB (io1 Express can support upto 64TiB)
		- Max IOPS: 64,000 (io1 Express supports upto 256,000 )
		- Max throughput: 1000 MiB/s (io1 supports upton 4000 MiB/s)
	- **Throughput Optimized HDD (st1)**:
		- Used for Big data, Data warehouses and Log processing etc.
		- Cannot be used as boot volumes for EC2 Instances
		- Volume Size: 125 GiB - 16 TiB
		- Max IOPS: 500
		- Max throughput: 500 MiB/s
	- **Cold HDD (sc1):**
		- Scenarios where the lowest storage cost is important and throughput-oriented storage for data that is infrequently accessed.
		- Cannot be used as boot volumes for EC2 Instances
		- Volume Size: 125 GiB - 16 TiB
		- Max IOPS: 250
		- Max throughput: 250 MiB/s
	- **Magnetic (standard):**
		- Used for workloads where data is infrequently accessed
		- Can be used as boot volumes for EC2 Instances
		- Volume size: 1 GiB-1 TiB
		- Max IOPS per volume: 40–200
		- Max Throughput: 40–90 MiB/s

### Amazon Machine Image (AMI)
- AMIs are the image files that are installed into the EC2 machines for OS to run.
- AMI are like the OS image files that are installed into EC2 instances which are like your computers in the cloud.
- An AMI can be used to setup EC2 instances.
- You can make use of cutom baked AMIs to reduce the overhead of installing similar applications over different EC2 instances.
- An AMI is region specific i.e. AMI created in one region cannot be used in other region unless you allow cross region replication of AMIs.
- There are 3 different Types of AMIs:
	- **Public:** These AMI can be used by any AWS Account so that anyone can use this AMI to launch the EC2 instances in their account.
	- **Private:** These AMIs can be used by the AWS account which owns/created the AMI and be used by AWS Accounts with whom it is shared to launch the EC2 instances in the respective AWS Accounts.
	- **Shared:** These are the AMIs shared by other AWS Accounts so that you can used to launch the EC2 instances in your account.

### Placement Groups
- Placement groups can be used to influence the placement of a group of EC2 instances within an Availability Zone.
- There is no cost for creating placement groups but you need to pay resource you create as part of your placement groups.
- There are three Types of Placement Groups:
	- **Cluster:** 
		- provisions EC2 instances into a low-latency group within a single AZ.
		- Not good for High Availability
		- beneficial for latency sensitive, high network throughput requiring applications.
	- **Partition:** 
		- Provisions instances across logical partitions to ensure that instances in one partition do not share underlying hardware with instances in other partitions
		- can have partitions in multiple Availability Zones in the same region
		- No two partitions within a placement group share the same racks, allowing isolating the impact of a hardware failure within the application.
	- **Spread:** 
		- Provisions a small group of instances across distinct underlying hardware to reduce correlated failures.
		- Reduces the risk of simultaneous failures that might occur when instances share the same underlying hardware.
		- Recommended for applications that have a small number of critical instances that should be kept separate from each other.

### Key Pairs
- Key Pairs are the access mechanism for SSH-ing into the machines.
- You can either create a new SSH Key or import your existing one in the AWS through AWS Management Console.

### Network Interfaces
- It is a logical networking component in a VPC.
- It is like a virtual network card to your EC2 instance which is like your computer in the cloud.
- A Network Interface consists of: MAC Address, IPv4,IPv6 Addresses etc.
- You can create and configure network interfaces and attach them to instances in the same Availability Zone.

### Launch Configuration
- It is a templating that defines how an EC2 instance is to be lauched within an Autoscaling Group.
- Information like which AMI, instance type, Key Pair, Security Groups, EBS volume mappings etc are specified in the template which is a part of launch configuration.
- You cannot edit the launch configuration but you can create a new version of launch configuration with updated values from existing Launch Template.

### EC2 Autoscaling
> Not to be confused with AWS Autoscaling.
- AWS Auto Scaling lets you build scaling plans that automate how groups of different resources respond to changes in demand. 
- You can specific minimum, maximum and desired number of EC2 instances in an EC2 Autoscling group.
- It is the scale out (horizontal) scaling method for EC2 instances.
- It makes use of Launch Configuration to create new EC2 instances and uses scaling option as rules which determines when to add and terminate servers to existing group of servers.
- You can use different scaling options based on your need. The famous ones are CPU based scaling (Scale based on demand) and Scheduled scaling (Scale based on a schedule).

### Target Groups
- Target groups are logical grouping of EC2 instances so it can be used to route requests to one or more registered targets
- You can define health checks on target groups which is leverage by Loadbalancer to route requests to the registered targets that are healthy.
- You can use target group only with Application Loadbalancers.
- There is no cost for creating Target groups.
- You can use different target groups to setup the behaviour how loadbalancer interacts with target group.
- There are 3 main type of target for target group:
	- **Instance:**
		- The targets are specified by instance ID.
	- **Lambda:**
		- The target is a Lambda function.
	- **IP:**
		- The targets are IP addresses.
		- You can't specify publicly routable IP addresses.

### Load Balancers
- It is a device that acts as a reverse proxy and distributes network or application traffic across a number of EC2 instances.
- Types of Load Balancers:
	- **Application Load Balancer:**
		- Works on Layer-7
		- - It makes use of flexible IPs to route HTTP and HTTPS traffic
		- ALB will route traffic only to a healthy targets within the target group.
		- It makes use of Target Group to route traffic to specific machines which can be reached either using resource ID or IP.
		- You can route traffic to specific targets based on traffic, IP, Headers etc.
		- With ALB, it is a requirement that you enable at least two or more Availability Zones.
		- ALB only routes traffic to healthy instances by checking the health of targets using Target Group Health Checks.
	- **Network Load Balancer:**
		- Works on Layer-4
		- It makes use of static IPs to route TCP, UDP and TLS traffic
		- It is used for applications that are latency critical.
		- It simply forwards requests to specific Instances, IPs or Lambdas.
	- **Classic Load Balancer**
		- Works on both Layer-4 and Layer-7 and is the only load balancer that works in EC2-Classic.
		- It supports application-defined sticky session cookies
		- It can’t forward traffic on more than one port per instance, and it doesn’t support forwarding to IP addresses.
		- It can forward traffic to EC2 Instances and containers hosted in ECS and EKS but not to containers hosted with Farget Type in ECS.
		- It is recommend not to use classic loadbalancer

## Lambda
- Lambda is a serverless compute service that lets you run code without provisioning or managing servers.
- Your codes are organized as Lambda Functions.
- Lambda runs your function only when needed and scales automatically, from a few requests per day to thousands per second
- You pay only for the compute time that you consume—there is no charge when your code is not running.
- You can write your Lambda functions in Java, Go, PowerShell, Node.js, C#, Python, and Ruby code, but also provides a Runtime API which allows you to use any additional programming languages.
- It can be used for processing large data, creating simple cron tasks, or create event driven applications.
- You cannot login into servers that run your lambda function but you can always view logs of your lambda function in AWS Cloudwatch.
- You can set your lambda function memory from 128MB to 10,240MB.
- AWS Lambda functions can be configured to run up to 15 minutes per execution. You can set the timeout to any value between 1 second and 15 minutes.

## ECR
- It is an AWS managed container image registry.
- What Github is for source codes, ECR is for docker image or dockerhub for AWS.
- You can create both public and private repositories in ECR.
- You can define lifecycle policy rules that is used to clean up of unused images.
- You can configure scan on push to each repositories so that images are scanned for software vulnerabilities.
- You can enable Cross-Region and cross-account replication access images easier whereever you need them.

## ECS
- It is a highly scalable, fast, container management service that makes it easy to run, stop, and manage Docker containers on a cluster.
- **Cluster** is a logical grouping of tasks or services. Clusters can be used to isolate your applications so they dont use the sameunderlying hardware. For Fargate Launch Type, cluster resources are also managed by Fargate.
- **Task definitions** is a JSON document that describes one or more containers that form your application. A maximum of 10 containers can be described within a Task Definition. It is a blueprint for the application that specifies the various parameters (eg: CPU, memory, ports, environment variables, data volumes etc) for your application.
- **Task** is the instantiation of a task definition within a cluster. You can run a standalone task, or you can run a task as part of a service.
- **Services** defines the desired number of tasks that is run and managed simultaneously in an Amazon ECS cluster. It is a scheduling mechanism for task definition that ensures the desired count of tasks per task definition is maintained.
- There are **two launch types** of ECS:
	**1. EC2 Launch Type:**
		- This is a serverless pay-as-you-go option. You can run containers without needing to manage your infrastructure.
		- Used for workloads that need to be optimized for low overhead or occasional bursts
	**2. Fargate Launch Type**
		- Configure and deploy EC2 instances in your cluster to run your containers.
		- Used for workloads that require consistently high CPU Core and memory or needs to be optimized for cost or needs to access persistent storage.

## EKS
- It is a fully-managed, certified Kubernetes service that simplifies the process of building, securing, operating, and maintaining Kubernetes clusters on AWS.
- Amazon EKS integrates with core AWS services such as CloudWatch, Auto Scaling Groups, and IAM to provide a seamless experience for monitoring, scaling and load balancing your containerized applications.

## LightSail
- LightSail is a simplified version of EC2 that is cost-effective, fast, & reliable with an easy-to-use interface.
- It’s ideal for simpler workloads, quick deployments, and getting started on AWS.
- LightSail can be used for Simple web applications, Websites that uses WordPress, and eCommerce, etc or Single-server business software or for Dev/Test environments

## Labs:
### Run a single app in multiple EC2 Instances:
1. Create one EC2 instance in private subnet with name `web-server1`.
**Userdata:** https://gist.github.com/chalisekrishna418/763dca1af1142903f16854ae3db2dcb5
2. Create a EC2 instance in public Subnet with name `bastion`. Enable Public IP.
**Userdata:** https://gist.github.com/chalisekrishna418/763dca1af1142903f16854ae3db2dcb5
3. Setup `bastion` instance as SSH bastion to access SSH of `web-server1`
4. Now Create a Loadbalancer (Application Loadbalancer) with following settings.
	a. In Public Subnet.
	b. Attach security group (only port 80 is allowed).
	c. Forward port 80 connections to the target group `web-server-tg`. Create the target group if required and add `web-server1` as target
5. Create AMI of `web-server1` without restart. Name the AMI as `web-server-1-20220527`.
6. Launch another private instance from existing AMI without any userdata. Name the instance as `web-server2`. Use same security group as that of `web-server-1`.
7. Add the `web-server-2` instance in same Target group as that of `web-server-1`. Check using Loadbalacer DNS Name if the site is working as usual.
8. Add health check in target group expecting HTTP Status code 200 for / on HTTP port.
9. SSH into `web-server-2` and change the content to `Hi, I am from web-server-2` instead of existing one.
10. Try hitting the URL and what behaviour can you experience.
11. Lets mock a behaviour of failure of single instance by stopping apache in `web-server-1` using the following command:
```
systemctl stop apache2.service
```
12. What happened to the application. Did the application go down or was there something else?

**Deletion List:**
- Application loadbalancer
- Target Group `web-server-tg`. Deregister Targets if required
- Delete Instances `web-server-1`, `bastion`, `web-server-2`
- Deregister created AMI: `web-server-1-20220527`
- Delete Security groups: `web-server-sg`, `bastion-sg`, `loadbalancer-sg`
- Delete NAT Gateway. Delete Routes if required !
- Delete `private-route-table`

## Reading List
- [AWSDocs: EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)
- [AWSDocs - Placement Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)
- [AWSDocs - Target Groups](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)
- [AWSDocs - Load Balancer Types](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/load-balancer-types.html)
- [AWS - Lambda FAQs](https://aws.amazon.com/lambda/faqs/)
- [AWSDocs - What is ECR?](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html)
- [AWDocs - Amazon Elastic Kubernetes Service](https://docs.aws.amazon.com/whitepapers/latest/overview-deployment-options/amazon-elastic-kubernetes-service.html)
