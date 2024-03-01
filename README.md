# First Click Attribution Project
* Designing + building a streaming pipeline by creating a first click attribution pipeline for an e-commerce website
* Using Apache Flink and Apache Kafka for stream processing and queuing
* e-commerce can be used to identify, for every purchased product, the click that led to this purchase
* Attribution is the joining of checkout/purchase of a product to a click


# Objectives:
1. Enrich checkout data with the username
   * User data is in a transactional database
2. Identify which click leads to a checkout (attribution)
   * for every product checkout, we consider the earliest click a user made on that product in the last hour to be the click that led to a checkout/purchase
3. Log the checkouts and their corresponding attributed clicks (if any) into a table
