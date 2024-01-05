**File Permission**
Task: Create a file/folder and give it the fine-grained access to it. Research which user need how much permissions. Document the all the process and your research.

To check permission of file/folder use:
```bash
ls -l ./ ./folder
```

![[Pasted image 20240105234105.png]]

- To change permissions of the folder such that owner can read, write and execute while group can only read and execute and others can't access the file use command:

```bash
chmod 750 folder
```

7 (Owner): Read(4) + Write(2) + Execute(1)
5 (Group): Read(4) + Execute(1)
0 (Others)

![[Pasted image 20240105235523.png]]

To change the permission of the 'file.txt' such that owner can only read and write the file while group members can only read the file and other do can't read, write or execute, use command:

```bash
chmod 640 folder
```

6 (Owner): Read(4) + Write(2)
4 (Group): Read(4)
0 (Others)

![[Pasted image 20240105235736.png]]