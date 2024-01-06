<center><h1>TASK 3</h1></center>

**User and Group Management**
**Task:** Create a set of user accounts and groups with specific permissions. Develop a scenario where different users need different access to certain directories. Document the user-group permissions and provide examples of commands used to achieve this

1. Create users:
```bash
sudo useradd dev1 dev2 marketingPerson1 marketingPerson2
```
2. Create groups developers and Marketing
```bash
sudo groupadd Developers Marketing
```
3. Assign users to their respective group:
```bash
sudo usermod -a -G Developers dev1
sudo usermod -a -G Developers dev2
sudo usermod -a -G Marketing marketingPerson1
sudo usermod -a -G Marketing marketingPerson2
```
4. Create some directories:
```bash
mkdir Marketing DevModules
```
5. Change ownerships:
```bash
sudo chown :Developers /DevModules
sudo chown :Marketing /Marketing
```
![[Pasted image 20240106023502.png]]

6. Change Permissions
```bash
chmod 770 /DevModules
chmod 775 /Marketing
```

![[Pasted image 20240106023826.png]]

DevModules only needs to be accessed by Developers, Marketing can be changed by Marketing group users but other users can read and execute the directory.

Checking Permissions:
```bash
su dev1
mkdir /Marketing/M
```

![[Pasted image 20240106024347.png]]
Developers group will be unable to write in the DevModules directory.

```bash
su marketingPerson1
ls DevModules
```
![[Pasted image 20240106024544.png]]Marketing group will be unable to read/write in DevModules.

