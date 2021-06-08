
1. Start Zookeeper
  ```bash
  docker run --rm \
    --name zookeeper \
    -e ALLOW_ANONYMOUS_LOGIN=yes \
    zookeeper:3.4
  ```
  
2. Start Kafka
  ```bash
  docker run --rm \
    --name kafka \
    --link zookeeper \
    -p 9092:9092 \ 
    -e ALLOW_PLAINTEXT_LISTENER=yes \
    -e KAFKA_ADVERTISED_HOST_NAME=127.0.0.1 \
    -e KAFKA_ADVERTISED_PORT=9092 \
    -e KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181 \
    bitnami/kafka:2.4.1
  ```

3. Start OAP
  ```bash
  docker run --rm \
    -—link kafka \
    --name oap \
    -e SW_KAFKA_FETCHER=default \
    -e SW_KAFKA_FETCHER_SERVERS=kafka:9092 \
    -e SW_KAFKA_FETCHER_PARTITIONS=1 \
    -e SW_KAFKA_FETCHER_PARTITIONS_FACTOR=1 \
    apache/skywalking-oap-server:8.5.0-es6
  ```
