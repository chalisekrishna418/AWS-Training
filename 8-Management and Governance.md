# Management and Governance

## Cloudtrail
- It is an AWS service that enables us to maintain governance, compliance, and operational and risk auditing of your AWS account.
- It does this by recording actions taken by a user, role, or an AWS service (i.e all API Calls within AWS).
- While configuring a trail, you setup a S3 bucket where the trails related to API Calls to AWS will be recorded as logs.
- It is enabled by default when a AWS Account has been created.
- You can enable log file integrity validation in S3 to ensure that the logs has not be tampered.
- You can also enable AWS CloudTrail Insights to identify and respond to unusual activity.

## Systems Manager
- AWS Systems Manager is a collection of capabilities that simplifies application and resource management, shortens the time to detect and resolve operational problems, and also helps manage your AWS resources securely at scale.
- **What can you do with Systems Manager?**
	- **Run Command:** Run a single command to a batch of EC2 instances.
	- **Patch Manager:** Patch mutiple servers at once.
	- **Session Manager:** Use SSM Agent to securly connect to EC2 instances using IAM.
	- **Parameter Store:** Secrets and configuration data management.
	- **Inventory:** Collect metadata such as which EC2 instances are running the which software and configurations required by your software policy, and which instances need to be updated.

## AWS Health Dashboard
- It provides ongoing visibility into your resource performance and the availability of your AWS services and accounts.
- This can be thought of as a status page of AWS Services, features and AWS backbone systems.
- https://status.aws.amazon.com/

### Personal Health Dashboard
- Here you can view, how the status of AWS Services, features and AWS backbone systems has affected resources you have created within your AWS Account.
- https://phd.aws.amazon.com/phd/home

## AWS Config
- AWS Config is a service that enables you to continuously assess, audit, and evaluate the configurations of your AWS resources.
- With AWS Config you can:
	- Evaluate AWS resource configurations for desired settings.
	- Get a snapshot of the current configurations of the supported resources that are associated with your AWS account.
	- Receive a notification whenever a resource is created, modified, or deleted.
	- View relationships between resources. For example, you might want to find all resources that use a particular security group.

## Cloudwatch
- Amazon CloudWatch monitors your Amazon Web Services (AWS) resources and the applications you run on AWS in real time by collecting and tracking metrics, and logs.
- Aside from logging and monitoring, this service can also be used to run crons from within the AWS.
- You can also create alerts on your metrics using **Alerts**, query the logs from **Cloudwatch Insights**.

### Cloudwatch Logs
- This features enables us to collect logs from our application and other AWS Services such as lambda, VPC, EC2 etc.
- **Log Stream** is a sequence of log events that share the same source.
- **Log Groups** is a group of log streams that share the same retention, monitoring, and access control settings. 
- **Log insights** enables you to query on the logs using basic SQL query like syntax and you can also set a alert rule based on a particular log pattern.

### Cloudwatch Metrics
- Cloudwatch metrics provides us with the perfomance data of our AWS Services.
- You can query metrics data in Cloudwatch using Cloudwatch Metrics Insights.
- two categories of monitoring: 
	- **Basic monitoring:**
		- It is automatically enabled for services that offer basic monitoring.
		- In most services, Basic monitoring publishes metrics in 5-minute interval
		- Free of charge
		- 
	- **Detailed monitoring:** 
		- User has to enable detailed monitoring if they intend to use.
		- For most services, Basic monitoring publishes metrics in 1-minute interval
		- AWS incurs some charges for using this.

### Alarms
- You can Leverage Cloudwatch metrics to create Alarms out of those metrics so that you can setup an action based on the alert.
- You can setup actions such as to scale the resource, notify developers on the alarms and many other items.
- EC2 autoscaling also used Alarms to scale EC2 instance automatically.

### X-ray traces
- X-ray is a tracing solution provided by AWS.
- Its enables us to see the detailed view of how an application behaves and immensly helps in debugging.

### Events
- Also known as Event Bridge,
- Everything that happens within an AWS Account is an event. With cloudwatch events, you can perform actions or make trigger to another AWS services based on that event.

### Dashboard
- It is customizable home page in the CloudWatch console that you can use to monitor your resources in a single view, even those resources that are spread across different Regions. Y
- You can also use CloudWatch dashboards to create customized views of the metrics and alarms for your AWS resources.

## Labs

### Using Management and Governance services
1. Go to Cloudtrail Service Page and create a trail with following details
	a. Name: `training-cloudtrail`
	b. create a new S3 bucket named: `training-cloudtrail-bucket-09876`
	c. select all events (Management,Data Events,Insights Events)
	d. The trail should be multi region trail.
2. Now create a EC2 instance is public subnet:
	a. Name: `management-service-lab`
	b. Needs to be have publicly accessible HTTP and SSH Access.
	c. UserData Link: https://gist.github.com/chalisekrishna418/763dca1af1142903f16854ae3db2dcb5
3. SSH into EC2 instance and install cloudwatch agent and SSM agent in that machine.
**SSM Agent Installation:** https://docs.aws.amazon.com/systems-manager/latest/userguide/agent-install-ubuntu-64-snap.html
**Cloudwatch Agent Installation:** https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-commandline-fleet.html
4. Create a Cloudwatch Dashboard named `management-service-lab Instance metrics` for CPU Usage, Network In, Network Out of instance `management-service-lab`.
5. Add the metrics for memory usage and Disk Usage for `management-service-lab` Instance in the same Dashboard. This will require us to work with cloudwatch Agent.
Hint Link: https://gauravguptacloud.medium.com/aws-cloudwatch-agent-installation-for-memory-metric-integrate-with-grafana-365404154
6. Create a SNS Topic named `management-service-lab-alerts-topic` and add your email as the subscriber.
7. Now Create a Cloudwatch Alert for High CPU Usage for more than 60% CPU usage.
8. Now, see the log data that is generated from Cloudtrail, what did you see in the logs. Also query for some logs from AWS Cloutrail insights iteslf.
9. Also, Send the Apache2 access logs into cloudwatch Logs and view the logs in cloudwatch.
10. Query for all HTTP 404 requests from Cloudwatch insights.
11. Now create a AWS Config Rule to setup tag `Key: env`, value should be either `dev,staging, uat or production`. 

## Reading Materials
- [AWSDocs - CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/create-multiple-trails.html)
- [AWSDocs - Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)
- [AWSDocs - AWS Health Dashboard](https://docs.aws.amazon.com/health/latest/ug/what-is-aws-health.html)
- [AWSDocs - AWS Config](https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)
