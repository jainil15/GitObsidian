<center><h1>TASK 2</h1></center>

**a. Task:** Create a backup of a directory - Use the `cp` command to create a backup copy of an entire directory, preserving its structure.

Structure of the directory Assignment2:

![[Pasted image 20240105182555.png]]

To copy the directory and its structure the following command is used:

```bash
cp -r Assignment2 Assignment2_backup
```

![[Pasted image 20240105182936.png]]
<br>
**b. Task:** Delete files that match a specific pattern - Use the `rm` command with wildcards to delete files that match a certain pattern (e.g., all `.tmp` files in a directory).

e.g., Remove all the txt file from Direc1

Before:
![[Pasted image 20240106163014.png]]

Command to remove all .tmp files from Direc1:
```bash
rm -r Direc1/*.tmp
```

After:
![[Pasted image 20240106163025.png]]

