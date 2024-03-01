#### First Click Attribution Project
* Designing + building a streaming pipeline by creating a first click attribution pipeline for an e-commerce website
* Using Apache Flink and Apache Kafka for stream processing and queuing
* e-commerce can be used to identify, for every purchased product, the click that led to this purchase
* Attribution is the joining of checkout/purchase of a product to a click

#### Objectives
1. Enrich checkout data with the username
   * User data is in a transactional database
2. Identify which click leads to a checkout (attribution)
   * for every product checkout, we consider the earliest click a user made on that product in the last hour to be the click that led to a checkout/purchase
3. Log the checkouts and their corresponding attributed clicks (if any) into a table
   * using Apache Table API to define source systems: clicks, checkouts, and users
   * defining source systems: clicks, checkouts, and users
   * using python script to generate fake click and checkout data
   * define how to process the data (enrich + attribute)
   * enriching with user data and attributing checkouts

#### Streaming Pipeline Architecture
1. Application
   * Website generates clicks and checkout event data
2. Queue
   * The clicks and checkout data are sent to their corresponding Kafka topics
3. Stream processing:
   * Flink reads data from the Kafka topics
   * The click data is stored in our cluster state
   * Only storing click information for last hour + only storing 1 click per user-product combination
   * The checkout data is enriched with user information by querying the user table in Postgres
   * The checkout data is left joined with the click data( in the cluster state) to see if the checkout can be attributed to a click
   * The enriched and attributed checkout data is logged into a Postgres sink table
4. Monitoring & Alerting
   * Apache Flink metrics are pulled by Prometheus and visualized using Graphana
