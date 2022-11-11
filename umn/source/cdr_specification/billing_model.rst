:original_name: dis_01_0223.html

.. _dis_01_0223:

Billing Model
=============

Data Ingestion Service (DIS) is charged for resource usage, there are three main billing factors: the duration of Partition and PUT Payload Unit number.

-  General partition contains duration, PUT Payload Unit number, Data storage size billing factor. Advanced partition contains duration billing factor.
-  The duration of Partition: Partition is the base capacity unit of DIS. There are two types of partition: General partition and advanced partition. The general partition provides a capacity of 1MB/sec data input , 2MB/sec data outputand support up to 1000 records put per second. The advanced partition provides a capacity of 5MB/sec data input ,10MB/sec data output and support up to 2000 records put per second .You specify the number of partitions when create the stream based on the throughput requirements. You are charged for each partition at an hourly rate.
-  PUT Payload Unit number: A record is the data that your data producer adds to DIS stream. A PUT Payload Unit is counted in 25KB payload "chunks" that comprise a record. For example, a 5KB record contains one PUT Payload Unit, a 45KB record contains two PUT Payload Units, and a 1000KB record contains 40 PUT Payload Units. PUT Payload Unit is charged with a per million PUT Payload Units rate.
-  Data storage size: the data storage size in DIS input from the partition. The Customer can specify stream data storage time: from One day to Seven days when create the stream. If the data storage time exceeds the specified time, the data will be automatically aged. In general, the data storage one day is free, it means that 84GB of storage space for each partition is free to use. Of course, the final free space size can be specified according to the actual situation.

DIS is charged for resource usage as follow:

-  One Partition Costs = partition time \* partition rate + Payload Unit Num \* Payload Unit Rate + Data storage size \* storage size rate
-  Total Costs per stream = Partition 1 Cost + Partition 2 Cost + … + Partition n Cost

Both resources will be charged at the same time. Each charged will be listed separately. There will be 3 CDR records for each stream in the billing interval.

The data will be cached for some time in the service, and default cache time is 24 hours. If the user want dump the data to OBS, the operation in OBS will be charged separately.

Example:

Let us assume that our data producers put 50 records per second in aggregate, and each record is 35KB. In this case, the total data input rate is 1.7MB/sec (50 records/sec*35KB/record). For simplicity, we assume that the throughput and data size of each record are stable and constant throughout the day.

We first calculate the number of partitions needed for our stream to achieve the required throughput. As one partition provides a capacity of 1MB/sec data input and supports 1000 records/sec, two partitions provide a capacity of 2MB/sec data input and support 2000 records/sec. So a stream with two partitions satisfies our required throughput of 1.7MB/sec at 50 records/sec.

We then calculate our costs using DIS pricing:

-  Partition Hour: One Partition costs $X per hour. Our stream has two partitions so that it costs $2X per hour.
-  PUT Payload Unit (25KB): The 1 million Payload Unit costs $Y. As our record is 35KB, each record contains two PUT Payload Units. Our data producers put 50 records or 100 PUT Payload Units per second in aggregate. That is 180000 records or 360000 PUT Payload Units per hour.so it costs 0.36*Y per hour.

If the data in the DIS stored 1 day, the Data storage size is always less than 84GB, so the total cost per hour is :$(2X + Y)

Optionally, we can choose to increase the data retention period of our stream from 24 hours to up to 7 days. In this example, if the throughput is stable, the data storage size is 514.08GB per partition(0.85MB/sec \* 3600sec \* 24hour \* 7day).We assume that the data storage rate is $Z per GB*Hour, the cost is $860.16*Z( the detail is (514.08-84)GB \* 2 partitions \* Z). The total cost should $(2*X + Y + 860.16*Z).

**Shard Hour**

Shard is the base throughput unit of an Amazon Kinesis stream. One shard provides a capacity of 1MB/sec data input and 2MB/sec data output. One shard can support up to 1000 records per second. You specify the number of shards needed within your stream based on your throughput requirements. You are charged for each shard at an hourly rate.

**PUT Payload Unit (25KB)**

A record is the data that your data producer adds to your Amazon Kinesis stream. A PUT Payload Unit is counted in 25KB payload "chunks" that comprise a record. For example, a 5KB record contains one PUT Payload Unit, a 45KB record contains two PUT Payload Units, and a 1MB record contains 40 PUT Payload Units. PUT Payload Unit is charged with a per million PUT Payload Units rate.

**Extended Data Retention (Up to 7 days)**

Amazon Kinesis stores your data for 24 hours by default. You can choose to increase the data retention period of your stream to up to 7 days. You are charged for an additional rate on each shard hour incurred by your stream once you enable extended data retention.

-  Getting records from Amazon Kinesis stream is free.
-  Data transfer is free. AWS does not charge for data transfer from your data producers to Amazon Kinesis Streams, or from Amazon Kinesis Streams to your Amazon Kinesis Applications.
