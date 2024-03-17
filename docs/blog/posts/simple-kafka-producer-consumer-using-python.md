---
date: 2024-03-17
description: >
  Simple Kafka Producer and Consumer Using Python
categories:
  - General
---

# Simple Kafka Producer and Consumer using Python

To create Kafka producer and Consumer using Python, you'll need to use the kafka-python library, which is a popular choice for interacting with Apache Kafka in Python.
Before you begin, ensure that you have Kafka installed and running in local.

<!-- more -->

## Start Kafka in local

For details, please checkout [this blog](confluent-platform-basics.md)

### Go to the directory where Confluent Platform is downloaded

```shell
cd directory/to/confluent/platform
```

### Start confluent services in local

```shell
bin/confluent local services start
```

## Create a kafka topic

```shell
bin/kafka-topics \
  --create \
  --bootstrap-server localhost:9092 \
  --topic local_test_topic
```

## Installations

**Note:** Make sure you already have `python3` and `pip` installed.

### Install `kafka-python`

```shell
pip3 install kafka-python
```

### Install `uuid`

```shell
pip3 install uuid
```

## Simple Kafka Producer using Python

### `producer.py` file

```python
import uuid

from kafka import KafkaProducer

bootstrap_servers = 'localhost:9092'
topic_name = 'local_test_topic'


def produce():
  producer = KafkaProducer(bootstrap_servers=bootstrap_servers, key_serializer=str.encode, value_serializer=str.encode)

  try:
    while True:
      key = str(uuid.uuid4())
      value = str(uuid.uuid4())
      producer.send(topic=topic_name, key=key, value=value)
      producer.flush()
      print("Message sent key: " + key + " and value " + value)
  finally:
    producer.flush()


if __name__ == "__main__":
  produce()
```

### Run producer code

```shell
python3 producer.py
```

## Simple Kafka Consumer using Python

### `consumer.py` file

```python
from kafka import KafkaConsumer

bootstrap_servers = 'localhost:9092'
topic_name = 'local_test_topic'


def consume():
  consumer = KafkaConsumer(topic_name,  # Topic name to consume messages from
                           group_id='my-group',  # Consumer group ID
                           bootstrap_servers=bootstrap_servers,
                           auto_offset_reset='earliest',  # Reset offset to beginning
                           enable_auto_commit=True)  # Enable auto commit

  for message in consumer:
    key = message.key.decode('utf-8') if message.key else None
    value = message.value.decode('utf-8') if message.value else None

    print(f"Received message: Key={key}, Value={value}, Partition={message.partition}, Offset={message.offset}")

  consumer.close()


if __name__ == "__main__":
  consume()
```

### Run consumer code

```shell
python3 consumer.py
```
