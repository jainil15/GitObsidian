**Redirecting Errors to a Log File:**
Create a shell script that generates errors, such as division by zero or file not found. Use error redirection to capture these errors in a log file. Document the error redirection process and the contents of the log file.

`2>` is used for Error Redirection. Redirect stderr to a file using `2>`. For example, `command 2> log.txt` saves error messages to a file.

Script *task2.sh*:
```bash
#!/bin/bash

div() {
	echo $(expr $1 / $2)
}
div 10 0
```

**command:**

```bash
bash task2.sh 2> log.txt
cat log.txt
```


![[Pasted image 20240105231111.png]]
