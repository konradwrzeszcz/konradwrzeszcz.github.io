## Services or online systems
Wait for requests from clients and try to handle them quickly
(e.g. key-value store, web server, database, cache)

## Batch processing systems or offline systems
e.g MapReduce and its successors

### Raw data
Authoritative version

### Dervied data
Result of taking existing data and transforming/procesing it. MapReduce is a tool for computing derived data.

## MapReduce, how does it work?

![alt_text](images/inverted_index.png "image_tooltip")

Index - words in documents <Document -> Words>

Inverted index - documents which contain words <Word -> Documents>

Embarassingly parallel - every iteration in foreach is completely independent, it's really easy to do it parallel

### Parallel inverted index

![alt_text](images/intermediate_key_value_pairs.png "image_tooltip")

![alt_text](images/replicas.png "image_tooltip")

Shuffle communication pattern

![alt_text](images/shuffle_communication_pattern.png "image_tooltip")
