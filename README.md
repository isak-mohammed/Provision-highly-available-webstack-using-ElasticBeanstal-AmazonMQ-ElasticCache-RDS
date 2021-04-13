# Provision highly available web stack using Amazon Elastic Beanstalk, Amazon MQ, Elastic Cache and Amazon RDS with just few clicks
## Prerequisites
1. An AWS account
2. JDK8 installed on your local machine
3. Maven installed on your local machine
4. Custom VPC with public & private subnets in each AZ of your nearest region in aws (Route tables, Nat gateway and Internet gateway should be configured in your custom VPC)

Please Note: I have 3x private(10.0.1.0/24, 10.0.2.0/24, 10.0.3.0/24), 3x public subnets (10.0.4.0/24, 10.0.5.0/24, 10.0.6.0/24) in eu-west-2 region in custom VPC(10.0.0.0/16) and will be using through out this setup.

Note: we will be using default VPC for this setup and planning to add more stuff in coming weeks with separate VPCs. We can use centos7 ami for all the 4x instances or can use ubuntu 18 ami for just tomcat instance as it will be easy to control the start and stop of tomcat service with systemctl command without much setup.
## Steps Involved in the setup:
1. Clone the repo and cd into project-1
2. Create Key pairs and security group for backend services.
3. Provision Multi-AZ MySQL using RDS service in private subnet group of our custom VPC.
4. Provision 2xnode Memcached cluster using Elastic Cache in private subnet group of our custom VPC.
5. Provision Active/Standby ActiveMQ message broker using Amazon MQ service in 2xprivate subnets our custom VPC.
6. Upload build application artifcat in Elastic Beanstalk, which in turns deploys our complete web application by provisioning tomcat ec2 instances in Auto Scaling Group(ASG), ALB, etc. and then update backend security group to allow frontend to interact with it.
7. Then Copy our Elastic Beanstalk environment end point and add it as CNAME in the domain provider dns setting to divert the traffic to ALB, So, that users can use meaningful URL to reach our application. And update the same URL in Cloud Front to be distributed using CDN.

## Link to setup:

https://isakmohammed.hashnode.dev/provision-highly-available-web-stack-using-amazon-elastic-beanstalk-amazon-mq-elastic-cache-and-amazon-rds-with-just-few-clicks
