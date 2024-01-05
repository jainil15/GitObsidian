**Start Systemd Service**
Task: Download any web server(Nginx, Apache) and run it via Systemd. Check the status of the service, restart it with some changes and make sure that service run when host get restarted. Document the steps.

To download Apache use command:
```bash
sudo apt install apache2
```

![[Pasted image 20240105231951.png]]

To check status of Apache use command:
```bash
sudo systemctl start apache2
```

and to check status:
```bash
sudo systemctl status apache2
```

![[Pasted image 20240105232201.png]]

To stop apache2 use command:
```bash
sudo systemctl stop apache2
```

To edit apache2 config file use command:
```bash
sudo systemctl edit apache2
```

![[Pasted image 20240105233036.png]]

To restart use command:
```bash
sudo systemctl restart apache2
```

![[Pasted image 20240105233135.png]]
