:original_name: dis_06_0504.html

.. _dis_06_0504:

Querying Stream Details
=======================

Initialize a DIS client instance named **dic**. For details, see :ref:`Initializing a DIS Client <dis_06_0015>`.

Use the DIS SDK to query the details about a specified stream.

.. code-block::

   String streamName = "myStream";
   DescribeStreamRequest describeStreamRequest = new DescribeStreamRequest();
   describeStreamRequest.setStreamName(streamName);
   System.out.println("descStream: " + JsonUtils.objToJson(dic.describeStream(describeStreamRequest)));

The returned stream details are as follows:

.. code-block::

   descStream: {"stream_name":"myStream","create_time":1515140868451,"last_modified_time":1515140868451,"retention_period":24,"status":"RUNNING","stream_type":"ADVANCED","partitions":[{"status":"ACTIVE","partition_id":"shardId-0000000000","hash_range":"[0 : 4611686018427387902]","sequence_number_range":"[0 : 0]"},{"status":"ACTIVE","partition_id":"shardId-0000000001","hash_range":"[4611686018427387903 : 9223372036854775807]","sequence_number_range":"[0 : 0]"}],"has_more_partitions":false}
