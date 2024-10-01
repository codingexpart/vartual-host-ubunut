
Go To the root of linux and move apache2 `sites-available`
``` shelll
cd /etc/apache2/sites-available
 ```
Copy `default-ssl.conf`
``` shelll
sudo cp default-ssl.conf cf.conf
 ```
Check is file copy or not?
``` shelll
ls
 ```
Make the file empty
``` shell
sudo truncate -s 0 cf.conf
```
Now open in nano
```
sudo nano cf.conf
```
Pest the code 
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName cf.local
    ServerAlias www.cf.local
    DocumentRoot /var/www/cf
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

<Directory /var/www/cf>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```
Create vertial host

```
sudo a2ensite cf.conf
```
Restart Server
```
sudo systemctl reload apache2
```

Check is that available or not

```
cd ..
cd sites-enabled
ls
```
Updeate Host file
```
sudo nano /etc/hosts
```
update your file name in host 
```
127.0.0.1 cf.local
```
copy project to `/var/www` 

Finaly make permition and restart the apache2 server
```
sudo chmod -R 777 /var/www
sudo systemctl restart apache2
sudo systemctl restart mysql
```
