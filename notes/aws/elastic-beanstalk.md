# Elastic Beanstalk

Quickly deploy and manage web-apps on AWS without worrying about the underlying infrastructure (Platform as a Service Paas)

## Platform as a Service
A platform allowing customers to develop, run, and manage applications without the complexity of building and maintaining the infrastructure typically associated with developing and launching an app

Can think of Elastic Beanstalk (EB) as the Heroku of AWS

Not recommended for "Production" applications (talking about enterprise, large companies)

EB is powered by a CloudFormation template
Sets up:
* Elastic Load Balancer
* Autoscaling Groups
* RDS Database
* EC2 Instance
* Monitoring
* In-Place and Blue/Green deployment methodologies
* Security
* Can run Dockerised environments

## Supported Languages
* Go
* NodeJS
* Java
* Python
* Ruby
* PHP
* ASP.NET
* Docker

Web vs Worker Environment

Web Environment
Comes in two variants
	Load Balances Env, uses ASG and set to scale, uses an ELB (designed to scale)
	Single-Instance Env, uses asg but desired capacity set to 1, no ELB to save costs, public IP address has to be used to route traffic to server
Creates an ASG
Creates an ELB (Optional)

Worker Environment
Creates an ASG
Creates an SQS Queue
Installs the Sqsd daemon on the EC2 instances
Creates CloudWatch Alarm to dynamically scale instances based on health

Deployment Policies
These are the deployment policies available with Elastic Beanstalk
All at once
Rolling
Rolling with additional batch
Immutable

Can't have rolling deployment policies on single-instance env
Rolling requires a LB because it attaches and detaches instances in batches from the ELB.

All at Once
1. Deploys the new app version to all instances at the same time
2 Takes all instances out of service while the deployment processes
3. Servers become available again

The fastest but also the most dangerous deployment method
If it fails you need to roll back the change by re-deploying the original version to all instances.

Rolling
1. Deploys the new app version to a batch of instances at a time.
2. Takes batch's instances out of service while the deployment processes.
3. Reattaches updated instances
4. Goes onto next batch, taking them out of serviec
5. Reattaches those instances (rinse and repeat)

In case of failure, need to perform an additional rolling update to roll back the changes.

### Rolling with additional batch

1. Launch new instance that will be used to replace a batch
2. Deploy update app version to new batch
3. Attach the new batch and terminate the existing batch

Rolling with additonal batch's ensure our capacity is never reduced. This is important for applications where a reduction in capacity could cause availability issues for users.

In case of failure, you need to perform an additional rolling update to roll back the changes.


