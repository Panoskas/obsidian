- ### cd to kafka location

`----------------------------------------------------------------`


- ### Get topic list
	`bin/kafka-topics.sh --list --zookeeper localhost:2181`

- ### Messages from <topic_name>
	`bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic name> --from-beginning`

- ### Delete a topic
`bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic <topic_name>`

- ### List all the consumer groups
`bin/kafka-consumer-groups.sh  --list --bootstrap-server localhost:9092`

- ### More info about a group
`bin/kafka-consumer-groups.sh --describe --group <group_name> --bootstrap-server localhost:9092`