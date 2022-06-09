# AWS_On-premise_Source_Connection

Provisioned Infrastructure using AWS CloudFormation - a service that allows one to manage infrastructure as code.

# YAML Template - The On-Premise File Server

After you've spent some time learning about YAML and CloudFormation, your boss decides it's time to give you a nudge in the right direction and shares the following YAML file with you: [Linux-instance-template](code/part1/student_linux_template.yml). 

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
