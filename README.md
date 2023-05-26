# nextcloud

Commands
```sh
sudo apt update
sudo apt upgrade
sudo apt install unzip
sudo apt install -y apache2
sudo apt install -y mysql-server
sudo apt install -y php libapache2-mod-php php-mysql php-xml php-cli php-cgi php-mbstring php-gd php-curl php-zip
cd /var/www/html
sudo wget https://download.nextcloud.com/server/releases/nextcloud-22.2.0.zip
cd ~
sudo unzip /var/www/html/nextcloud-22.2.0.zip
mv nextcloud/ /var/www/html/nextcloud
sudo chown -R www-data:www-data /var/www/html/nextcloud
sudo chmod -R 755 /var/www/html/nextcloud
```
Setup Database
```sh
sudo mysql -u root -p
```
Database sepup:
```sql
CREATE DATABASE nextcloud;
CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
config nextcloud
```sh
sudo vi /etc/apache2/sites-available/nextcloud.conf
```
copy and the configuration 
```confg
<VirtualHost *:80>
    DocumentRoot /var/www/html/nextcloud
    ServerName your-server.com

    <Directory /var/www/html/nextcloud>
        Require all granted
        Options FollowSymlinks MultiViews
        AllowOverride All

       <IfModule mod_dav.c>
            Dav off
        </IfModule>

    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```
run below commands
```sh
sudo a2ensite nextcloud
sudo a2enmod rewrite
sudo systemctl restart apache2
```
note data folder
```sh
cd /var/www/html/nextcloud/data
```




