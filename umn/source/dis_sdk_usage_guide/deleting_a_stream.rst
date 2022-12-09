:original_name: dis_06_0502.html

.. _dis_06_0502:

Deleting a Stream
=================

Initialize a DIS client instance named **dic**. For details, see :ref:`Initializing a DIS Client <dis_06_0015>`.

Use the DIS SDK to delete a specified DIS stream.

.. code-block::

   //Specify the name of the stream to be deleted.
   String streamName = "myStream";
   DeleteStreamRequest deleteStreamRequest = new DeleteStreamRequest();
   deleteStreamRequest.setStreamName(streamName);

After configuring **DeleteStreamRequest**, you can delete a stream by calling deleteStream.

.. code-block::

   dic.deleteStream(deleteStreamRequest);
