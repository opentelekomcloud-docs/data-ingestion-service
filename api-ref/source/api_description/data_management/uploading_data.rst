:original_name: dis_02_0018.html

.. _dis_02_0018:

Uploading Data
==============

Function
--------

This API is used to upload data to DIS streams.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

POST /v2/{project_id}/records

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                         | Description                                                                                                        |
   +=================+=================+==============================================================================================+====================================================================================================================+
   | stream_name     | Yes             | String                                                                                       | Name of the stream                                                                                                 |
   |                 |                 |                                                                                              |                                                                                                                    |
   |                 |                 |                                                                                              | Maximum: **60**                                                                                                    |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | stream_id       | No              | String                                                                                       | Unique ID of the stream.                                                                                           |
   |                 |                 |                                                                                              |                                                                                                                    |
   |                 |                 |                                                                                              | If no stream is found based on stream_name and stream_id is not empty, stream_id is used to search for the stream. |
   |                 |                 |                                                                                              |                                                                                                                    |
   |                 |                 |                                                                                              | Note:                                                                                                              |
   |                 |                 |                                                                                              |                                                                                                                    |
   |                 |                 |                                                                                              | This parameter is mandatory when you upload data to a stream that has been authorized.                             |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | records         | Yes             | Array of :ref:`PutRecordsRequestEntry <dis_02_0018__request_putrecordsrequestentry>` objects | List of records to be uploaded                                                                                     |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _dis_02_0018__request_putrecordsrequestentry:

.. table:: **Table 4** PutRecordsRequestEntry

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                   |
   +===================+=================+=================+===============================================================================================================================================================================================================================================================================+
   | data              | Yes             | String          | Data to be uploaded.                                                                                                                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                                                                                               |
   |                   |                 |                 | The uploaded data is the serialized binary data (character string encoded using Base64).                                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                                                                               |
   |                   |                 |                 | For example, if the character string data needs to be uploaded, the character string after Base64 encoding is **ZGF0YQ==**.                                                                                                                                                   |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | explicit_hash_key | No              | String          | Hash value of the data to be written to the partition. The hash value overwrites the hash value of **partition_key**.                                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                                                                                               |
   |                   |                 |                 | Value range: 0 to long.max                                                                                                                                                                                                                                                    |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_id      | No              | String          | Partition identifier of the stream.Two partition ID formats are available:- shardId-0000000000- 0For example, if a stream has three partitions, the partition IDs are **0**, **1**, and **2**, or **shardId-0000000000**, **shardId-0000000001**, and **shardId-0000000002**. |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_key     | No              | String          | Partition to which data is written to.Note:If **partition_id** is transferred, it is preferentially used. If it is not transferred, **partition_key** is used.                                                                                                                |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +---------------------+---------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Parameter           | Type                                                                                        | Description                                     |
   +=====================+=============================================================================================+=================================================+
   | failed_record_count | Integer                                                                                     | Number of data records that fail to be uploaded |
   +---------------------+---------------------------------------------------------------------------------------------+-------------------------------------------------+
   | records             | Array of :ref:`PutRecordsResultEntry <dis_02_0018__response_putrecordsresultentry>` objects | List of upload results                          |
   +---------------------+---------------------------------------------------------------------------------------------+-------------------------------------------------+

.. _dis_02_0018__response_putrecordsresultentry:

.. table:: **Table 6** PutRecordsResultEntry

   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                           |
   +=================+========+=======================================================================================================================================================================================================================================================================================================================================================================================================+
   | partition_id    | String | ID of the partition to which data is uploaded                                                                                                                                                                                                                                                                                                                                                         |
   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence_number | String | Sequence number of the data to be uploaded. A sequence number is the unique identifier of each record. DIS automatically allocates a sequence number when the data producer calls the PutRecords operation to add data to the DIS stream. The sequence number of the same partition key usually changes with time. A longer interval between PutRecords requests results in a larger sequence number. |
   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code      | String | Error code                                                                                                                                                                                                                                                                                                                                                                                            |
   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message   | String | Error message                                                                                                                                                                                                                                                                                                                                                                                         |
   +-----------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Uploading Data

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/records

   {
     "stream_name" : "newstream",
     "records" : [ {
       "data" : "MTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTE="
     } ]
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ===============
Status Code Description
=========== ===============
200         Normal response
=========== ===============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
