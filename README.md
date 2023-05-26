- Open VM terminal
- Copy below command and past in terminal
```sh 
sudo apt update
sudo apt -y upgrade
sudo apt install unzip
sudo apt install -y apache2
sudo apt install -y mysql-server
sudo apt install -y php libapache2-mod-php php-mysql php-xml php-cli php-cgi php-mbstring php-gd php-curl php-zip
sudo wget https://download.nextcloud.com/server/releases/latest.zip
sudo unzip latest.zip
sudo mv nextcloud/ /var/www/html/nextcloud
sudo chown -R www-data:www-data /var/www/html/nextcloud
sudo mysql -u root -p
```
password: enter
Create Database:
update sql nextcloud user password
```sql
CREATE DATABASE nextcloud;
CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'strongsqluserpassword';
GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost';
FLUSH PRIVILEGES;
EXIT; 
```
Give commands:
```sh
sudo a2ensite nextcloud
sudo a2enmod rewrite
sudo systemctl restart apache2
```
open browser 
http://serverip/nextcloud

Nextcloud admin
username: <nextcloud-admin-username>
Password: <nextcloud-admin-password>

Database user: nextcloud
Database password: strongsqluserpassword
Database name: nextcloud
Database host: localhost(Default)
