# MongoDB
CEDAR uses `MongoDB` as the storage for the CEDAR artifacts: fields, elements, templates and metadata instances.

## Install MongoBD

Please install `MongoDB-Community, version 3.4`:

```sh
sudo apt update
sudo apt upgrade

sudo wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list

sudo apt update
sudo apt install -y mongodb-org
sudo systemctl start mongod
sudo systemctl status mongod
sudo systemctl stop mongod
sudo service mongod start
sudo service mongod stop
```

## Start MongoDB without access control
In order to have secure access to MongoDB, we will create a privileged user, a dedicated CEDAR user, and we will turn on access control.

First, we will create a power user. You will need to start MongoDB without access control from the command line.

Please replace the path below with the one applicable to your system:

```sh
/usr/bin/mongod \
  --port 27017 \
  --dbpath /usr/local/var/mongodb
```

## Create privileged user
Once mongoDB is started, in a different terminal connect to it:

```sh
/usr/bin/mongo
```

In this new terminal use the `admin` collection and create a privileged user:
```js
use admin

db.createUser(
  {
    user: "mongoRootUser",
    pwd: "changeme",
    roles: [ { role: "root", db: "admin" } ]
  }
)

exit
```

Close this terminal, and stop the running MongoDB by pressing ++ctrl++ + C.

## Start MongoDB with access control
To use the following command to start mongo edit the alias at [$CEDAR_UTIL_BIN/services-osx/startmysql.sh] and change [ brew services start mongodb-community@3.4 ] to [sudo service mongod start] 

```sh
startmongo
```

## Create CEDAR application user
Connect to MongoDB with the previously created user:
```sh
/usr/bin/mongo \
  --port 27017 \
  --username "mongoRootUser" \
  --password "changeme" \
  --authenticationDatabase "admin"
```

Create the user:
```js
use cedar

db.createUser(
  {
   user: "cedarMongoUser",
   pwd: "changeme",
   roles: [ "readWrite"]
  })

exit
```

## Restart MongoDB
```sh
stopmongo
startmongo
```

## Check MongoDB status
```sh
cedarss
```

You should see the following line in the output:
```
| MongoDB                    | Running | openPort    |27017|                   |
```

## Edit MongoDB config
/etc/mongod.conf

```conf
# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0
```
