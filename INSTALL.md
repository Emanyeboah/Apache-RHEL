## How to set up the Apache Web Server on RHEL
### 1. Install Apache web server on RHEL.
```
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```
### 2. Create Your Website HTML.
```
sudo nano /var/www/html/mywebsite/index.html
```
Paste:
```
<!DOCTYPE html>
<html>
<head><title>Welcome to My Website</title></head>
<body>
<h1>This is my first web page on Apache with HTTPS!</h1>
</body>
</html>
```
### 3. Generate a Self-Signed SSL Certificate.
Create a directory:
```
sudo mkdir /etc/httpd/ssl
```
Generate the certificate:
```
sudo openssl req -x509 -nodes -days 365 \
  -newkey rsa:2048 \
  -keyout /etc/httpd/ssl/apache.key \
  -out /etc/httpd/ssl/apache.crt
```
**Common Name:** mywebsite.local
### $. Enable SSL Module & Update Apache Config.
Install SSL Module:
```
sudo yum install mod_ssl -y
```
