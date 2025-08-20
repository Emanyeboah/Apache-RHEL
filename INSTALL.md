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
### 4. Enable SSL Module & Update Apache Config.
Install SSL Module:
```
sudo yum install mod_ssl -y
```
Edit SSL config:
```
sudo nano /etc/httpd/conf.d/ssl.conf
```
Update these lines:
```
SSLCertificateFile /etc/ssl/mycerts/apache-selfsigned.crt
SSLCertificatekeyfile /etc/ssl/mycerts/apache-selfsigned.key
```
Change server name:
```
ServerName mywebsite.local
```
### 5. Test Apache Config.
```
sudo apachectl configtest
```
If the Syntax is OK, proceed.
### 6. Restart Apache.
```
sudo systemctl restart httpd
```
### 7. Visit Your Site.
Go to:
```
https://mywebsite.local
```
- Browser will warn about the self-signed cert (completely normal)
- Proceed, and your launch page will say:
  " This is my first web page on Apache!"

