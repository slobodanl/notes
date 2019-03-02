_Written by: Reza Shams Amiri_
# 02 Kafka
   1. Nothing but a Transaction log
      1. When you replay the log, the log is the ultimate source of truth
   1. Producer and consumer are decoupled (separation of concern)
      1. The consumers consume data at their own rate
## Zookeeper:
   1. Kafka uses Zookeeper to findout about all the producer and consumer nodes
   1. Each Kafaka server registers itself with Zookeeper
      1. I am ready to host a topic, you can give me a topic to me and i will keep it.
         1. partitions: A means to group the data and you can increase parallel processing
         1. replication factor: A means to acheive redunduncy by copying the exact same data
   1. One server is elected as leader and others are elected as follower
      1. When leader goes down Zookeeper elects another leader

**Kafka guaranties data consistency as long as "replication factor-1" servers are available!**{.note}

## Producer:
   1. Producer is a process which generates the data that you want to push to a topic
   1. Each time a producer pushes a message to a Kafka topic it essentially pushes a message to a tranaction log
         - That message gets an ID -

## Consumer:
   1. Can consume the data from wherever it wants (earliest/latest/... message)
   1. Each consumer-"group" has an offset registered which shows what was the latest read



## Refs:
1. [Getting Started with Kafka by Nikhil Nanivadekar - YouTube][GSWKBNNY]


* * *
Creation date: _2019-03-02_

[GSWKBNNY]: https://www.youtube.com/watch?v=kQyyJhuIf3k&index=28&list=PLUQORQEatnJfUeQxIZEZ-Psf_bzzz4sgX
