# Simple firewalld Centos7 Config that covers old SSH and new SSH port #

```bash
sudo systemctl start firewalld
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --permanent --add-port=2222/tcp
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload
```


To remove a service you can do
```bash
sudo firewall-cmd --permanent --remove-service=ssh
```