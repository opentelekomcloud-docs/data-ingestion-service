:original_name: dis_06_0017.html

.. _dis_06_0017:

Downloading Streaming Data
==========================

Sample Code
-----------

Use the initialized client instance to obtain data through the DIS stream. The sample code is available in the **ConsumerDemo.java** file under the **dis-sdk-demo\\src\\main\\java\\com\\bigdata\\dis\\sdk\\demo** directory.

The value of **streamName** must be the same as that of **Stream Name** configured in :ref:`Step 1: Creating a DIS Stream <dis_01_0601>`.

.. code-block::

   //Configure the stream name.
   String streamName = "streamName";
   // Configure the ID of the partition for data download.
   String partitionId = "0";
   //Configure the sequence number for data download.
   String startingSequenceNumber = "0";
   //Configure the data download mode.
   String cursorType = PartitionCursorTypeEnum.AT_SEQUENCE_NUMBER.name();
   try
   {
   //Obtain data cursors.
         GetPartitionCursorRequest request = new GetPartitionCursorRequest();
         request.setStreamName(streamName);
         request.setPartitionId(partitionId);
         request.setStartingSequenceNumber(startingSequenceNumber);
         request.setCursorType(cursorType);
         GetPartitionCursorResult response = dic.getPartitionCursor(request);
         String cursor = response.getPartitionCursor();
               log.info("Get stream {}[partitionId={}] cursor success : {}", streamName, partitionId, cursor);
               GetRecordsRequest recordsRequest = newGetRecordsRequest();
         GetRecordsResult recordResponse = null;
         while (true)
         {
             recordsRequest.setPartitionCursor(cursor);
             recordsRequest.setLimit(2);
             recordResponse = dic.getRecords(recordsRequest);
   //Obtain the next-batch data cursors.
             cursor = recordResponse.getNextPartitionCursor();
                       for (Record record : recordResponse.getRecords())
             {
                 log.info("Get Record [{}], partitionKey [{}], sequenceNumber [{}].",
                     new String(record.getData().array()),
                     record.getPartitionKey(),
                     record.getSequenceNumber());
             }
             Thread.sleep(1000);
         }
     }
   catch (DISClientException e)
   {
       log.error("Failed to get a normal response, please check params and retry. Error message [{}]", e.getMessage(), e);
   }
   catch (ResourceAccessException e)
   {
       log.error("Failed to access endpoint. Error message [{}]", e.getMessage(), e);
   }
   catch (Exception e)
   {
       log.error(e.getMessage(), e);
   }

Running the Program
-------------------

Right-click the program and choose **Run As > 1 Java Application** from the shortcut menu. If the program runs successfully, the information similar to the following is displayed on the console:

.. code-block::

   14:55:42.954 [main] INFOcom.bigdata.dis.sdk.DISConfig - get from classLoader
   14:55:44.103 [main] INFOcom.bigdata.dis.sdk.util.config.ConfigurationUtils - get from classLoader
   14:55:44.105 [main] INFOcom.bigdata.dis.sdk.util.config.ConfigurationUtils - propertyMapFromFile size : 2
   14:55:45.235 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get stream streamName[partitionId=0] cursor success : eyJnZXRJdGVyYXRvclBhcmFtIjp7InN0cmVhbS1uYW1lIjoiZGlzLTEzbW9uZXkiLCJwYXJ0aXRpb24taWQiOiIwIiwiY3Vyc29yLXR5cGUiOiJBVF9TRVFVRU5DRV9OVU1CRVIiLCJzdGFydGluZy1zZXF1ZW5jZS1udW1iZXIiOiIxMDY4OTcyIn0sImdlbmVyYXRlVGltZXN0YW1wIjoxNTEzNjY2NjMxMTYxfQ
   14:55:45.305 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get Record [hello world.], partitionKey [964885], sequenceNumber [0].
   14:55:45.305 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get Record [hello world.], partitionKey [910960], sequenceNumber [1].
   14:55:46.359 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get Record [hello world.], partitionKey [528377], sequenceNumber [2].
