# Redis
CEDAR uses `Redis` as message queue for communication between components of the system.

## Install Redis

Please install `Redis, version 6.0.x`:

```sh
sudo apt install redis-server
```

## Start Redis
```sh
sudo service redis-server start
```
???+ warning "Important"

    If you want to use startredis you need to change the scriprt by looking into the alias and replacing it with the above command.

## Modify the Start Redis Alias 

```sh
alias startredis
```
you should see something similar to 
alias startredis='$CEDAR_UTIL_BIN/services-osx/startredis.sh'
modifty the file startredis.sh using your favorite editor and change the command [ brew services start redis ] with [ sudo service redis-server start ]

## Start Redis
```sh
startredis
```

## Check Redis status
```sh
cedarss
```

You should see the following line in the output:
```
| Redis-persistent           | Running | redisPing   | 6379|                   |
```
