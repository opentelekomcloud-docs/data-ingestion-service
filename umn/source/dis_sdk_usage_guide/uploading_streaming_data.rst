:original_name: dis_06_0016.html

.. _dis_06_0016:

Uploading Streaming Data
========================

Sample Code
-----------

Use the initialized client instance to upload your streaming data to DIS. The sample code is available in the **ProducerDemo.java** file in the **dis-sdk-demo\\src\\com\\bigdata\\dis\\sdk\\demo** directory.

The value of **streamName** must be the same as that of **Stream Name** configured in :ref:`Step 1: Creating a DIS Stream <dis_01_0601>`.

The code for uploading streaming data is as follows:

.. code-block::

   //Initialize an asynchronous sending client.
   DISConfig disConfig = new DISConfig().setAK("xxxx").setSK("xxxx").setProjectId("xxxx").setRegion("xxxx").setEndpoint("xxxx");
   DISProducer producer = new DISProducer(disConfig);

   //Configure the stream name.
   String streamName = "streamName";
   //Configure the data to be uploaded.
   String message = "hello world.";
   ByteBuffer buffer = ByteBuffer.wrap(message.getBytes());
   PutRecordsRequestEntry putRecordsRequestEntry = new PutRecordsRequestEntry();
   putRecordsRequestEntry.setData(buffer);
   putRecordsRequestEntry.setPartitionKey(String.valueOf(ThreadLocalRandom.current().nextInt(1000000)));
   log.info("========== BEGIN PUT ============");

   int count = 10;
   CountDownLatch cd = new CountDownLatch(count);
   for (int i = 0; i < count; i++)
   {
       putRecordsRequestEntry.setPartitionKey(String.valueOf(ThreadLocalRandom.current().nextInt(1000000)));
       try
       {
           producer.putRecordAsync(streamName, putRecordsRequestEntry, new AsyncHandler<PutRecordsResultEntry>()
           {
               @Override
               public void onSuccess(PutRecordsResultEntry result)
               {
                   log.info(result.toString());
                   cd.countDown();
               }

               @Override
               public void onError(Exception exception)
               {
                   log.error(exception.getMessage(), exception);
                   cd.countDown();
               }
           });
       }
       catch (Exception e)
       {
           log.error(e.getMessage(), e);
           cd.countDown();
       }
   }

   cd.await();
   log.info("========== PUT OVER ============");
   producer.close();

Running the Program
-------------------

Right-click the program and choose **Run As > 1 Java Application** from the shortcut menu. If the program runs successfully, the information similar to the following is displayed on the console:

.. code-block::

   17:27:49.130 [main] INFO  com.bigdata.dis.sdk.DISConfig - get from classLoader
   17:27:49.142 [Sender Thread] DEBUG com.bigdata.dis.sdk.producer.internals.Sender - Starting Kafka producer I/O thread.
   17:27:49.145 [main] INFO  DISProducerDemo - ========== BEGIN PUT ============
   17:27:49.202 [Sender Thread] DEBUG com.bigdata.dis.sdk.producer.internals.Sender - begin to send : 1
   17:27:49.203 [Sender Thread] DEBUG com.bigdata.dis.sdk.producer.internals.Sender - batch size: 10, 120
   17:27:50.197 [pool-2-thread-1] INFO  com.bigdata.dis.sdk.util.config.ConfigurationUtils - get from classLoader
   17:27:50.197 [pool-2-thread-1] INFO  com.bigdata.dis.sdk.util.config.ConfigurationUtils - propertyMapFromFile size : 2
   17:27:51.531 [pool-2-thread-1] DEBUG com.bigdata.dis.sdk.producer.internals.Sender - batches success. dis-alAR-nb, 10
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.532 [pool-2-thread-1] INFO  DISProducerDemo - PutRecordsResultEntry [partitionId=shardId-0000000000, sequenceNumber=76, errorCode=null, errorMessage=null]
   17:27:51.533 [main] INFO  DISProducerDemo - ========== PUT OVER ============
   17:27:51.571 [Sender Thread] DEBUG com.bigdata.dis.sdk.producer.internals.Sender - Beginning shutdown of Kafka producer I/O thread, sending remaining records.
