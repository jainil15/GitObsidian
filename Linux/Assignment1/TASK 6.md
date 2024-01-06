<center><h1>TASK 6</h1></center>

**Task**: Develop a practical guide detailing the use of the "du -h" command to check disk space utilization. Provide examples for various directories and files, and explain the significance of the command's options and output.

**`du -h`** command is used to estimate the space used by a directory or file. `-h` means human readable.

![[Pasted image 20240105165340.png]]
- First column shows the disk space
- Second column shows the path of the directory.

 **`du -h /path`** is used to disk space utilization of a particular directory.

e.g. `du -h /Desktop`
![[Pasted image 20240105165846.png]]
#### **Options:** 
- The `-h` flag makes the output human-readable.
- Use `-s` for a summarized total and `-c` for a grand total