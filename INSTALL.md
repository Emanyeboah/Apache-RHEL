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
