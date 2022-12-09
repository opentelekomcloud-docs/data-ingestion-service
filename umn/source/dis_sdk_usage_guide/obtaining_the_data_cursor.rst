:original_name: dis_06_0505.html

.. _dis_06_0505:

Obtaining the Data Cursor
=========================

Initialize a DIS client instance named **dic**. For details, see :ref:`Initializing a DIS Client <dis_06_0015>`.

Use the DIS SDK to obtain the information about the data cursor.

.. code-block::

   //Configure the stream name.
   String streamName = "myStream";
   // Configure the ID of the partition for data download.
   String partitionId = "0";
   //Configure the sequence number for data download.
   String startingSequenceNumber = "0";
   //Configure the data download mode.
   String cursorType = PartitionCursorTypeEnum.AT_SEQUENCE_NUMBER.name();

   GetPartitionCursorRequest request = new GetPartitionCursorRequest();
   request.setStreamName(streamName);
   request.setPartitionId(partitionId);
   request.setStartingSequenceNumber(startingSequenceNumber);
   request.setCursorType(cursorType);
   GetPartitionCursorResult response = dic.getPartitionCursor(request);
   String cursor = response.getPartitionCursor();
