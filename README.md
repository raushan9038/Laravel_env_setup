# Laravel_env_setup

1. apt-get update -y
2. apt upgrade -y
3 . apt install apache2 -y
4. apt install php7.4 libapache2-mod-php7.4 php7.4-curl php-pear php7.4-gd php7.4-dev php7.4-zip php7.4-mbstring php7.4-mysql php7.4-xml curl -y

5. vi /etc/php/7.4/apache2/php.ini
6. systemctl start apache2
7. systemctl enable apache2
8. curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
chmod +x /usr/local/bin/composer

9. composer --version
10. cd /var/www/html
11. composer create-project laravel/laravel projectname --prefer-dist
12. cd projectname
13. php artisan         -----> we will see the laravel version
14. chown -R www-data:www-data /var/www/html/projectname
15. chmod -R 775 /var/www/html/projectname/storage
16. nano /etc/apache2/sites-available/laravel.conf

<VirtualHost *:80>
ServerName ip address of the server
ServerAdmin admin@example.com
DocumentRoot /var/www/html/projectname/public
<Directory /var/www/html/projectname>
AllowOverride All
</Directory>
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

17. a2ensite laravel.conf
18. a2enmod rewrite
19. systemctl restart apache2

Now we can access the Laravel app by ip address of the server.

 
