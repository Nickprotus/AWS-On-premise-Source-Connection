# AWS_On-premise_Source_Connection

Provisioned Infrastructure using AWS CloudFormation - a service that allows one to manage infrastructure as code.

### YAML Template - The On-Premise File Server

The EXPLORE Data Science Academy shared the following YAML file: [Linux-instance-template](code/part1/student_linux_template.yml). 

The template is part of the configuration files use to recreate the on-premise source connection scenario, and is responsible for setting up the following infrastructure via AWS CloudFormation: 

**Resources Created**
 - *Linux Instance*: A `t2.micro` EC2 instance, used to simulate the file server used within the on-premise source connection scenario.   
 - *IAM Role*: An IAM role allowing an associated instance to access other AWS services. 
 - *S3 Access Policy*: An IAM policy giving read-only access to any bucket within the S3 service. 
 - *Instance Profile*: An IAM profile, connecting the instance and IAM role together. 

**Template Inputs**
 - *VPC*: A VPC Id that defines which VPC the Linux instance will be deployed into.
 - *Subnet*: A Subnet Id defining which subnet to associate with the deployed Linux instance.  
 - *Security Group*: A list of security group Id's which can be associated with the deployed instance.
 - *KeyName*: The name of a previously created AWS key pair which is associated with the Linux instance. 
 - *Linux AMI*: The Amazon Machine Image (AMI) which is used to configure the EC2 instance. This input specifies the latest version of Amazon's Linux as the AMI to use. 


### Additional Templates

*"VPC"* base template which sets up the requisite network infrastructure into which the above resources can be deployed. 
*"Windows-instance"* template which sets up the on-premise machine which can be used to access the file server. 


### Launching Infrastructure via CloudFormation

VPC Stack Launch
Windows Instance Stack Launch
Linux Instance Stack Launch


### Setting Up a File Gateway 

Established Connectivity with the On-Premise Windows Instance
Created an S3 File Gateway Resource Bucket
Configured and Deployed an AWS File Gateway


### Configuring and Mounting the NFS File Share 

Set up a corresponding NFS-based file share that will be responsible for receiving data during the on-premise to cloud migration. The file share is mounted to the organisation's file server (Linux instance) in order to facilitate seamless data transfer to the cloud. 

NFS Creation
File Server Connection and NFS Mounting


### Configuring Alarm Triggers

Having mounted the NFS file share onto the Linux instance file server, I configured a metric-based CloudWatch alarm which will trigger when a data transfer over a specified threshold is exceeded. 
