# Travel-Blog-Tutorial
Blog


Hello, this is a tutorial on how to build a Travel blog using Iaas runs on top of apache-webserver and access it via domain name on the web. This is a step by step process starting by gaining access to an AWS account, running linux commands and building the server and finally getting acess to the website via its domain name.


## Log on/create an account Amazon EC2
In order to progress this tutorial on Amazon EC2 please click on this link https://signin.aws.amazon.com/signin? and select root user.
Once that is done it will ask you for the purposes of using AWS select the school you are in as minimal delays are experienced in this selection.

## Launch Ubuntu machine Amazon EC2
* Click on Launch new instance on EC2 dashboard
* Select an instance name in this case call it webserver2
* For the AMI choose Ubuntu and select the 24.04 server
* Instance type -  t2.micro
* Configure -  t2.micro with default settings
* Key pair -  create it and select a name
* Configure network settings - create a security group and enable SSH and HTTP ports
* Configure storage - leave with default settings

## Console into the Virtual Machine
Now that the instance is up and running your going to need to ssh into the virtual machine via a console, in this case i am using ubuntu but this will work on powershell as well. What your going to do is click on the instance running, select the 'connect' tab above it and press the ssh client section. From there you will see ssh code: 
