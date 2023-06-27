:original_name: dis_02_0016_01.html

.. _dis_02_0016_01:

Creating Streams
================

Function
--------

This API is used to create a stream.

-  When creating a stream, specify a stream type (common or advanced) and the number of partitions.
-  A maximum of 10 advanced stream partitions and 50 common stream partitions can be created for an account by default. You can submit a work order to increase the quota.

URI
---

POST /v2/{project_id}/streams

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Mandatory       | Type                                                            | Description                                                                                                  |
   +================================+=================+=================================================================+==============================================================================================================+
   | stream_name                    | Yes             | String                                                          | Stream name                                                                                                  |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | The stream name can contain 1 to 64 characters, including letters, digits, underscores (_), and hyphens (-). |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Maximum: **64**                                                                                              |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | partition_count                | Yes             | Integer                                                         | Number of partitions                                                                                         |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Partitions are the base throughput unit of the DIS stream.                                                   |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | stream_type                    | No              | String                                                          | Stream type                                                                                                  |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  **COMMON**: a common stream with a bandwidth of 1 MB/s                                                    |
   |                                |                 |                                                                 | -  **ADVANCED**: an advanced stream with a bandwidth of 5 MB/s                                               |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Enumeration values:                                                                                          |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  **COMMON**                                                                                                |
   |                                |                 |                                                                 | -  **ADVANCED**                                                                                              |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | data_type                      | No              | String                                                          | Source data type                                                                                             |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  **BLOB**: a collection of binary data stored as a single entity in a database management system           |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Default value: **BLOB**                                                                                      |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Enumeration values:                                                                                          |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  **BLOB**                                                                                                  |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | data_duration                  | No              | Integer                                                         | Data retention period                                                                                        |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Value range: 24-72                                                                                           |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Unit: hour                                                                                                   |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Default value: **24**                                                                                        |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | If this parameter is left unspecified, the default value will be used.                                       |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Maximum: **72**                                                                                              |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Default: **24**                                                                                              |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | auto_scale_enabled             | No              | Boolean                                                         | Whether to enable auto scaling                                                                               |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  **true**: Auto scaling is enabled.                                                                        |
   |                                |                 |                                                                 | -  **false**: Auto scaling is disabled.                                                                      |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | By default, this function is disabled.                                                                       |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Default: **false**                                                                                           |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | auto_scale_min_partition_count | No              | Long                                                            | Minimum number of partitions for automatic scale-down when auto scaling is enabled.                          |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Minimum: **1**                                                                                               |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | auto_scale_max_partition_count | No              | Integer                                                         | Maximum number of partitions for automatic scale-up when auto scaling is enabled.                            |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | compression_format             | No              | String                                                          | Data compression type. The following types are available:                                                    |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  snappy                                                                                                    |
   |                                |                 |                                                                 | -  gzip                                                                                                      |
   |                                |                 |                                                                 | -  zip                                                                                                       |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Data is not compressed by default.                                                                           |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | Enumeration values:                                                                                          |
   |                                |                 |                                                                 |                                                                                                              |
   |                                |                 |                                                                 | -  **snappy**                                                                                                |
   |                                |                 |                                                                 | -  **gzip**                                                                                                  |
   |                                |                 |                                                                 | -  **zip**                                                                                                   |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | tags                           | No              | Array of :ref:`Tag <dis_02_0016_01__request_tag>` objects       | List of stream tags.                                                                                         |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | sys_tags                       | No              | Array of :ref:`SysTag <dis_02_0016_01__request_systag>` objects | Stream enterprise projects.                                                                                  |
   +--------------------------------+-----------------+-----------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+

.. _dis_02_0016_01__request_tag:

.. table:: **Table 4** Tag

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================+
   | key             | No              | String          | Key                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It cannot be left blank.                                                                                                                     |
   |                 |                 |                 | -  It must be unique for each resource.                                                                                                         |
   |                 |                 |                 | -  It can contain uppercase and lowercase letters, digits, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF).              |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Minimum: **1**                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Maximum: **36**                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It can contain a maximum of 43 characters.                                                                                                   |
   |                 |                 |                 | -  It can contain uppercase and lowercase letters, digits, periods (.), hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
   |                 |                 |                 | -  It can only contain digits, letters, hyphens (-), and underscores (_).                                                                       |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Minimum: **0**                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Maximum: **43**                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dis_02_0016_01__request_systag:

.. table:: **Table 5** SysTag

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | key             | No              | String          | Key                                                                                                          |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  It cannot be left blank.                                                                                  |
   |                 |                 |                 | -  Its value must be **\_sys_enterprise_project_id**.                                                        |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Enumeration values:                                                                                          |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  **\_sys_enterprise_project_id**                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value. The value is the enterprise project ID, which needs to be obtained on the enterprise management page. |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  It is a 36-digit UUID.                                                                                    |
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
