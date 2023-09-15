:original_name: dis_01_0603.html

.. _dis_01_0603:

Step 3: Sending Data to DIS
===========================

Function
--------

Local data is continuously uploaded to DIS.

.. note::

   Data can be stored in DIS, OBS, and DLI. For how to configure a storage location, see :ref:`Creating a Dump Task <dis_01_0047>`.

   The maximum number of days for DIS to preserve data cannot exceed **Data Retention (days)**.

Sample Code
-----------

The example code file is the **ProducerDemo.java** file in the **\\dis-sdk-demo\\src\\main\\java\\com\\bigdata\\dis\\sdk\\demo** directory decompressed from the **dis-sdk-1.2.3.zip** package. The compression package is downloaded from the `DIS SDK <https://dis-publish.obs-website.cn-north-1.myhuaweicloud.com/>`__.

Running the Producer Program
----------------------------

Right-click the producer application and choose **Run As** > **1 Java Application** from the shortcut menu.


.. figure:: /_static/images/en-us_image_0068150349.png
   :alt: **Figure 1** Running a producer application

   **Figure 1** Running a producer application

While data is being sent to DIS, the DIS console displays DIS stream information. If information similar to the following is displayed, the data has been successfully sent to DIS:

.. code-block::

   14:40:20.090 [main] INFOcom.bigdata.dis.sdk.DISConfig - get from classLoader
   14:40:20.093 [main] INFODEMOT - ========== BEGIN PUT ============
   14:40:21.186 [main] INFOcom.bigdata.dis.sdk.util.config.ConfigurationUtils - get from classLoader
   14:40:21.187 [main] INFOcom.bigdata.dis.sdk.util.config.ConfigurationUtils - propertyMapFromFile size : 2
   14:40:22.092 [main] INFOcom.bigdata.dis.sdk.demo.ProducerDemo - Put 3 records[3 successful / 0 failed].
   14:40:22.092 [main] INFOcom.bigdata.dis.sdk.demo.ProducerDemo - [hello world.] put success, partitionId [shardId-0000000000], partitionKey [964885], sequenceNumber [0]
   14:40:22.092 [main] INFOcom.bigdata.dis.sdk.demo.ProducerDemo - [hello world.] put success, partitionId [shardId-0000000000], partitionKey [910960], sequenceNumber [1]
   14:40:22.092 [main] INFOcom.bigdata.dis.sdk.demo.ProducerDemo - [hello world.] put success, partitionId [shardId-0000000000], partitionKey [528377], sequenceNumber [2]
   14:40:22.092 [main] INFOcom.bigdata.dis.sdk.demo.ProducerDemo - ========== PUT OVER ============
