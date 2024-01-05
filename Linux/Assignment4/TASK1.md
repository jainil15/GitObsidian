**Debugging Scripts :**
 Objective: Write a buggy shell script and use debugging to identify and fix the issue using the "set" and their options. Check which options is used in which scenario, document it with all the information.
 
```bash
set +x  
add() {  
	local a=$1  
	echo $(expr 1 + $a)  
}  
set -x  
echo $(add 'a')
```

![[Pasted image 20240105225634.png]]
**fixed Script:**
```bash
set +x  
add() {  
	local a=$1  
	echo $(expr 1 + $a)  
}  
set -x  
echo $(add 4)
```

