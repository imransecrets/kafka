# kafka

# Uber Example

## Data Location Updates

- Data location is updated every 1 second.
- If there are 100 riders, then 100 entries are passed to the data server.
- Due to throughput limitations, the data server can go down if it receives too many requests simultaneously.

## Throughput Challenges

- Thousands of users may be using the service at the same time, causing throughput issues.

# Kafka Overview

## Throughput and Storage

- Kafka has high throughput and low storage requirements.
- Queries are not possible directly in Kafka.
- Databases, on the other hand, have low throughput but high storage capacity and support querying.

# Kafka Concepts

## Core Components

### Producer
- The entity that publishes data to Kafka topics.

### Consumer
- The entity that subscribes to Kafka topics and processes the data.

### Topic
- A category or feed name to which records are stored and published.
- Topics are divided into partitions.

## Partitions

- Partitions can be divided by area, e.g., Lahore, Karachi, Islamabad.
- Partitions cannot be time-sliced, e.g., all data from 10 to 11 in one partition and 11 to 12 in another.

## Partition to Consumer Allocation

- 4 partitions, 1 consumer: All partitions are allotted to one consumer.
- 4 partitions, 2 consumers: Two partitions are allotted to each consumer.
- 4 partitions, 3 consumers: Two partitions are allotted to one consumer and the remaining two to each of the other consumers.
- 4 partitions, 4 consumers: Each partition is allotted to one consumer.
- 4 partitions, 5 consumers: All partitions are allotted, and one consumer has to wait.

### Rules

- One consumer can consume multiple partitions.

# DOCKER INSTALLATION
1. IN WINDOW
   Download and install from the official website for window and use (but we are not using this)
2. THROUGH DOCKER
   Get the docker image
   docker pull apache/kafka:3.7.0 (we use this on)
3. Open Docker Desktop search for Apache/kafka:3.7.0 and install

   https://hub.docker.com/r/apache/kafka/tags

         docker pull apache/kafka:3.7.0
   
## image created now run the image
    docker run -d -p 9092:9092 --name kafka [image id complete or 1st 4 letters]

    container created and running you can check
    docker ps 

   ![image](https://github.com/imransecrets/kafka/assets/8496861/de2e7c3e-d870-4d63-9fda-85023839620a)



## Now execute the container command prompt
   docker exec -it [container id complete of 1st f letters] bin/bash
   
   ![image](https://github.com/imransecrets/kafka/assets/8496861/d17fac28-39fd-481c-bec9-bf9ca4808dcb)
    
       cd opt/kafka/bin
    
   ![image](https://github.com/imransecrets/kafka/assets/8496861/84d47625-86fc-4050-aaa8-b997f50b1ae0)

      98de6cf9f7f0:/$ ls /opt/kafka/bin

   ![image](https://github.com/imransecrets/kafka/assets/8496861/136bb37d-9ce9-44a9-98ee-9c257cd0a870)
   For getting help
        
         98de6cf9f7f0:/opt/kafka/bin$  /opt/kafka/bin/kafka-topics.sh --help
   now go to https://kafka.apache.org/documentation/ and copy some command part

   ![image](https://github.com/imransecrets/kafka/assets/8496861/3bd5317a-8906-4bba-851e-68308ea8240e)
   For creating TOPIC
         
         /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic my-topic

   ![image](https://github.com/imransecrets/kafka/assets/8496861/c04a214f-c189-4dda-8408-123fb3538dea)
   For deleting TOPIC 
   
      /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic my-topic

   ![image](https://github.com/imransecrets/kafka/assets/8496861/d04bef18-9497-413d-ae45-dcb7b6e691aa)
   For describing Topic
   
      98de6cf9f7f0:/$ /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic my-topic

   ![image](https://github.com/imransecrets/kafka/assets/8496861/cea3b11f-2600-4a77-ae13-751647bb2efb)
   Now create producers for some topic and write down some material
         
      98de6cf9f7f0:/opt/kafka/bin$ /opt/kafka/bin/kafka-console-producer.sh --bootstrap-server localhost:9092 --topic my-topic

   ![image](https://github.com/imransecrets/kafka/assets/8496861/69df6611-b9ac-4f29-a9c1-56d0ca4e9184)

   Now open new window and again go to command prompt to docker container

   ![image](https://github.com/imransecrets/kafka/assets/8496861/1a399c15-043d-4ed5-a0fe-d80935443459)

   Now create consummer for same topic

      98de6cf9f7f0:/opt/kafka/bin$ /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my-topic --from-beginning

   ![image](https://github.com/imransecrets/kafka/assets/8496861/5f735bc0-5be3-436d-9708-0790bc8cbc38)

   ## Consumer Groups
  * Check whether any group was created for previously created consumers or not

          98de6cf9f7f0:/opt/kafka/bin$ /opt/kafka/bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
   
   ![image](https://github.com/imransecrets/kafka/assets/8496861/853d0e28-4f2f-4bc8-b17b-2c9b94219044)

      98de6cf9f7f0:/opt/kafka/bin$ /opt/kafka/bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group hello

   ![image](https://github.com/imransecrets/kafka/assets/8496861/ed72d466-dbaf-4ebe-8e6b-71f352adf46c)

   * Note :- if you create a new consumer with the same group then it will replace the previous consumer with a new one

     1st one created with same group name hello 
     ![image](https://github.com/imransecrets/kafka/assets/8496861/2029c78f-dbba-44aa-943d-2e337e95c5e2)

     2nd one created with same group name will receive messages from where 1st one finished

     ![image](https://github.com/imransecrets/kafka/assets/8496861/f17391ba-c600-488f-8add-a1c71fd11cdb)

     again check the groups
     98de6cf9f7f0:/opt/kafka/bin$ /opt/kafka/bin/kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
     
     ![image](https://github.com/imransecrets/kafka/assets/8496861/2482bd8d-202f-4a12-8adf-48a474b7a44b)


     


   

   



   



