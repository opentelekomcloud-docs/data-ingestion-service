:original_name: dis_06_0503.html

.. _dis_06_0503:

Querying a Stream List
======================

Initialize a DIS client instance named **dic**. For details, see :ref:`Initializing a DIS Client <dis_06_0015>`.

Use the DIS SDK to list active streams.

Use the **setLimit** method to set the number of streams returned each time. If **setLimit** is not specified, a maximum of 10 streams are returned by default.

.. code-block::

   ListStreamsRequest listStreamsRequest = new ListStreamsRequest();
   listStreamsRequest.setLimit(5);
   System.out.println("listStream: " + JsonUtils.objToJson(dic.listStreams(listStreamsRequest)));

The returned stream list is as follows:

.. code-block::

   listStream: {"total_number":20,"stream_names":["Stream0","Stream1","Stream2","Stream3","Stream4"],"has_more_streams":true}
