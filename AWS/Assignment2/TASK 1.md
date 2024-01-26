<center><h1> TASK 1: Launch an EC2 Instance:</h1></center>

**Subtask 1: Launch a new EC2 instance using the Amazon Linux 2 AMI using AWS console.**

Following are the steps to Launch EC2 Instance:

1. Search for ec2 in search tab inside aws console.
	![[Pasted image 20240125185723.png]]

2. In EC2 click on “Launch Instance”.
	![[Pasted image 20240125185750.png]]

3. After that enter the name of the web server. Then search for Amazon Linux 2 and select Amazon Linux 2 AMI inside the Application and OS images tab. Select instance type t2.micro. We need to generate key pair in order to access this Virtual machine using SSH. Enter the name of the key and select RSA and .pem file format for the key. Select “Allow SSH traffic “ and select “Anywhere” and also allow HTTP traffic. In configure storage select 8gb of gp3 volume which is eligible for free tier. Then click on Launch Instance.
	![[Pasted image 20240125185759.png]]
	­­­![[Pasted image 20240125185804.png]]
	![[Pasted image 20240125185812.png]]
4. Now you will be able to see “myLinux2Server” running inside the running instances.
	![[Pasted image 20240125185823.png]]

5. Now click on “myLinux2Server” to view details about that instance. Inside that click on security tab and scroll down to inbound rules, where we can see that port 22 and 80 are open.
	![[Pasted image 20240125185831.png]]

**SUBTASK 3:** Connect to the newly launched EC2 instance using SSH

**Steps to connect to EC2 instance:**

1. Open powershell and navigate to the folder where the “MyAmazonLinux2KeyPair.pem” is located.
	![[Pasted image 20240125185853.png]]

2. Then enter the following command to connect to ec2 instance using ssh:
	

```bash
ssh -i .\MyAmazonLinxu2KeyPair [ec2-user@13.126.222.222](mailto:ec2-user@13.126.222.222%20)
```
	
![[Pasted image 20240125185900.png]]