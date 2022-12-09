Ресурсы:  
http://localhost:2181 - Zookeeper
http://localhost:9002 - zoonavigator 
localhost:9092 - Kafka  
http://localhost:8081 - schema-registry  
http://localhost:8083 - kafka-connect  
http://localhost:8002 - kafka-connect-ui  
http://localhost:8001 - kafka-ui  
http://localhost:9000 - kafka-manager manager/manager  
localhost:3306 - MYSQL DB  
http://localhost:8070 - MYSQL adminer  


Подключаемся к контейнеру kafka:  
kafka-topics.sh --create --topic home-config --partitions 1 --replication-factor 1 --if-not-exists --bootstrap-server kafka:9092  
kafka-topics.sh --create --topic home-offsets --partitions 1 --replication-factor 1 --if-not-exists --bootstrap-server kafka:9092  
kafka-topics.sh --create --topic home-status --partitions 1 --replication-factor 1 --if-not-exists --bootstrap-server kafka:9092  

http://localhost:8070  
Подключаемся:  
mysql  
confluent  
confluent  
confluent  

Выполняем: create.sql  

Для создания конектора:  
curl -X POST -H "Content-Type: application/json" --data '{ "name": "mysql-jdbc-test", "config": { "connector.class": "io.confluent.connect.jdbc.JdbcSourceConnector", "tasks.max": 1, "connection.url": "jdbc:mysql://mysql:3306/confluent?user=confluent&password=confluent", "mode": "incrementing", "incrementing.column.name": "id", "timestamp.column.name": "modified", "topic.prefix": "mysql-jdbc-", "poll.interval.ms": 1000 } }' http://localhost:8083/connectors  
  
На kafka-schema-registry:  
kafka-avro-console-consumer --bootstrap-server kafka-1:9092,kafka-2:9092,kafka-3:9092 --topic mysql-jdbc-test --from-beginning --max-messages 10  