:original_name: ShowCheckpoint.html

.. _ShowCheckpoint:

Querying Checkpoint Details
===========================

Function
--------

This API is used to query checkpoint details.

URI
---

GET /v2/{project_id}/checkpoints

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================+
   | stream_name     | Yes             | String          | Name of the stream to which the checkpoint belongs.                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_id    | Yes             | String          | Identifier of the stream partition to which the checkpoint belongs. The value can be in either of the following formats:                                                   |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  shardId-0000000000                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  0                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | For example, if a stream has three partitions, the partition identifiers are 0, 1, and 2, or shardId-0000000000, shardId-0000000001, and shardId-0000000002, respectively. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_name        | Yes             | String          | Name of the app associated with the checkpoint.                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | checkpoint_type | Yes             | String          | Type of the checkpoint.                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  LAST_READ: Only sequence numbers are recorded in databases.                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Enumeration values:                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  **LAST_READ**                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                         |
   +=================+=================+=================+=====================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                         |
   |                 |                 |                 |                                                                                                     |
   |                 |                 |                 | The token can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

.. table:: **Table 4** Response body parameters

   +-----------------+--------+--------------------------------------------------------------------------+
   | Parameter       | Type   | Description                                                              |
   +=================+========+==========================================================================+
   | sequence_number | String | Sequence number used to record the consumption checkpoint of the stream. |
   +-----------------+--------+--------------------------------------------------------------------------+
   | metadata        | String | Metadata information of the consumer application.                        |
   +-----------------+--------+--------------------------------------------------------------------------+

Example Requests
----------------

Querying Checkpoint Details

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/checkpoints

Example Responses
-----------------

**Status code: 204**

Normal response.

.. code-block::

   {
     "sequence_number" : "newstram",
     "metadata" : ""
   }

Status Codes
------------

=========== ================
Status Code Description
=========== ================
204         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
