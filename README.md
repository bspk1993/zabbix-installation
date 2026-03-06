# zabbix-installation

youtube link : https://www.youtube.com/watch?v=G9zOtA3CMLo

go to zabbix.com

select the required configuration of the instance to install , I am going to Ubuntu-22.04 ,t2.medium, 30GB GP3 storage, Security group -10051 ,


go to the below steps;

wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu22.04_all.deb
dpkg -i zabbix-release_latest_7.0+ubuntu22.04_all.deb
apt update

apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent

mysql -u root -p
password
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> set global log_bin_trust_function_creators = 1;
mysql> quit;

mysql -uroot -p
password
mysql> set global log_bin_trust_function_creators = 0;
mysql> quit;

DBPassword=password

# systemctl restart zabbix-server zabbix-agent apache2
# systemctl enable zabbix-server zabbix-agent apache2

i  have given the login credentials as 

username : Admin
Password: zabbix


    1  wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_7.0+ubuntu22.04_all.deb
    2  dpkg -i zabbix-release_latest_7.0+ubuntu22.04_all.deb
    3  apt update
    4  apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
    5  mysql -uroot -p
    6  systemctl status mysql
    7  mysql -u root -p
    8  mysql --version
    9  systemctl enable mysql
   10  apt update
   11  apt install mysql-server -y
   12  systemctl status mysql
   13  mysql -u root -p
   14  zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
   15  history
