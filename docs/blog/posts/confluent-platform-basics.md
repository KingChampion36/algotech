---
date: 2024-03-16
#authors: [techblogs]
description: >
  Getting Started With Confluent Platform
categories:
  - General
---

# Getting Started With Confluent Platform

Confluent Platform is a full-scale streaming platform that enables you to easily access, store, and manage data as continuous, real-time streams.

Check out the official documentation of confluent [here](https://docs.confluent.io/platform/current/platform.html).

<!-- more -->

## Download Confluent Platform in your local

Download confluent platform from confluent's official website [here](https://www.confluent.io/get-started/?product=self-managed)

## Go to the directory where Confluent Platform is downloaded

```shell
cd directory/to/confluent/platform
```

### Help command

```shell
bin/confluent local --help
```

#### Output

```shell
Use the "confluent local" commands to try out Confluent Platform by running a single-node instance locally on your machine. Keep in mind, these commands require Java to run.

Usage:
  confluent local [command]

Available Commands:
  current     Get the path of the current Confluent run.
  destroy     Delete the data and logs for the current Confluent run.
  services    Manage Confluent Platform services.
  version     Print the Confluent Platform version.

Global Flags:
  -h, --help            Show help for this command.
  -v, --verbose count   Increase verbosity (-v for warn, -vv for info, -vvv for debug, -vvvv for trace).

Use "confluent local [command] --help" for more information about a command.
```

## Start Services

To know more about `Services`, use the help command:

```shell
bin/confluent local services --help
```

### Start confluent services in local

```shell
bin/confluent local services start
```

### Output

```shell
Using CONFLUENT_CURRENT: /var/folders/n1/zs8c9zw95ng2qy812fwv5rjh0000gn/T/confluent.646371
Starting ZooKeeper
ZooKeeper is [UP]
Starting Kafka
Kafka is [UP]
Starting Schema Registry
Schema Registry is [UP]
Starting Kafka REST
Kafka REST is [UP]
Starting Connect
Connect is [UP]
Starting ksqlDB Server
ksqlDB Server is [UP]
Starting Control Center
Control Center is [UP]
```

## Verify that Kafka is running in local

This can be verified by either using cuRL or telnet:

```shell
telnet localhost 9092
```

## View the Control Center UI

Control Center UI can be viewed at [http://localhost:9021](http://localhost:9021)

## List kafka topics in the cluster

```shell
bin/kafka-topics \
  --list \
  --bootstrap-server localhost:9092
```

## Create a kafka topic

```shell
bin/kafka-topics \
  --create \
  --bootstrap-server localhost:9092 \
  --topic local_test_topic
```

## Verify that the kafka topic is created

```shell
bin/kafka-topics \
  --list \
  --bootstrap-server localhost:9092 \
  | grep 'local_test_topic'
```

### Output

```shell
local_test_topic
```

## Describe the kafka topic

```shell
bin/kafka-topics \
  --describe \
  --bootstrap-server localhost:9092 \
  --topic local_test_topic
```

### Output

```shell
Topic: local_test_topic	TopicId: c1wfq1qDSXGt6gfVU3qgzQ	PartitionCount: 1	ReplicationFactor: 1	Configs: segment.bytes=1073741824
	Topic: local_test_topic	Partition: 0	Leader: 0	Replicas: 0	Isr: 0	Offline:
```

## Produce to the kafka topic

```shell
bin/kafka-console-producer \
  --bootstrap-server localhost:9092 \
  --topic local_test_topic \
  --property parse.key=true \
  --property key.separator=:
```

The key and value should be separated by `:` while writing messages in the console.

### Example:

```shell
key1:message1
key2:message2
```

## Consume from the kafka topic

Open a new tab in the terminal and consume messages from the kafka topic.

```shell
bin/kafka-console-consumer \
  --bootstrap-server localhost:9092 \
  --topic local_test_topic \
  --property print.key=true \
  --from-beginning
```

### Output

```shell
key1	message1
key2	message2
```
