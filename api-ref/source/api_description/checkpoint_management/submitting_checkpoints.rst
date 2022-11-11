:original_name: dis_02_0403.html

.. _dis_02_0403:

Submitting Checkpoints
======================

Function
--------

This API is used to submit checkpoints.

URI
---

POST /v2/{project_id}/checkpoints

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                         |
   +=================+=================+=================+=====================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                         |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | The token can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================+
   | app_name        | Yes             | String          | Name of the app, which is the unique identifier of a user data consumption program.                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | checkpoint_type | Yes             | String          | Type of the checkpoint.                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  LAST_READ: Only sequence numbers are recorded in databases.                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Enumeration values:                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  **LAST_READ**                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | stream_name     | Yes             | String          | Name of the stream.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_id    | Yes             | String          | Partition identifier of the stream. The value can be in either of the following formats:                                                                                   |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  shardId-0000000000                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  0                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | For example, if a stream has three partitions, the partition identifiers are 0, 1, and 2, or shardId-0000000000, shardId-0000000001, and shardId-0000000002, respectively. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence_number | Yes             | String          | Sequence number to be submitted, which is used to record the consumption checkpoint of the stream. Ensure that the sequence number is within the valid range.              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | No              | String          | Metadata information of the consumer application.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | The metadata information can contain a maximum of 1,000 characters.                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Maximum: **1000**                                                                                                                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Submitting Checkpoints

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/checkpoints

   {
     "stream_name" : "newstream",
     "app_name" : "newapp",
     "partition_id" : "0",
     "sequence_number" : "2",
     "checkpoint_type" : "LAST_READ"
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ================
Status Code Description
=========== ================
201         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
