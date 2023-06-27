:original_name: DeleteCheckpoint.html

.. _DeleteCheckpoint:

Deleting Checkpoints
====================

Function
--------

This API is used to delete checkpoints.

URI
---

DELETE /v2/{project_id}/checkpoints

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================+
   | stream_name     | Yes             | String          | Name of the stream to which the checkpoint belongs.                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_name        | Yes             | String          | Name of the application associated with the checkpoint.                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Maximum: **50**                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | checkpoint_type | Yes             | String          | Type of the checkpoint                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  **LAST_READ**: Only sequence numbers are recorded in databases.                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Enumeration values:                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  **LAST_READ**                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_id    | No              | String          | Identifier of the stream partition to which the checkpoint belongs. The value can be in either of the following formats:- shardId-0000000000- 0                            |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | For example, if a stream has three partitions, the partition identifiers are 0, 1, and 2, or shardId-0000000000, shardId-0000000001, and shardId-0000000002, respectively. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                          |
   |                 |                 |                 | The token can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Deleting Checkpoints

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/checkpoints

Example Responses
-----------------

None

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
