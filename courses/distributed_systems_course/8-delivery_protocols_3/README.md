## Chandy-Lamport algorithm properties
1. Limitations
    - channels are FIFO
    - reliable delivery (no message loss/corruption/duplication)
    - process don't crash while the algorithm is running
2. Adventages
    - algorithm can run without stopping aplication
    - if the graph of processes is strongly connected (all processes are connected in one graph) algorithm will work concurrently and fast
    - multiple processes can be an initiators (you don't have to choose initiator and algorithm is faster)

### What are snapshot good for?
1. Checkpointing
2. Deadlock detection
3. Any stable property detection (property that once true, remains true)

## Causality in Chandy-Lamport algorithm

```
A 'cut' is a 'time frontier' going accros a Lamport diagram, dividing it into 'past' and 'future'
```

An event is in the cut if it is on the past side.
![alt_text](images/past_and_future.png "image_tooltip")

A cut is consistent when, for all events <em>E</em> that are in the cut, if <em>F -> E</em>, then <em>F</em> is also in the cut

Chandy-Lamport algorithm determines a consistent cut.

![alt_text](images/consistent_cut.png "image_tooltip")

**Chandy-Lamport snapshots are causally correct**

## Summary

![alt_text](images/summary_fifo.png "image_tooltip")


### Total order delivery protocol

1. Coordinator process 
    - it's really slow, because coordinator is a bottleneck
    - system stops if coordinator crash

![alt_text](images/coordinator.png "image_tooltip")

## Algorithms properties

### Safety property

Something bad never happens - can be violated in a finite execution (E.g. FIFO/Causal/Totaly ordered delivery)

![alt_text](images/safety_property.png "image_tooltip")

### Liveness property

Something good eventually happens - cannot be violated in a finite execution (The system eventually response to client's request)
E.g. Reliable delivery

![alt_text](images/liveness_property.png "image_tooltip")

```
We need both properties in distributed system

E.g. FIFO
safty property: all messeges deliver in the right order
liveness property: all messages are delivered (not ignored) 
```

![alt_text](images/fifo_example.png "image_tooltip")