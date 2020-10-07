---
id: apache
title: Apache Configuration
---
The Croissant Framework is designed to work with the Apache webserver as it makes use of Apache's `.htaccess` file to handle URL rewriting. It's possible to use [nginx](nginx) or [NodeJS](nodejs) should you desire.
## Apache Configuration
```xml
<virtualhost *:80>
	ServerAdmin webmaster@localhost
	ServerName www.myserver.co.uk
	DocumentRoot /var/www/Croissant/croissant/docroot
	ErrorLog /var/log/apache2/croissant-error.log
	LogLevel warn
	CustomLog /var/log/apache2/myserver-access.log
	combined ServerSignature On 
</virtualhost>
```