a. Task: Display the contents of a text file - Use commands like `cat`, `less`, or `more` to view the content of a text file. Describe the differences between these commands and identify scenarios where each is preferable.

**`cat`:** cat command is used to concatenate and print on the standard output.
- cat command is simple and straight forward
- cat shows the entire output at the same time.
- cat command doesn't provide navigation.
 Use Cases:
- cat is suitable for small files

![[Pasted image 20240105173145.png]]

**`more`:** `more` command is a filter for paging through text one screenful at a time.
- Allows interactive navigation
- Basic paging functionality
- Suitable for browsing through a file.
- `more` is similar to `less` but less features.
Use Cases:
- to view the text files in the command prompt, displaying one screen at a time in case the file is large

![[Pasted image 20240105174127.png]]

**`less`:** `less` is similar to more but is does not read the entire file before starting, so with large input files it starts up faster than text editor like vi.
- Provides interactive navigation.
- Can handle large files.
- `less` have more features.
- `less` does not read the whole content of a file unlike `more` command.
Use Cases:
- `less` command is used for large files when you need to navigate interactively.

![[Pasted image 20240105173827.png]]
--
b. Task: Display a specific range of lines from a text file - Use the appropriate options with `cat`, `sed`, or `awk` to display a specific range of lines from a text file

For displaying a range of lines from a text file using commands like `cat`, `sed` and `awk`. Following are the commands:

**`cat`:**  cat command is used to concatenate and print on the standard output.
e.g., command for displaying 10 lines from 12 to 22 from largefile.txt.

```bash
cat largefile.txt | head -n 22 | tail -n +12
```
![[Pasted image 20240105180345.png]]

**`awk:`** awk is programming language for scanning pattern and text processing.
e.g., command for displaying 10 lines from 12 to 22 from largefile.txt.

```bash
awk 'NR>=12 && NR <=22' largefile.txt
```

![[Pasted image 20240105181110.png]]

 **`sed`:** sed is stream editor for filtering and transforming text.
e.g., command for displaying 10 lines from 12 to 22 from largefile.txt.

```bash
sed -n '12,22p' largefile.txt
```

![[Pasted image 20240105181229.png]]
