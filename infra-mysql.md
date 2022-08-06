# MySql
CEDAR uses `MySql` as the backend for Keycloak as well as storage for messages and logs.

## Install MySql

Please install `MySql version 5.7`:

```sh
sudo apt install mysql-server-5.7
```
Alternatively you can install it by downloading .deb files
```sh
wget https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-server_5.7.32-1ubuntu18.04_amd64.deb-bundle.tar
```
extract the files from the downloaded .tar file and go to that directory and run the following commands to install
```sh
sudo dpkg -i mysql-*
```

## Start MySql
To use [ startmysql ] relplace [ brew services start mysql@5.7 ] with [sudo service mysql starat] in the file [$CEDAR_UTIL_BIN/services-osx/startmysql.sh] which is an alias for [ startmysql ]
Normally mysql will start automatically upon starting the os
```sh
startmysql
```

## Check MySql status
```sh
cedarss
```

You should see the following line in the output:
```
| MySQL                      | Running | openPort    | 3306|                   |
```

## Secure MySql server
```sh
mysql_secure_installation
```

If you get a 'Column count' error, you will need to run the following command first:
```sh
sudo mysql_upgrade -uroot -p
```

Respond to the questions as follows:

| Question                 | Answer |
| -----------                  | ----------- |
|Would you like to setup VALIDATE PASSWORD plugin?  | N|
|New password:            | changeme|
|Re-enter new password:   | changeme|
|Remove anonymous users?  | Y|
|Disallow root login remotely?  | Y|
|Remove test database and access to it?  | Y|
|Reload privilege tables now?            | Y|

## Create CEDAR application users
Connect to the running MySql server

```sh
mysql -uroot -p
```

Execute the below three groups of statements in order to create MySql databases and corresponding users for the different components of CEDAR: 
```sql
CREATE DATABASE IF NOT EXISTS `cedar_keycloak`;
CREATE USER 'cedarMySQLKeycloakUser'@'localhost' IDENTIFIED BY 'changeme';
GRANT ALL PRIVILEGES ON cedar_keycloak.* TO 'cedarMySQLKeycloakUser'@'localhost';
```

```sql
CREATE DATABASE IF NOT EXISTS `cedar_messaging`;
CREATE USER 'cedarMySQLMessagingUser'@'localhost' IDENTIFIED BY 'changeme';
GRANT ALL PRIVILEGES ON cedar_messaging.* TO 'cedarMySQLMessagingUser'@'localhost';
```

```sql
CREATE DATABASE IF NOT EXISTS `cedar_log`;
CREATE USER 'cedarMySQLLogUser'@'localhost' IDENTIFIED BY 'changeme';
GRANT ALL PRIVILEGES ON cedar_log.* TO 'cedarMySQLLogUser'@'localhost';
```
Flush privileges and quit:

```sql
FLUSH PRIVILEGES;
quit
```
## If your run into issues related to mysql installation
remove mysql 
```sh
sudo apt remove --purge mysql*
```
## Mysql installation references
https://www.computingforgeeks.com/how-to-install-mysql-on-ubuntu-focal/
https://www.fosstechnix.com/how-to-install-mysql-5-7-on-ubuntu-20-04-lts/

