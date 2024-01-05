 **1: Basic Functions** 
Objective: Write a shell script that uses a function to print a greeting.

```bash
greet() {
	echo "Good Morning!"
}
greet
```

![[Pasted image 20240105212435.png]]

**2: Debugging Scripts** 
Objective: Write a buggy shell script and use debugging to identify and fix the issue.

```shell
#!/bin/bash

add() {
	local a=$1
	echo $(expr 1 + $a)
}
echo $(add 'a')
```

```bash
bash -x ./task2.sh
```

![[Pasted image 20240105214306.png]]
fixed script:
```bash
#!/bin/bash

add() {
	local a=$1
	echo $(expr 1 + $a)
}
echo $(add 15)
```

**3: Using Functions for Repetitive Tasks** 
Objective: Write a shell script that uses a function to create multiple directories.

```bash
#!/bin/bash

createDir() {
	for i in "$@"
	do
		mkdir -p "$i"
		echo "directory $i created"	
	done
}
read dirs
createDir $dirs 
``` 

![[Pasted image 20240105215427.png]]
![[Pasted image 20240105215556.png]]

**4: Script with All Learned Concepts** 
Objective: Write a shell script that uses variables, conditionals, loops, and functions to interact with the file system.

Script:
```bash
#!/bin/bash  
  
createDirs() {  
	for i in "$@"  
	do  
		mkdir -p "$i"  
		echo "directory $i created"  
	done  
}  
createFiles() {  
	for i in "$@"  
	do  
		touch "$i"  
		echo "file $i created"  
	done  
}  
removeDirs() {  
	for i in "$@"  
	do  
		rm -r "$i"  
		echo "$i removed"  
	done  
}  
readFile() {  
	cat $1  
}  
  
while true  
do  
	echo "Select one of the following:"  
	echo "1. Create files"  
	echo "2. Create Dirs"  
	echo "3. Read file"  
	echo "4. Remove files/dirs"  
	echo "5. Quit"  
	  
	read -p "Enter your choice: " choice  
	case $choice in  
	1)  
		read -p "Enter file names to create: " fileNames  
		createFiles $fileNames  
		;;  
	2)  
		read -p "Enter dir names to create: " dirNames  
		createDirs $dirNames  
		;;  
	3)  
		read -p "Enter a file name to read: " fileNameToRead  
		readFile $fileNameToRead  
		;;  
	4)  
		read -p "Enter a files/dirs to remove: " fileDirNames  
		removeFiles fileDirNames  
		;;  
	5)  
		echo "Quitting..."  
		break  
		;;  
	*)  
		echo "Invalid choice"  
		;;  
	esac  
done

