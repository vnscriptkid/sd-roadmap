## Kafka

- Message stream
- Components: producer, broker, consumers
- Producer:
  - can have many publishers
  - 2 steps: (1) determine the partition based on key if exists or partition strategy (2) determine the broker where partition resides in
  - acks: wait for replicas to be in sync before responding, one or all
- Queues
  - Topic
    - Organize same type of messages into a logical group
    - Topic can have many partitions
  - Partitions
    - Unit of parallelism, allow multiple messages can be processed at a time
    - Each partition holds an exclusive subset of messages of one topic
    - Partitions are distributed across brokers, make it possible for horizontal scaling (adding more brokers, more partitions)
    - Each partition has
      - 1 leader replica: handle all reads and writes
      - Many follower replicas (# based on replication factor): incase leader replica goes down, one of follower replica will take over
- Consumers
  -  Consumer group can have many consumers, each does the same job
  -  Limit: #consumers (of group) <= #partitions
  -  Each parition is assigned to one consumer: ensure msg is only read once per group
  -  New consumer joins / Existing consumer leaves: Rebalancing (Reassignment of partitions)

## Sources
- https://www.hellointerview.com/learn/system-design/deep-dives/kafka
- https://courses.arpitbhayani.me/
