:original_name: dis_01_0604.html

.. _dis_01_0604:

Step 4: Obtaining Data from DIS
===============================

Function
--------

You can retrieve data from DIS when needed.

Sample Code
-----------

The example code file is the **ConsumerDemo.java** file in the **\\dis-sdk-demo\\src\\main\\java\\com\\bigdata\\dis\\sdk\\demo** directory decompressed from the **dis-sdk-XXX.zip** package. The compression package is downloaded from the `DIS SDK <https://dis-publish.obs-website.cn-north-1.myhuaweicloud.com/>`__.

Running the Consumer Application
--------------------------------

If information similar to the following appears, data has been successfully retrieved from DIS:

.. code-block::

   14:55:42.954 [main] INFOcom.bigdata.dis.sdk.DISConfig - get from classLoader
   14:55:44.103 [main] INFOcom.bigdata.dis.sdk.util.config.ConfigurationUtils - get from classLoader
   14:55:44.105 [main] INFOcom.bigdata.dis.sdk.util.config.ConfigurationUtils - propertyMapFromFile size : 2
   14:55:45.235 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get stream streamName[partitionId=0] cursor success : eyJnZXRJdGVyYXRvclBhcmFtIjp7InN0cmVhbS1uYW1lIjoiZGlzLTEzbW9uZXkiLCJwYXJ0aXRpb24taWQiOiIwIiwiY3Vyc29yLXR5cGUiOiJBVF9TRVFVRU5DRV9OVU1CRVIiLCJzdGFydGluZy1zZXF1ZW5jZS1udW1iZXIiOiIxMDY4OTcyIn0sImdlbmVyYXRlVGltZXN0YW1wIjoxNTEzNjY2NjMxMTYxfQ
   14:55:45.305 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get Record [hello world.], partitionKey [964885], sequenceNumber [0].
   14:55:45.305 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get Record [hello world.], partitionKey [910960], sequenceNumber [1].
   14:55:46.359 [main] INFOcom.bigdata.dis.sdk.demo.ConsumerDemo - Get Record [hello world.], partitionKey [528377], sequenceNumber [2].
