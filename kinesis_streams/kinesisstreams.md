### Kinesis Streams is used to :
![image](https://user-images.githubusercontent.com/52529498/140963179-d2cbd175-ef20-45ba-b558-a533abc3d5e6.png)

### Kinesis stream reads from : 
![image](https://user-images.githubusercontent.com/52529498/140964922-fb652512-8700-437c-9d69-27cd7b461a45.png)

- Streams are managed service automatially durable and resilient.
- Kinesis streams(KSs) has producer library and consumer library. 
- shards read from producer at 1 mb/s and write to consumer at 2 mb/s. Shard is the basic unit of work in KSs, you can increase the number of shards if the producer rate increases or vice versa.
- See above figure, producer could be a Amazon EC2 instance, mobile client, on premise servers, iot devices, etc. If volume of data increases in the stream we can increase the number of shards to upscale the stream. On the downstream side we have consumers - applications or lambda etc. If the data on the downstream side increase use the auto scaling group for the applications, lambda is a managed service so will autoscale as need be. Data in the stream is preserved for 24 hours by defualt and it can be increased upto 7 days. Each sharh ingests 1mb/s or 1000 records per second and emits 2mb/s
- Kinesis streams can be secured via server side encryption.Streams can be scled up or down and we only pay for shards allocated per hour
- Kinesis streams features
  - preserve client ordering, preserves the order as FIFO - first in first out
    - ![image](https://user-images.githubusercontent.com/52529498/141669323-a601dfc3-6282-4895-95d4-ed156295616e.png)
  - consume in parallel, Consumer A could be processing for logic A and Consumer B may be creating timeseries dataset
    -  ![image](https://user-images.githubusercontent.com/52529498/141673230-6ba341dd-9b7c-4300-8389-94cc9947d748.png)
  - decouple collection and processing
    - ![image](https://user-images.githubusercontent.com/52529498/141681469-6fa299bd-e3b2-4435-8211-68fb86c01853.png)


# Kinesis typical use case see diagram below:
-  all the use cases have in common is large number for small messages - single log message or single txn, from many sources ingested and stored and made available to many apps. Messages processed in real time, processed reliably, secure with server side encrytion and scalable. 
- ![image](https://user-images.githubusercontent.com/52529498/141680350-e660a089-e61c-4915-ad72-5765ad273ec2.png)

  


