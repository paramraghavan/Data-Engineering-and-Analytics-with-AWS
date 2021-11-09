# Data-Engineering-and-Analytics-with-AWS
This is based on my experience working with AWS, resources available in AWS and my curious web searches.

## Architecting on AWS
When architecting our system we should separate *Compute* and *Storage*. We should use
- the open data formats like apache parquet, Avro, ORC. etc. I have mostly use [parquet](https://github.com/paramraghavan/Data-Engineering-and-Analysis-with-AWS/blob/main/parquet.md), but in some cses used csv as that was the consumers requirement.
- The data should not be replicated but shared across team, such that the same data is used by marketing team for sql query and s used by data scientist to run their model

## Lifecycle of data
![image](https://user-images.githubusercontent.com/52529498/140820594-4f8775e2-7506-4b1f-a98e-c3e547dc9e73.png)

## Data Source
- S3
- On premise database
- file system
- IOT devices
- etc

## Ingestion Layer
- AWS Custom Data Migration Service for on premise databases
- AWS Kinesis Kinesis Analytics for IOT devices, data streams. Kinesis Analytics - continuously reads and process streaming data in real time, (You write application code in a language supported by Apache Flink) to process the incoming streaming data and produce output. Then, Kinesis Data Analytics writes the output to a configured destination, in our case S3
- AWS Glue Crawler
- AWS Snowball - used for one time bulk transfer from on premise to S3
- Custom code - for example Java or python code which moves data from on premise to S3

## Storage
- S3

References:
- http://diagramo.com/editor/editor.php


