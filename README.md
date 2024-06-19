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

      ls

   ![image](https://github.com/imransecrets/kafka/assets/8496861/136bb37d-9ce9-44a9-98ee-9c257cd0a870)

   


