# Kinesis streams
## Kinesis Streams is used to :
![image](https://user-images.githubusercontent.com/52529498/140963179-d2cbd175-ef20-45ba-b558-a533abc3d5e6.png)

## Stream processing
means processing data in a stream—in other words, processing data that’s generated continuously, in small datasets (measured in kilobytes). You would use stream processing when you need real-time feedback or continuous insights. This kind of processing is performed on datasets like IoT sensor data, e-commerce purchases, in-game player activity, clickstreams, or information from social networks.
Many organizations use both types of processing, stream and batch, on the exact same dataset. Stream processing is used to get initial insights and real-time feedback, while batch processing is used to get deep insights from complex analytics. For example, credit card transactions. Have you ever received in text just moments after swiping your card? This is a streaming data fraud prevention alert. This is a stream process that happens in near-real time.

Now another process going on regularly using the same data would be the credit card company processing the days customer fraud prevention alert trends. Same data, two completely different business being met, two different velocities.


### Kinesis stream reads from : 
![image](https://user-images.githubusercontent.com/52529498/140964922-fb652512-8700-437c-9d69-27cd7b461a45.png)

- Streams are managed service automatially durable and resilient.
- Kinesis streams(KSs) has producer library and consumer library. 
- shards read from producer at 1 mb/s and write to consumer at 2 mb/s. Shard is the basic unit of work in KSs, you can increase the number of shards if the producer rate increases or vice versa.
- See above figure, producer could be a Amazon EC2 instance, mobile client, on premise servers, iot devices, etc. If volume of data increases in the stream we can increase the number of shards to upscale the stream. On the downstream side we have consumers - applications or lambda etc. If the data on the downstream side increase use the auto scaling group for the applications, lambda is a managed service so will autoscale as need be. Data in the stream is preserved for 24 hours by defaault and it can be increased upto 7 days. Each shard ingests 1mb/s or 1000 records per second and emits 2mb/s
- Kinesis streams can be secured via server side encryption.Streams can be scled up or down and we only pay for shards allocated per hour
- Kinesis streams features
  - preserve client ordering, preserves the order as FIFO - first in first out
    - ![image](https://user-images.githubusercontent.com/52529498/141669323-a601dfc3-6282-4895-95d4-ed156295616e.png)
  - consume in parallel, Consumer A could be processing for logic A and Consumer B may be creating timeseries dataset
    -  ![image](https://user-images.githubusercontent.com/52529498/141673230-6ba341dd-9b7c-4300-8389-94cc9947d748.png)
  - decouple collection and processing
    - ![image](https://user-images.githubusercontent.com/52529498/141681469-6fa299bd-e3b2-4435-8211-68fb86c01853.png)


## Kinesis typical use case see diagram below:
-  all the use cases have in common is large number for small messages - single log message or single txn, from many sources ingested and stored and made available to many apps. Messages processed in real time, processed reliably, secure with server side encrytion and scalable. 
- ![image](https://user-images.githubusercontent.com/52529498/141680350-e660a089-e61c-4915-ad72-5765ad273ec2.png)


# Kinesis Firehose
Amazon Kinesis Data Firehose is the easiest way to reliably load streaming data into data lakes, data stores, and analytics services. It can capture, transform, and deliver streaming data to Amazon S3, Amazon Redshift, etc.  <ul>It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration.</ul> It can also batch, compress, transform, and encrypt your data streams before loading, minimizing the amount of storage used and increasing security.

You can easily create a Firehose delivery stream from the AWS Management Console, configure it with a few clicks, and start ingesting streaming data from hundreds of thousands of data sources to your specified destinations. You can also configure your data streams to automatically convert the incoming data to open and standards based formats like Apache Parquet and Apache ORC before the data is delivered.

With Amazon Kinesis Data Firehose, there is no minimum fee or setup cost. You pay for the amount of data that you transmit through the service, if applicable, for converting data formats, and for Amazon VPC delivery and data transfer.
Each record can be as large as 1000Kb

![image](https://user-images.githubusercontent.com/52529498/141684424-1a57aa1e-0963-4f74-91d2-cd0052759aed.png)

![image](https://user-images.githubusercontent.com/52529498/141689084-2a75d375-4392-46d0-b768-8003218d1df1.png)

## How does it work
![image](https://user-images.githubusercontent.com/52529498/141689117-11fd8f91-816d-466e-8acf-97a7b85d7054.png)

## Data tranformation with firehose, lambda transforms the data
![image](https://user-images.githubusercontent.com/52529498/141689188-a9772d79-47d9-46a7-a328-314b4a1207f2.png)

![image](https://user-images.githubusercontent.com/52529498/141689418-d584104a-5114-4159-8b82-f100140e80a9.png)


# Kinesis Analytics
Amazon Kinesis is Amazon's real‑time data streaming service. Amazon Kinesis enables you to collect, process, and analyze streaming data in real time instead of having to wait until all your data is collected before the processing can begin. With Kinesis, you can ingest real‑time data such as application logs, web clickstreams, IoT telemetry data, and more right into your database, data lakes, and data warehouses, or build your own real‑time applications using this data to gain insight into your information. With Kinesis, you can ingest real‑time data such as application logs, web clickstreams, IoT telemetry data, and more right into your database, data lakes, and data warehouses, or build your own real‑time applications using this data to gain insight into your information

Amazon Kinesis Analytics processes and analyzes streaming data in real time with standard SQL without having to learn new programming languages or processing frameworks. Kinesis Analytics enables you to query streaming data or build entire streaming applications with SQL. 

The results can be used to create insights and visualizations so that you can respond to your business and customer needs promptly. Notifications and alerts can also be configured. This service supports ingesting data from Amazon Kinesis Streams and Amazon Kinesis Firehose streaming sources.

To get started with Kinesis Analytics, you'll first need to log in to the AWS Management Console and select Kinesis Stream or Kinesis Firehose delivery stream as an input. Amazon Kinesis Analytics continuously polls the streaming source for new data and ingests it using in‑application streams. Next, write your SQL queries to process the streaming data using your Kinesis Analytics SQL editor and built‑in templates, and test it with live streaming data.
Kinesis Analytics is able to send processed results to Amazon Simple Storage Service, or S3, Amazon Redshift, Amazon Elasticsearch Service, or your own custom destination for further analysis

![image](https://user-images.githubusercontent.com/52529498/141690095-9561bf76-3c14-4aa3-a513-7d0e31591c79.png)

![image](https://user-images.githubusercontent.com/52529498/141690191-f65a22aa-1a4f-4122-9a75-e9efbe077274.png)

ref: https://www.serverless.com/examples/kinesis-streams-fan-out-kinesis-analytics

## Realtime log analytics
![image](https://user-images.githubusercontent.com/52529498/141690448-2c2a159b-2f34-4070-9ca3-44eeba1a753e.png)

## IOT use case
![image](https://user-images.githubusercontent.com/52529498/141690547-e19efcba-6c09-400b-bea3-e5ad55843820.png)

 You can use Kinesis Analytics to transform, aggregate, and filter streaming data from IoT devices such as consumer appliances, embedded sensors, and TV set top boxes. You could then use the data to send real‑time alerts when a sensor exceeds certain operating thresholds. Kinesis Streams collects and streams the data to Kinesis Analytics in real time, which then filters aggregates, and enriches the data. Processed results are then transmitted to Amazon DynamoDB, which in turn powers customer dashboards and sends alerts in real time

Kinesis Analytics enables you to quickly author SQL code that continuously reads, processes, and stores data in real time. It can be used to generate time‑series analytics and calculate metrics over time windows and then stream values to a destination. Kinesis Analytics can also send aggregated and processed streaming data results downstream to feed real‑time dashboards.

ref: https://aws.amazon.com/kinesis/data-firehose/?kinesis-blogs.sort-by=item.additionalFields.createdDate&kinesis-blogs.sort-order=desc

  


