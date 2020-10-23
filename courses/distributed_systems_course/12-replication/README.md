# Replication

## Strong consistency

### Primary-backup replication

One primary replica and multiple backup replicas. Client talks only with primary replica.

![alt_text](images/primary_backup_replication.png "image_tooltip")

### Chain replication

"Chain Replication for supporting high throughout and availability", von Renesse and Schneider, 2004

![alt_text](images/chain_replication.png "image_tooltip")

Throughput - number of actions per unit of time
Latency - time between invocation and complition of a single action

**Chain replication has the biggest improvement over primary-backup replication when 10-15% of requests are writes**