:original_name: UpdatePartitionCount.html

.. _UpdatePartitionCount:

Changing Partition Quantity
===========================

Function
--------

This API is used to change the number of partitions in a specific stream.

URI
---

PUT /v2/{project_id}/streams/{stream_name}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                      |
   +=================+=================+=================+==================================================================+
   | project_id      | Yes             | String          | Project ID.                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | stream_name     | Yes             | String          | Name of the stream whose partition quantity needs to be changed. |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | Maximum: **64**                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                          |
   |                 |                 |                 | The token can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                                                                                                                                                |
   +========================+=================+=================+============================================================================================================================================================================+
   | stream_name            | Yes             | String          | Name of the stream whose partition quantity needs to be changed.                                                                                                           |
   |                        |                 |                 |                                                                                                                                                                            |
   |                        |                 |                 | Maximum: **64**                                                                                                                                                            |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | target_partition_count | Yes             | Integer         | Number of the target partitions                                                                                                                                            |
   |                        |                 |                 |                                                                                                                                                                            |
   |                        |                 |                 | The value is an integer greater than 0.                                                                                                                                    |
   |                        |                 |                 |                                                                                                                                                                            |
   |                        |                 |                 | If the value is greater than the number of current partitions, scaling-up is required. If the value is less than the number of current partitions, scale-down is required. |
   |                        |                 |                 |                                                                                                                                                                            |
   |                        |                 |                 | Note:                                                                                                                                                                      |
   |                        |                 |                 |                                                                                                                                                                            |
   |                        |                 |                 | Each stream can be scaled up and down for five times within one hour. After a stream is scaled up or down, it cannot be scaled up or down again in the next one hour.      |
   |                        |                 |                 |                                                                                                                                                                            |
   |                        |                 |                 | Minimum: **0**                                                                                                                                                             |
   +------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Changing Partition Quantity

.. code-block:: text

   PUT https://{Endpoint}/v2/{project_id}/streams/{stream_name}

   {
     "stream_name" : "newstream",
     "target_partition_count" : 5
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ================
Status Code Description
=========== ================
200         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
