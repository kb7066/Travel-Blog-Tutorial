



# Wondering Wayfarer Travel-Blog-Tutorial
Student ID: 35325158

Name: Khalid Abdi

Domain name: https://khalid-ab.com/



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
# Test webserver
Now that we have gained the right permissions and have access to the html, lets try testing the conenctivity go the amazon EC2 instance and copy the public ip-address. Before pasting it in place it with a http before the ip-address and paste into the webrowser. Once that is done you webserver should pop up on the browser.


# Editing Webpage
Once the webpage is up we know that the ip-address for the server is functioning and correct, it is now time to edit our travel-blog webpage. So first i would like to use the sudo command above in the previous step and sudo into our index.html file. Once your in go to index.html file were it says <title> place in the title of your webpage in this case lets call it "Wondering Wayfarer's" and shoud look like this down below

![image](https://github.com/user-attachments/assets/71cb256b-de8b-4f37-896b-e64408c74854)

Once thats done you want to also add a heading for what your travel blog is about and based on by changing the <h1> header to "Mongolia". Then after thats done you need to also change the colour and add a description about your blog. This can be done by altering the <body style= to "background-colour: lightblue">. And for the description go to were it says <div class= put in "description"> and write the information in the code block. It should look like this down below.

![image](https://github.com/user-attachments/assets/2cbda9bb-fe06-4493-bf36-9687cd834cf6)














# Linking the Domain name 

We now can access our webpage via the ip-address of the vm, but we now would like to link our virtual machine in the cloud with DNS so follow these steps below.

* Go AWS ec2 dashboard and look for route 53 which is used to register domain names
* Then go to were it says register domains and select a name that is easy and simple characters from A-Z 0-9.
* Once a name is selected proceed to checkout
* Finally enter your details in the billing page, once that is complete wait until domain name is registered
* After domain name is registered go to the hosted zones tab in route 53 and click create A records make sure the TTL 300 and the domain name is pointing to your ip-address.

# SSH into the Virtual machine via the domain name

Once you have recieved your domain name go to the CLI on ubuntu and type in this command to ssh into your machine.
```
ssh -i pemkey.pem ubuntu@[yourdomain-name-goes-here.com]
```
If you successfully ssh'ed into your machine via the domain try typing https://your-domain-name.com on the URL page and see if it loads your website


# Obtaining a digital certificate via certbot
Since we got our webpage accessbile via our domain we are going to need a digital certificate for HTTPS. To do that go this page. 

```
https://certbot.eff.org/
```
And select my website is running as 'Apache' on 'Linux snap', once that is done go to your ubuntu command line and just follow the steps to the end. Now try by going to your webiste via its domain name and you should see in the URL tab a lock saying 'You are securely connected to this site Verified by: Lets encrypt'. After you have done that you should have your machien accessible via domain name and webpage running.


![image](https://github.com/user-attachments/assets/fd380adc-1495-48c5-864d-6b12cfc7fcc0)




