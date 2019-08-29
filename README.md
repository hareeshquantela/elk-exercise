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
							
							
							Locally 
							
sudo /etc/init.d/elasticsearch start

                                                  
							On DOCKER
		
Docker/docker-compose.yml  -- > docker-compose up

							Start Kibana
							
cd kibana-7.3.1-linux-x86_64/

./bin/kibana


							File beat paths
							
Filebeat uses the following default paths unless you explicitly change them.

		Home of the Filebeat installation.

/usr/share/filebeat

		
		The location for the binary files.

/usr/share/filebeat/bin


		The location for configuration files.

/etc/filebeat

	
		The location for persistent data files.

/var/lib/filebeat

		The location for the logs created by Filebeat.

/var/log/filebeat




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









