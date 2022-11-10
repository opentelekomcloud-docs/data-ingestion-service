:original_name: dis_02_0019.html

.. _dis_02_0019:

Downloading Data
================

Function
--------

This API is used to download data from DIS streams.

URI
---

GET /v2/{project_id}/records

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                            |
   +==================+=================+=================+========================================================================================================+
   | partition-cursor | Yes             | String          | Data cursor, which needs to be obtained through the API for obtaining data cursors.                    |
   |                  |                 |                 |                                                                                                        |
   |                  |                 |                 | Value range: a string of 1 to 512 characters                                                           |
   |                  |                 |                 |                                                                                                        |
   |                  |                 |                 | Note:                                                                                                  |
   |                  |                 |                 |                                                                                                        |
   |                  |                 |                 | The validity period of a data cursor is 5 minutes.                                                     |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | max_fetch_bytes  | No              | Integer         | Maximum number of bytes that can be obtained for each request.                                         |
   |                  |                 |                 |                                                                                                        |
   |                  |                 |                 | Note:                                                                                                  |
   |                  |                 |                 |                                                                                                        |
   |                  |                 |                 | If the value is less than the size of a single record in the partition, the record cannot be obtained. |
   +------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

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

   +-----------------------+---------------------------------------------------------------+----------------------------------------------------+
   | Parameter             | Type                                                          | Description                                        |
   +=======================+===============================================================+====================================================+
   | records               | Array of :ref:`Record <dis_02_0019__response_record>` objects | List of downloaded records.                        |
   +-----------------------+---------------------------------------------------------------+----------------------------------------------------+
   | next_partition_cursor | String                                                        | Next iterator.                                     |
   |                       |                                                               |                                                    |
   |                       |                                                               | Note:                                              |
   |                       |                                                               |                                                    |
   |                       |                                                               | The validity period of a data cursor is 5 minutes. |
   +-----------------------+---------------------------------------------------------------+----------------------------------------------------+

.. _dis_02_0019__response_record:

.. table:: **Table 5** Record

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================+
   | partition_key         | String                | Partition key set when data is being uploaded.                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                  |
   |                       |                       | Note:                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                  |
   |                       |                       | If the partition_key parameter is passed when data is uploaded, this parameter will be returned when data is downloaded. If partition_id instead of partition_key is passed when data is uploaded, no partition_key is returned. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sequence_number       | String                | Sequence number of the data record.                                                                                                                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data                  | String                | Downloaded data.                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                  |
   |                       |                       | The downloaded data is the serialized binary data (Base64-encoded character string).                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                  |
   |                       |                       | For example, the data returned by the data download API is "ZGF0YQ==", which is "data" after Base64 decoding.                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp             | Long                  | Timestamp when the record is written to DIS.                                                                                                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp_type        | String                | Timestamp data type.                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                  |
   |                       |                       | -  CreateTime: creation time.                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                  |
   |                       |                       | Default: **CreateTime**                                                                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Downloading Data

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/records

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "records" : [ {
       "partition_key" : "0",
       "sequence_number" : "485",
       "data" : "MTExMTExMTExMTExMTExMTExMTExMTExMTExMTExMTEx",
       "timestamp" : 1527577402541,
       "timestamp_type" : "CreateTime"
     } ],
     "next_partition_cursor" : "eyJpdGVyR2VuVGltZSI6MTQ5MDk1MDE1Nzc0NywiU3RyZWFtTmFtZSI6IjY2MCIsIlNoYXJkSWQiOiIwIiwiU2hhcmRJdGVyYXRvclR5cGUiOiJBVF9TRVFVRU5DRV9OVU1CRVIiLCJTdGFydGluZ1NlcXVlbmNlTnVtYmVyIjoiMjIiLCJUaW1lU3RhbXAiOjB9"
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
