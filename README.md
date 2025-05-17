
# Wondering Wayfarer Travel-Blog-Tutorial



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
Now that the instance is up and running your going to need to ssh into the virtual machine via a console, in this case i am using ubuntu but this will work on powershell as well. What your going to do is click on the instance running, select the 'connect' tab above it and press the ssh client section. 

* Downlaod the pem key and place into a folder on your device

* Then open a linux command line or a Powrshell command line on your device, and cd into where the key was placed, and enter this:
```
 ssh -i "yourkeyname.pem" ubuntu@ec2-12-123-1-35.ap-southwest-5.compute.amazonaws.com
```
After running this you will get a permission denied telling the user that they cant ssh into the machine so run the following command to give the user right permissions

```
chmod 400 "yourkey.pem"
```

# Install Apache #

Once you have ssh'ed into your mahcine on the command line you will need to refresh/update the package making sure its up to date you can do this by doing a:

```
sudo apt update
```
To install the apache webserver
```
sudo apt install apache2
```

# Index.html permissions
Once the apache webserver is installed we will now need to gain access into our index.html we can do this by running:
```
sudo nano /var/www/html/index.html
```
you will most likely not be able to edit this html as you do not have the right permissions so you will to give it the right ones. So inside the virutal machine cd and write. 

```
cd /var/www/html
```
Then check if the index.html file is in there by doing an ls.
```
ls
```
Then finally try to sudo into the index.html and try to access it now by doing this command
```
sudo nano /var/www/html/index.html
```
#Test webserver
Now that we have gained the right permissions and have access to the html, lets try testing the conenctivity go the amazon EC2 instance and copy the public ip-address. Before pasting it in place it with a http before the ip-address and paste into the webrowser. Once that is done you webserver should pop up on the browser.


#Editing Webpage






# Linking the Domain name 



