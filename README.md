



Go To the root of linux and move apache2 `sites-available`
``` shelll
cd /etc/apache2/sites-available
 ```
Copy `default-ssl.conf`
``` shelll
sudo cp default-ssl.conf folderName.conf
 ```
Check is file copy or not?
``` shelll
ls
 ```
Make the file empty
``` shell
sudo truncate -s 0 folderName.conf
```
Now open in nano
```
sudo nano folderName.conf
```
Pest the code 
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName folderName.local
    ServerAlias www.folderName.local
    DocumentRoot /var/www/folderName
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
Check is that available or not

```
cd ..
cd /sites-enabled
```
Updeate Host file
```
sudo nano /etc/hosts
```
update your file name in host 
```
127.0.0.1 folderName.local
```
copy project to `/var/www` 

Finaly make permition and restart the apache2 server
```
sudo chmod -R 777 /var/www
sudo systemctl restart apache2
sudo systemctl restart mysql
```
