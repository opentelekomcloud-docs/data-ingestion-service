:original_name: dis_02_0016_01.html

.. _dis_02_0016_01:

Creating Streams
================

Function
--------

This API is used to create a stream.

-  When creating a stream, specify a stream type (common or advanced) and the number of partitions.

-  By default, an account can create a maximum of 10 advanced stream partitions and 50 common stream partitions. You can submit a service ticket to increase the quota.

URI
---

POST /v2/{project_id}/streams

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

   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Mandatory       | Type                                                                | Description                                                                                                                                                          |
   +================================+=================+=====================================================================+======================================================================================================================================================================+
   | stream_name                    | Yes             | String                                                              | Name of the stream.                                                                                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | The stream name can contain 1 to 64 characters, including letters, digits, underscores (_), and hyphens (-).                                                         |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Maximum: **64**                                                                                                                                                      |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_count                | Yes             | Integer                                                             | Number of partitions. Partitions are the base throughput unit of a DIS stream.                                                                                       |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | stream_type                    | No              | String                                                              | Stream type.                                                                                                                                                         |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  COMMON: a common stream. The bandwidth is 1 MB/s.                                                                                                                 |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  ADVANCED: an advanced stream. The bandwidth is 5 MB/s.                                                                                                            |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Enumeration values:                                                                                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **COMMON**                                                                                                                                                        |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **ADVANCED**                                                                                                                                                      |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_type                      | No              | String                                                              | Source data type.                                                                                                                                                    |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  BLOB: a set of binary data stored in a database management system.                                                                                                |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  JSON: an open-source file format that uses readable text to transmit data objects consisting of attribute values or serialized values.                            |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  CSV: a simple text format for storing tabular data in a plain text file. Commas (,) are used as separators by default.                                            |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Default value: BLOB                                                                                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Enumeration values:                                                                                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **BLOB**                                                                                                                                                          |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **JSON**                                                                                                                                                          |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **CSV**                                                                                                                                                           |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_duration                  | No              | Integer                                                             | Period of time for which data is retained in the stream. Value range: 24-72 Unit: hour Default value: 24 If this parameter is left blank, the default value is used. |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Maximum: **168**                                                                                                                                                     |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Default: **24**                                                                                                                                                      |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_enabled             | No              | Boolean                                                             | Specifies whether to enable auto scaling.                                                                                                                            |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  true: Auto scaling is enabled.                                                                                                                                    |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  false: Auto scaling is disabled.                                                                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | This function is disabled by default.                                                                                                                                |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Default: **false**                                                                                                                                                   |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_min_partition_count | No              | Long                                                                | Minimum number of partitions for automatic scale-down when auto scaling is enabled.                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Minimum: **1**                                                                                                                                                       |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_max_partition_count | No              | Integer                                                             | Maximum number of partitions for automatic scale-up when auto scaling is enabled.                                                                                    |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_schema                    | No              | String                                                              | Source data structure that defines JSON and CSV formats. It is described in the syntax of the Avro schema.                                                           |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | csv_properties                 | No              | :ref:`CSVProperties <dis_02_0016_01__request_csvproperties>` object | Attributes of data in CSV format, such as delimiter.                                                                                                                 |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | compression_format             | No              | String                                                              | Compression type of data. Currently, the value can be:                                                                                                               |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  snappy                                                                                                                                                            |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  gzip                                                                                                                                                              |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  zip                                                                                                                                                               |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Data is not compressed by default.                                                                                                                                   |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | Enumeration values:                                                                                                                                                  |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **snappy**                                                                                                                                                        |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **gzip**                                                                                                                                                          |
   |                                |                 |                                                                     |                                                                                                                                                                      |
   |                                |                 |                                                                     | -  **zip**                                                                                                                                                           |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                           | No              | Array of :ref:`Tag <dis_02_0016_01__request_tag>` objects           | List of stream tags.                                                                                                                                                 |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sys_tags                       | No              | Array of :ref:`SysTag <dis_02_0016_01__request_systag>` objects     | Stream enterprise projects.                                                                                                                                          |
   +--------------------------------+-----------------+---------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dis_02_0016_01__request_csvproperties:

.. table:: **Table 4** CSVProperties

   ========= ========= ====== ===============
   Parameter Mandatory Type   Description
   ========= ========= ====== ===============
   delimiter No        String Data separator.
   ========= ========= ====== ===============

.. _dis_02_0016_01__request_tag:

.. table:: **Table 5** Tag

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                |
   +=================+=================+=================+============================================================================================+
   | key             | No              | String          | Key.                                                                                       |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  This field cannot be left blank.                                                        |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  The key value of a resource must be unique.                                             |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  Character set: A-Z, a-z, 0-9, '-', '_', and Unicode characters (\\u4E00-\\u9FFF).       |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                             |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Maximum: **36**                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value.                                                                                     |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  The value contains a maximum of 43 characters.                                          |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  Character set: A-Z, a-z, 0-9, '. ', '-', '_', and Unicode characters (\\u4E00-\\u9FFF). |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  The value can contain only digits, letters, hyphens (-), and underscores (_).           |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Minimum: **0**                                                                             |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Maximum: **43**                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+

.. _dis_02_0016_01__request_systag:

.. table:: **Table 6** SysTag

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | key             | No              | String          | Key.                                                                                                         |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  This field cannot be left blank.                                                                          |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  The value must be \_sys_enterprise_project_id.                                                            |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Enumeration values:                                                                                          |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  **\_sys_enterprise_project_id**                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value. The value is the enterprise project ID, which needs to be obtained on the enterprise management page. |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  36-digit UUID                                                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Creating Streams

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/streams

   {
     "stream_name" : "newstream",
     "partition_count" : 3,
     "data_duration" : 24
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
201         Created
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
