## State replication

### Reasons to do replication
1. Mitigrationg data loss (fault tolerance)
2. Data locality (you want your data to be close to you)
3. Scalability (serve more request)

### Reasons to not do replication
1. Having to keep replicas consistent is a huge problem
2. Expensive (you need more machines)

## Determinism

Relates multiple runs of a system to each other.

![alt_text](images/violation_of_determinism.png "image_tooltip")

This is a violation of determinism, not of totally ordered delivery.

### Strong consistency

A replicated storage system is strongly consistent if clients can't tell that it's replicated.

### What can go wrong

1. Read your writes violation

![alt_text](images/read_your_writes_violation.png "image_tooltip")

2. FIFO consistency violation - FIFO anomaly between replicas

![alt_text](images/fifo_violation.png "image_tooltip")

FIFO consistency - writes done by a single process are seen by all processes in the order they were issued.

3. Causal consistency violation

![alt_text](images/causal_consistency_violation.png "image_tooltip")

Causal consistency - writes that are potentially causally related (i.e. related by happens before) must be seen by all processes in the same order.


### Consistency hierarchy

![alt_text](images/consistency_hierarchy.png "image_tooltip")
