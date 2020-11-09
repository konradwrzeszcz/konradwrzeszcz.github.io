## Making copies for fault tolerance
1. Dealing with message omission via reliable delivery protocols
- sending a message many times until one is acknowledge (at-least-once-delivery)
2. Dealing with machines crashing via replication protocols
- copying the same data in several distinct physical locations
3. Dealing with lost computation via recomputation, e.g. in MapReduce

## Constant partial failure
Distributed systems hide their failures by design. This is the reason why distributed systems are so hard to debug.

How to debug?
- chaos engineering - create fails in production system on purpose to check how the system reacts