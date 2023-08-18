---
title: "Hosting Laravel on Linux"
subtitle: ""
date: 2023-08-18T14:42:54+07:00
lastmod: 2023-08-18T14:42:54+07:00
draft: true
authors: []
description: ""

tags: []
categories: []
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

<!--more-->

Install server (Apache/Nginx)
-----------------------------

Install environment (PHP, MariaDB)
----------------------------------

```
sudo apt install php8.2
```

```
sudo apt install php8.2-mysql libapache2-mod-php php8.2-imap php8.2-ldap php8.1-xml php8.2-fpm php8.2-curl php8.2-mbstring php8.2-zip
```

```
sudo wget https://dev.mysql.com/get/mysql-apt-config_0.8.22-1_all.deb # download mysql repo
sudo apt install ./mysql-apt-config_0.8.22-1_all.deb # install packages needed for the mysql server
sudo apt update # updating our apt repository
sudo apt install mysql-server # installation of the mysql server
```

Install Composer for Laravel
----------------------------

```
sudo curl -sS https://getcomposer.org/installer | php
```

```
#set composer as global function by moving to global location
sudo mv composer.phar /usr/local/bin/composer
```

Install Our App by Git Pull or Git Clone or Install New App Instead
-------------------------------------------------------------------

Set Owner of Our Apps to Served as Website
------------------------------------------

```
sudo chown -R www-data:www-data /var/www/html/app/
sudo chmod -R 775 /var/www/html/app/
```

Set Virtual Host to Pointing Domain
-----------------------------------

```
sudo nano /etc/apache2/sites-available/app.conf
```

```
<VirtualHost *:80 *:3000>
    ServerAdmin admin@example.com
    DocumentRoot /var/www/html/app/

    <Directory /var/www/html/app/>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
    </Directory>

    LogLevel debug
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

Activate Mod Rewrite for Dynamic Routing
----------------------------------------

```
sudo a2enmod rewrite
sudo a2ensite app.conf
```

Set .env And .htaccess
----------------------

Reload Apache
-------------

```
sudo systemctl reload apache2
```

* * * * *

Special thanks to **Achebe Okechukwu** for detailed tutorial on [hackernoon](https://hackernoon.com/how-to-deploy-a-laravel-app-with-the-debian-11-vagrant-box)