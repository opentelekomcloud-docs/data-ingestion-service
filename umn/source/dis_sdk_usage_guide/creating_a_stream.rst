:original_name: dis_06_0501.html

.. _dis_06_0501:

Creating a Stream
=================

Initialize a DIS client instance named **dic**. For details, see :ref:`Initializing a DIS Client <dis_06_0015>`.

When you use the DIS SDK to create a DIS stream, specify the stream name, number of partitions in the stream and stream type.

**STREAM_TYPE_COMMON** indicates a common stream, and **STREAM_TYPE_ADVANCED** indicates an advanced stream.

.. code-block::

   //Configure the channel name.
   String streamName = "myStream";
   //Configure the number of partitions in the stream.
   Integer partitionCount = new Integer(3);
   CreateStreamRequest createStreamRequest = new CreateStreamRequest();
   createStreamRequest.setStreamName(streamName);
   createStreamRequest.setPartitionCount(partitionCount);
   //Configure the stream type.
   createStreamRequest.setStreamType(CreateStreamRequest.STREAM_TYPE_COMMON);

After configuring **CreateStreamRequest**, you can create a stream by calling **createStream**.

.. code-block::

   dic.createStream(createStreamRequest);
