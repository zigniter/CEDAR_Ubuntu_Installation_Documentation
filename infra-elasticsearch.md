# Elasticsearch
CEDAR uses `elasticsearch` to make search for artifacts possible.

## Install Elasticsearch

Please install `elasticsearch version 6.8`:

```sh
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
sudo apt update
sudo apt install elasticsearch
```
## Install Elasticsearch Alternative two
Download elasticsearch version 6.8 and put it under ~/CEDAR directory or ${CEDAR_HOME}
To start elastic you may change the command [ brew services start elasticsearch@6 ] in the alias [ $CEDAR_UTIL_BIN/services-osx/startelastic.sh ] to [ ${CEDAR_HOME}/elasticsearch-6.8.0/bin/elasticsearch ] the use [ startelastic] 

```sh
${CEDAR_HOME}/elasticsearch-6.8.0/bin/elasticsearch
```

    
???+ warning "Important"

    Do not add Elasticsearch as a background service! We will have scripts in place which will start it when necessary.

    **Do not start Elasticsearch at this point!**
 
## Configure Elasticsearch

```sh
vi /usr/local/etc/elasticsearch/elasticsearch.yml
```

Around `line #17`, change the cluster name configuration:

```
cluster.name: elasticsearch_cedar
```

## Start Elasticsearch

```sh
startelastic
```

## Check Elasticsearch status
```sh
cedarss
```

You should see the following lines in the output:
```
| Elasticsearch-REST         | Running | httpResponse| 9200| HTTP/1.1\s200\sOK |
| Elasticsearch-Transport    | Running | openPort    | 9300|                   |
```

## Also run the following scripts
curl -X PUT "localhost:9200/cedar-search/_settings?pretty" -H 'Content-Type: application/json' -d'
{
    "index.blocks.read_only_allow_delete": "false"
}
'

curl -X PUT "localhost:9200/cedar-search/_settings?pretty" -H 'Content-Type: application/json' -d'
{
    "index.blocks.read_only_allow_delete": null
}
'


curl -X GET "localhost:9200/_cat/indices"


GET /_cat/indices



PUT some_index/_settings
{
    "index.blocks.read_only_allow_delete": null
}
