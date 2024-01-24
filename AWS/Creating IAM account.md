1. To Create IAM account go to the aws console and search for iam and select IAM.
	![[Pasted image 20240124214459.png]]
2. Then select "Users" from the menu.
	![[Pasted image 20240124214654.png]]
3. Then click on create user.
	![[Pasted image 20240124214722.png]]
4. Then enter the user name and select "Provide user access to the AWS Management Console" and then select I want to create an IAM user. Then select custom password and enter password that follows the password policy. Then uncheck "Users must create a new password at next sign-in". Then click on next
	![[Pasted image 20240124215337.png]]
5. Now Click select "Attach policies directly" in permission options. Now search for policy "AmazonS3FullAccess" then select it. Then click on next.
	![[Pasted image 20240124215951.png]]
6. Then you will see Review and Create page. Now click on "Create User"
	![[Pasted image 20240124220129.png]]
7.  Now you can either download the user credential's .csv file. Then click on "Return to users list"
	![[Pasted image 20240124220329.png]]
8. Now you will be able to see all the IAM users
	![[Pasted image 20240124220416.png]]

### To create IAM user's access key
1. Select "S3-User" from IAM users list.
	![[Pasted image 20240124220802.png]]
2. Navigate to security credentials in "S3-User" info. And scroll down to Access keys and then click on "create access key"
	![[Pasted image 20240124220823.png]]
3. Select "Command Line Interface (CLI)" from the use case. Then click on "next".
	 ![[Pasted image 20240124220917.png]]
4. Then you can add an optional description tag. Then click on "Create access key"
	![[Pasted image 20240124221251.png]]
	
5. Now you will be able to see the access key and secret access key.
	![[Pasted image 20240124221941.png]]