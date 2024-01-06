<center><h1>TASK 4</h1></center>

**Cronjob**  
**Task:** Create a shell script which will take backup of any Text file on daily 11:30 AM and paste into the /backup folder.

1. Create *save_backup.sh* shell script:

```bash
#!/bin/bash  
backup_filename="$(date +%Y%m%d%H%M%S)_population_backup.txt"  
cp "/home/jainil/Desktop/Assignment5/population.txt" "/home/jainil/Desktop/Assignment5/backup/$backup_filename"  
echo "Backup create with name $backup_filename"
```

2. Edit the crontab by using command,:
```bash
crontab -e
```

Then add `30 11 * * * /home/jainil/Desktop/Assignment/save_backup.sh` at the end of the file, this means that save_backup.sh file will run at 11:30am.

![[Pasted image 20240106014317.png]]
