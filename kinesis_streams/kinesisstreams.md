### Kinesis Streams is used to :
![image](https://user-images.githubusercontent.com/52529498/140963179-d2cbd175-ef20-45ba-b558-a533abc3d5e6.png)

### Kinesis stream reads from : 
![image](https://user-images.githubusercontent.com/52529498/140964922-fb652512-8700-437c-9d69-27cd7b461a45.png)

- Streams are managed service automatially durable and resilient.
- Kinesis streams(KSs) has producer library and consumer library. 
- shards read from producer at 1 mb/s and write to consumer at 2 mb/s. Shard is the basic unit of work in KSs, you can increase the number of shards if the producer rate increases or vice versa.
- See above figure, producer could be a Amazon EC2 instance, mobile client, on premise servers, iot devices, etc. If volume of data increases in the stream we can increase the number of shards to upscale the stream. On the downstream side we have consumers - applications or lambda etc. If the data on the downstream side increase use the auto scaling group for the applications, lambda is a managed service so will autoscale as need be. Data in the stream is preserved for 24 hours by defualt and it can be increased upto 7 days.
- Kinesis streams can be secured via server side encryption.Streams can be scled up or down and we only pay for shards allocated per hour
- Kinesis streams
  - preserve client ordering
  - consume in parallel
  - decouple collection and processing



