<center><h1>TASK 5</h1></center>

**Secure File Transfer**
**Task:** Configure SSH for secure remote access to a server. Using SCP, transfer a file from your local machine to the remote server. Document the steps involved, including setting up SSH keys for authentication and using SCP for the transfer.

**For Connecting to remote server:** 
1. Install openssh-client:
```bash
sudo apt install openssh-client
```
2. Generate the ssh key:
```bash
sudo ssh-keygen
```
3. Connect to the remote server:
```bash
sudo ssh -p 1875 jainil@127.0.0.1
```

![[Pasted image 20240106130600.png]]

**To transfer the file using `scp`:**
```bash
scp lorem.txt -p 1875 jainil@127.0.0.1:/home/jainil/Desktop/Jainil_Folder
```

![[Pasted image 20240106131048.png]]