## Home server 
```bash
#!/bin/bash 
sudo -i
apt update -y 
apt install nginx -y 
systemctl start nginx 
systemctl enable nginx 
echo "this is Home server $HOSTNAME" >/var/www/html/index.html
```

## shop Server 
```bash
#!/bin/bash 
sudo -i
apt update -y 
apt install nginx -y 
systemctl start nginx 
systemctl enable nginx
rm /var/www/html/*.html 
mkdir /var/www/html/shop
echo "this is shop server $HOSTNAME" >/var/www/html/shop/index.html
```
## Hair Server 
```bash
#!/bin/bash 
sudo -i
apt update -y 
apt install nginx -y 
systemctl start nginx 
systemctl enable nginx
rm /var/www/html/*.html 
mkdir /var/www/html/Hair
echo "this is Hair server $HOSTNAME" >/var/www/html/Hair/index.html
```


