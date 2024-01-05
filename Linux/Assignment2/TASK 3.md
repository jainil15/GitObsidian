a. Task: Search and replace text in a file - Use the `sed` command to search for and replace specific text in a text file. Demonstrate the use of regular expressions.

e.g., Replace all "Nulla" with "Jainil" in smallfile.txt file.

```bash
sed `s/Nulla/Jainil` smallfile.txt
```

![[Pasted image 20240105185716.png]]
Following example demonstrating the use of regular expression in `sed`
example: replace all the word that contains 'is' with 'Replaced'
```bash
sed 's/[a-zA-z]*is*[a-zA-Z]*/Replaced/g' smallfile.txt
```

![[Pasted image 20240105191112.png]]

**b. Task:** Extract and manipulate data from a CSV file - Use `awk` to extract and manipulate data from a CSV file. Show how to perform operations like summing columns or filtering data based on criteria.

1. Summation of salary column:
```bash
awk -F',' '{sum+=$7}' END {print "Total Salary: ", sum} csvrecords.csv
```

![[Pasted image 20240105194450.png]]
2. Filter by different profession like developer:
```bash
awk -F',' '$6 == "developer"' csvrecords.csv
```

![[Pasted image 20240105194737.png]]

Print all the name that starts with 'J'
```bash
awk -F',' '$2 ~ /^J/' csvrecords.csv
```

![[Pasted image 20240105195316.png]]

Print all the id between 500 and 750:
```bash
awk -F',' '$1>=500 && $1<=750' csvrecords.csv
```

![[Pasted image 20240105195514.png]]