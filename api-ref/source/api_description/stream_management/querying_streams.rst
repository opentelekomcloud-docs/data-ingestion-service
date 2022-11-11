:original_name: dis_02_0024.html

.. _dis_02_0024:

Querying Streams
================

Function
--------

This API is used to query all streams created by the current tenant.

During the query, specify the stream from which the stream list is returned and the maximum number of streams to be returned for a single request.

URI
---

GET /v2/{project_id}/streams

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

.. table:: **Table 2** Query parameters

   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                             |
   +===================+=================+=================+=========================================================================================================================================================================================================================================================================================+
   | limit             | No              | Integer         | The maximum number of DIS streams to list in a single API call.                                                                                                                                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                                                                                                                         |
   |                   |                 |                 | Value range: 1-100 Default value: 10                                                                                                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                                                                                                         |
   |                   |                 |                 | Minimum: **1**                                                                                                                                                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                                                                                                                         |
   |                   |                 |                 | Maximum: **100**                                                                                                                                                                                                                                                                        |
   |                   |                 |                 |                                                                                                                                                                                                                                                                                         |
   |                   |                 |                 | Default: **10**                                                                                                                                                                                                                                                                         |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_stream_name | No              | String          | Name of the DIS stream to start the stream list with. The returned stream list does not contain this DIS stream name.                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                                                                                                         |
   |                   |                 |                 | If pagination query is required, this parameter is not transferred for query on the first page. If the value of has_more_streams is true, the query is performed on the next page. The value of start_stream_name is the name of the last stream in the query result of the first page. |
   +-------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Parameter             | Type                                                                  | Description                                                                   |
   +=======================+=======================================================================+===============================================================================+
   | total_number          | Long                                                                  | Total number of all the DIS streams created by the current tenant.            |
   +-----------------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | stream_names          | Array of strings                                                      | List of the streams meeting the current requests.                             |
   +-----------------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | has_more_streams      | Boolean                                                               | Specify whether there are more matching DIS streams to list. Possible values: |
   |                       |                                                                       |                                                                               |
   |                       |                                                                       | -  true: yes                                                                  |
   |                       |                                                                       |                                                                               |
   |                       |                                                                       | -  false: no                                                                  |
   |                       |                                                                       |                                                                               |
   |                       |                                                                       | Default: **false**                                                            |
   +-----------------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | stream_info_list      | Array of :ref:`StreamInfo <dis_02_0024__response_streaminfo>` objects | Stream details.                                                               |
   +-----------------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------+

.. _dis_02_0024__response_streaminfo:

.. table:: **Table 5** StreamInfo

   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Type                                                          | Description                                                                                                                                            |
   +================================+===============================================================+========================================================================================================================================================+
   | stream_name                    | String                                                        | Name of the stream.                                                                                                                                    |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time                    | Long                                                          | Time when the stream is created. The value is a 13-bit timestamp.                                                                                      |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | retention_period               | Integer                                                       | Period for storing data in units of hours.                                                                                                             |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                         | String                                                        | Current status of the stream. Possible values:                                                                                                         |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  CREATING: The stream is being created.                                                                                                              |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  RUNNING: The stream is running.                                                                                                                     |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  TERMINATING: The stream is being deleted.                                                                                                           |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  TERMINATED: The stream has been deleted.                                                                                                            |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | Enumeration values:                                                                                                                                    |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **CREATING**                                                                                                                                        |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **RUNNING**                                                                                                                                         |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **TERMINATING**                                                                                                                                     |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **FROZEN**                                                                                                                                          |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | stream_type                    | String                                                        | Stream type.                                                                                                                                           |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  COMMON: a common stream. The bandwidth is 1 MB/s.                                                                                                   |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  ADVANCED: an advanced stream. The bandwidth is 5 MB/s.                                                                                              |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | Enumeration values:                                                                                                                                    |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **COMMON**                                                                                                                                          |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **ADVANCED**                                                                                                                                        |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_type                      | String                                                        | Source data type.                                                                                                                                      |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  BLOB: a collection of binary data stored as a single entity in a database management system.                                                        |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  JSON: an open-standard file format that uses human-readable text to transmit data objects consisting of attribute-value pairs and array data types. |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  CSV: a simple text format for storing tabular data in a plain text file. Commas are used as delimiters.                                             |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | Default value: BLOB                                                                                                                                    |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | Enumeration values:                                                                                                                                    |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **BLOB**                                                                                                                                            |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **JSON**                                                                                                                                            |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  **CSV**                                                                                                                                             |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_count                | Integer                                                       | Quantity of partitions. Partitions are the base throughput unit of a DIS stream.                                                                       |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_enabled             | Boolean                                                       | Specifies whether to enable auto scaling.                                                                                                              |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  true: auto scaling is enabled.                                                                                                                      |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | -  false: auto scaling is disabled.                                                                                                                    |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | This function is disabled by default.                                                                                                                  |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | Default: **false**                                                                                                                                     |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_min_partition_count | Integer                                                       | Minimum number of partitions for automatic scale-down when auto scaling is enabled.                                                                    |
   |                                |                                                               |                                                                                                                                                        |
   |                                |                                                               | Minimum: **1**                                                                                                                                         |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_max_partition_count | Integer                                                       | Maximum number of partitions for automatic scale-up when auto scaling is enabled.                                                                      |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                           | Array of :ref:`Tag <dis_02_0024__response_tag>` objects       | List of stream tags.                                                                                                                                   |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags                       | Array of :ref:`SysTag <dis_02_0024__response_systag>` objects | Stream enterprise projects.                                                                                                                            |
   +--------------------------------+---------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dis_02_0024__response_tag:

.. table:: **Table 6** Tag

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                |
   +=======================+=======================+============================================================================================+
   | key                   | String                | Key.                                                                                       |
   |                       |                       |                                                                                            |
   |                       |                       | -  This field cannot be left blank.                                                        |
   |                       |                       |                                                                                            |
   |                       |                       | -  The key value of a resource must be unique.                                             |
   |                       |                       |                                                                                            |
   |                       |                       | -  Character set: A-Z, a-z, 0-9, '-', '_', and Unicode characters (\\u4E00-\\u9FFF).       |
   |                       |                       |                                                                                            |
   |                       |                       | Minimum: **1**                                                                             |
   |                       |                       |                                                                                            |
   |                       |                       | Maximum: **36**                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+
   | value                 | String                | Value.                                                                                     |
   |                       |                       |                                                                                            |
   |                       |                       | -  The value contains a maximum of 43 characters.                                          |
   |                       |                       |                                                                                            |
   |                       |                       | -  Character set: A-Z, a-z, 0-9, '. ', '-', '_', and Unicode characters (\\u4E00-\\u9FFF). |
   |                       |                       |                                                                                            |
   |                       |                       | -  The value can contain only digits, letters, hyphens (-), and underscores (_).           |
   |                       |                       |                                                                                            |
   |                       |                       | Minimum: **0**                                                                             |
   |                       |                       |                                                                                            |
   |                       |                       | Maximum: **43**                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+

.. _dis_02_0024__response_systag:

.. table:: **Table 7** SysTag

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                  |
   +=======================+=======================+==============================================================================================================+
   | key                   | String                | Key.                                                                                                         |
   |                       |                       |                                                                                                              |
   |                       |                       | -  This field cannot be left blank.                                                                          |
   |                       |                       |                                                                                                              |
   |                       |                       | -  The value must be \_sys_enterprise_project_id.                                                            |
   |                       |                       |                                                                                                              |
   |                       |                       | Enumeration values:                                                                                          |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **\_sys_enterprise_project_id**                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Value. The value is the enterprise project ID, which needs to be obtained on the enterprise management page. |
   |                       |                       |                                                                                                              |
   |                       |                       | -  36-digit UUID                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Streams

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/streams

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "total_number" : 1,
     "stream_names" : [ "newstream" ],
     "stream_info_list" : [ {
       "stream_id" : "8QM3Nt9YTLOwtUVYJhO",
       "stream_name" : "newstream",
       "create_time" : 1593569685875,
       "retention_period" : 24,
       "status" : "RUNNING",
       "stream_type" : "COMMON",
       "data_type" : "BLOB",
       "partition_count" : 1,
       "tags" : [ ],
       "auto_scale_enabled" : false,
       "auto_scale_min_partition_count" : 0,
       "auto_scale_max_partition_count" : 0
     } ],
     "has_more_streams" : false
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
