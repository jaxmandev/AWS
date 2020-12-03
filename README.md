# Introduction to AWS

## What is the Cloud?
* Cloud computing is the on-demand delivery of compute power, database, storage, applications, and other IT resources via the internet with pay-as-you go pricing.
* Infrastructure as a Service model.
## What is AWS?
* Amazon Web Services is one of the leading providers of cloud computing.
* Secure, cloud platform that offers a broad set of global cloud-based products.
* Amazon Web Services (AWS) includes over 175 different products and services
- including 60 that are free to try and deploy in a real-world setting. 
- The most popular services include 

1. Amazon Simple Storage Service (or S3) for object storage in the cloud and 
2. Amazon Elastic Compute Cloud (EC2) for virtual server access see below.

- all of the 175 features geared to help you run your cloud computing environment. 
It’s quite an extensive catalog, including tools to help you:
```
manage, deploy, and maintain compute, online storage, cloud databases, networking, analytics, robotics, machine learning, Internet of Things, security, VR and AR, media, and application development, and mobile apps and more.
```

## Deployment
Deployment is typically categorised into three main categories:
* On-Premise – This type of deployment occurs on premise and entails building, deploying and maintaining physical servers.
* Cloud / Public Cloud – The service provider hosts infrastructure and provisions to customers via the internet.
* Hybrid - This is a mixture of both Cloud and on-premise where some tasks may be completed using the cloud, and others, typically tasks which prioritise discretion, may opt for on-premise.

## Advantages of the cloud
1. Trade capital expense for variable expense-
  * Traditional model has a large up-front cost.
  * Capital expenditure in the form of heavily investing in data centres and servers, with guessed capacity needs.
  * With cloud, pay only for what you use.
  * Reduced maintenance allowing customer to focus upon business needs.
2. Massive Economies of Scale
  * Lower variable costs - use of hundreds and thousands of customers aggregated lading to higher economies of scale and savings passed onto customers.
  * Lower pay-as-you-go prices.
3. Stop Guessing capacity
  * Traditional model required guessing capacity leading to idle resources or limited capacity i.e under or over utilisation of resources.
  * Cloud - Use as much or little as you need, scale up or down within minutes.
4. Increased speed and agility
  * Minutes between wanting and needed resources
  * Lower costs and time for experimenting and developing.
5. Stop spending money in running and maintaining data centres.
  * Focus on products and customers rather than infrastructure.
6. Go global in minutes
  * Deploy apps in multiple AWS regions around the world within minutes.
  * Lower latency - better experience at a lower cost.


## What is EC2
* EC2, Elastic Compute Cloud is one of the services provided by AWS in the compute category.  
* Provides virtual machines in the cloud. These are known as EC2 instances.
* Gives full control over the guest OS on each instance.

## Security Groups
* Security groups act as virtual firewalls for EC2 instances.
* Used to control incoming and outgoing traffic by defining rules for inbound and outbound traffic.
* Rules can only be 'allow' rules i.e. cannot deny.
* An inbound rule would be used open a port to a specific ip address. The source would be specified as 'My IP'.
* Similarly, an inbound rule can also allow access to all ip addresses by having the source as 'Anywhere'. This is not advisable, especially for port 22
* Port 22 should not be open to to all as it poses a serious security risk. It can lead to multiple login attempts and if multi-factor authentication has not been enabled, the account is likely to be compromised.

# Connecting to an Instance
* To connect to an instance, we can use SSH keys.
* These can be created when spinning up an instance and must be stored in a secure location away from other code, typically the ~/.ssh directory.
1. Locate your key which should be in the SSH folder.
2. Ensure your key is not publically viewable, this can be done by running the command:
```bash
chmod 400 key.pem
```
3. Connect to the instance using the command
```bash
ssh -i "key.pem" ubuntu@ec2-publicIP.eu-west-1.compute.amazonaws.com
```
These instructions can also be accessed via clicking the 'Connect' button on the EC2 Instance page on the AWS Management Console.

## SCP
* Secure copy (scp) is a command to copy files and directories between locations.
* To send a single file to a remote server, use the following command:
```bash
scp -i ~/.ssh/keyname.pem filename ubuntu@ip:~/location
```
* To send a folder, we need the recursive flag, -r. Use the following command:
```bash
scp -i ~/.ssh/keyname.pem -r foldername ubuntu@ip:~/location
```

# Task - Run Sparta Sample Node App on EC2
1. Create an instance in AWS.
2. Connect to the instance
3. Use scp to copy the provisioning file into the virtual machine.
```bash
scp -i ~/.ssh/keyname.pem filename ubuntu@ip:~/location
```
4. Assign execute permissions to the provisioning file by running `chmod +x filename`
5. Use scp to copy the app and environment folders to the virtual machine.
```bash
scp -i ~/.ssh/keyname.pem -r foldername ubuntu@ip:~/location
```
6. Amend the provisioning file, if necessary, to reflect any changes in paths which may have resulted from copying the files.
7. Run the provisioning file.
8. Navigate to the public ip address of the instance. The following page should be displayed on
  * **port 3000**    
  ![port 3000](images/port_3000.png)    
  * **and port 80**     
  ![port 80](images/port_80.png)     

9. As an added test, run the following command to display the html webpage within the terminal.
```bash
curl privateip:3000
```    
![curl](images/curl.png)
