# Startup and stop scripts

There are start and stop scripts available for each service that is present in the CEDAR ecosystem.

These will be introduced throughout this guide. As an example starting and stopping `MongoDB` after a installation would be done with:

```sh
sudo service mongod start
brew service mongod stop
```

In the CEDAR environment we have these aliases for simplicity:

```sh
startmongo
stopmongo
```
You may modify the content of the scripts by going to their alias using alias startmongo for example and editing and saving using your favoriate editor

## List of startup scripts
A non-exhaustive list of the start aliases is as follows

* Infrastructure
```sh
startmongo
startneo
startmysql
startelastic
startkibana
startredis
startrc
startnginx
startkk
```

* Microservices
```sh
startmessaging
startgroup
startrepo
startresource
startschema
startartifact
startterminology
startuser
startvaluerecommender
startsubmission
startworker
startopenview
startinternals
```
* Frontend
```sh
starteditor
```

## List of stop scripts
For each start script/alias there is a corresponding stop script (with some exceptions).
We will not enumerate all these.
The full list of aliases available can be listed using:

```sh
alias
```
