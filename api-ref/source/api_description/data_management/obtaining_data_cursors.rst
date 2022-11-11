:original_name: dis_02_0020.html

.. _dis_02_0020:

Obtaining Data Cursors
======================

Function
--------

This API is used to obtain data cursors.

URI
---

GET /v2/{project_id}/cursors

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                              |
   +==========================+=================+=================+==========================================================================================================================================================================================================================================================================================================================================================+
   | stream-name              | Yes             | String          | Name of the stream.                                                                                                                                                                                                                                                                                                                                      |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition-id             | Yes             | String          | Partition ID of the stream. The value can be in either of the following formats:                                                                                                                                                                                                                                                                         |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  shardId-0000000000                                                                                                                                                                                                                                                                                                                                    |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  0                                                                                                                                                                                                                                                                                                                                                     |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | For example, if a stream has three partitions, the partition identifiers are 0, 1, and 2, or shardId-0000000000, shardId-0000000001, and shardId-0000000002, respectively.                                                                                                                                                                               |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cursor-type              | No              | String          | Cursor type.                                                                                                                                                                                                                                                                                                                                             |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  AT_SEQUENCE_NUMBER: Data is read from the position denoted by a specific sequence number (that is defined by starting-sequence-number). This is the default cursor type.                                                                                                                                                                              |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  AFTER_SEQUENCE_NUMBER: Data is read right after the position denoted by a specific sequence number (that is defined by starting-sequence-number).                                                                                                                                                                                                     |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  TRIM_HORIZON: Data is read from the earliest data record in the partition. For example, a tenant uses a DIS stream to upload three pieces of data A1, A2, and A3. N days later, A1 has expired and A2 and A3 are still in the validity period. In this case, if the tenant uses TRIM_HORIZON to download the data, the system downloads data from A2. |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  LATEST: Data is read from the latest record in the partition. This setting ensures that you always read the latest record in the partition.                                                                                                                                                                                                           |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  AT_TIMESTAMP: Data is read from the position denoted by a specific timestamp.                                                                                                                                                                                                                                                                         |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | Enumeration values:                                                                                                                                                                                                                                                                                                                                      |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  **AT_SEQUENCE_NUMBER**                                                                                                                                                                                                                                                                                                                                |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  **AFTER_SEQUENCE_NUMBER**                                                                                                                                                                                                                                                                                                                             |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  **TRIM_HORIZON**                                                                                                                                                                                                                                                                                                                                      |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  **LATEST**                                                                                                                                                                                                                                                                                                                                            |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | -  **AT_TIMESTAMP**                                                                                                                                                                                                                                                                                                                                      |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | starting-sequence-number | No              | String          | Serial number. A sequence number is a unique identifier for each record. DIS automatically allocates a sequence number when the data producer calls the PutRecords operation to add data to the DIS stream. SN of the same partition key usually changes with time. A longer interval between PutRecords requests results in a larger sequence number.   |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | The sequence number is closely related to cursor types AT_SEQUENCE_NUMBER and AFTER_SEQUENCE_NUMBER. The two parameters determine the position of the data to be read.                                                                                                                                                                                   |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | Value range: 0 to 9,223,372,036,854,775,807                                                                                                                                                                                                                                                                                                              |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp                | No              | Long            | Timestamp when the data record starts to be read, which is closely related to cursor type AT_TIMESTAMP. The two parameters determine the position of the data to be read.                                                                                                                                                                                |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | Note:                                                                                                                                                                                                                                                                                                                                                    |
   |                          |                 |                 |                                                                                                                                                                                                                                                                                                                                                          |
   |                          |                 |                 | The timestamp is accurate to milliseconds.                                                                                                                                                                                                                                                                                                               |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------+
   | Parameter             | Type                  | Description                                               |
   +=======================+=======================+===========================================================+
   | partition_cursor      | String                | Data cursor. Value range: a string of 1 to 512 characters |
   |                       |                       |                                                           |
   |                       |                       | Note:                                                     |
   |                       |                       |                                                           |
   |                       |                       | The validity period of a data cursor is 5 minutes.        |
   |                       |                       |                                                           |
   |                       |                       | Minimum: **1**                                            |
   |                       |                       |                                                           |
   |                       |                       | Maximum: **512**                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------+

Example Requests
----------------

Obtaining Data Cursors

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/cursors

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "partition_cursor" : "eyJnZXRJdGVyYXRvclBhcmFtIjp7InN0cmVhbS1uYW1lIjoianpjIiwicGFydGl0aW9uLWlkIjoiMCIsImN1cnNvci10eXBlIjoiQVRfU0VRVUVOQ0VfTlVNQkVSIiwic3RhcnRpbmctc2VxdWVuY2UtbnVtYmVyIjoiMTAifSwiZ2VuZXJhdGVUaW1lc3RhbXAiOjE1MDYxNTk1NjM0MDV9"
   }

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
