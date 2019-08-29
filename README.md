# elk-exercise

SIDDHI IN PRACTICE



Navigate into :  cd /usr/lib/wso2/wso2sp/4.4.0/bin
      sudo ./editor.sh

Stream processor studio : http://localhost:9390/editor

Start zookeeper    : bin/zookeeper-server-start.sh config/zookeeper.properties

Start kafka server : bin/kafka-server-start.sh config/server.properties

Create topic       : bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test

Send messages      : bin/kafka-console-producer.sh --broker-list localhost:9092 --topic kafka-impl

Consume messages   : bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic kafka-impl-result --from-beginning





	                                                Elastic search
                                                  

https://www.elastic.co/guide/en/elasticsearch/reference/7.3/docker.html

Elastic search (Run using docker ) ::  docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.3.1
Or Docker ps -a , Docker start {ID}

Run on Docker using docker-compose.yml  -- > docker-compose up



Indices list            : curl 'localhost:9200/_cat/indices?v'

Search records by index : curl 'localhost:9200/kafkadata/_search?q=*&pretty'

Matching query          : curl -X GET "localhost:9200/kafkadata/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { "match": { "name": "hareeseh" } }
}
'

Pull range : 

curl -X GET "localhost:9200/elas_log/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": {
    "bool": {
      "must": { "match_all": {} },
      "filter": {
        "range": {
          "age": {
            "gte": 20,
            "lte": 40
          }
        }
      }
    }
  }
}
'









