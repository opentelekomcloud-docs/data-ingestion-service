:original_name: ShowTransferTask.html

.. _ShowTransferTask:

Querying Dump Task Details
==========================

Function
--------

This API is used to query dump task details.

URI
---

GET /v2/{project_id}/streams/{stream_name}/transfer-tasks/{task_name}

.. table:: **Table 1** Path parameters

   =========== ========= ====== ====================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ====================================
   project_id  Yes       String Project ID.
   stream_name Yes       String Name of the stream.
   task_name   Yes       String Name of the dump task to be deleted.
   =========== ========= ====== ====================================

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Parameter                   | Type                                                                                                       | Description                                                           |
   +=============================+============================================================================================================+=======================================================================+
   | stream_name                 | String                                                                                                     | Name of the stream to which the dump task belongs.                    |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | task_name                   | String                                                                                                     | Name of the dump task.                                                |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | state                       | String                                                                                                     | Dump task status. Possible values:                                    |
   |                             |                                                                                                            |                                                                       |
   |                             |                                                                                                            | -  ERROR: An error occurs.                                            |
   |                             |                                                                                                            | -  STARTING: The dump task is being started.                          |
   |                             |                                                                                                            | -  PAUSED: The dump task has been stopped.                            |
   |                             |                                                                                                            | -  RUNNING: The dump task is running.                                 |
   |                             |                                                                                                            | -  DELETE: The dump task has been deleted.                            |
   |                             |                                                                                                            | -  ABNORMAL: The dump task is abnormal.                               |
   |                             |                                                                                                            |                                                                       |
   |                             |                                                                                                            | Enumeration values:                                                   |
   |                             |                                                                                                            |                                                                       |
   |                             |                                                                                                            | -  **ERROR**                                                          |
   |                             |                                                                                                            | -  **STARTING**                                                       |
   |                             |                                                                                                            | -  **PAUSED**                                                         |
   |                             |                                                                                                            | -  **RUNNING**                                                        |
   |                             |                                                                                                            | -  **DELETE**                                                         |
   |                             |                                                                                                            | -  **ABNORMAL**                                                       |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | destination_type            | String                                                                                                     | Dump destination. Possible values:                                    |
   |                             |                                                                                                            |                                                                       |
   |                             |                                                                                                            | -  OBS: Data is dumped to OBS.                                        |
   |                             |                                                                                                            |                                                                       |
   |                             |                                                                                                            | Enumeration values:                                                   |
   |                             |                                                                                                            |                                                                       |
   |                             |                                                                                                            | -  **OBS**                                                            |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | create_time                 | Long                                                                                                       | Time when the dump task is created.                                   |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | last_transfer_timestamp     | Long                                                                                                       | Latest dump time of the dump task.                                    |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | partitions                  | Array of :ref:`PartitionResult <showtransfertask__response_partitionresult>` objects                       | List of partition dump details.                                       |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | obs_destination_description | :ref:`OBSDestinationDescriptorRequest <showtransfertask__response_obsdestinationdescriptorrequest>` object | Parameter list of OBS to which data in the DIS stream will be dumped. |
   +-----------------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

.. _showtransfertask__response_partitionresult:

.. table:: **Table 4** PartitionResult

   +-----------------------+-----------------------+-------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                 |
   +=======================+=======================+=============================================================+
   | status                | String                | Current status of the partition. Possible values:           |
   |                       |                       |                                                             |
   |                       |                       | -  CREATING: The stream is being created.                   |
   |                       |                       | -  ACTIVE: The stream is available.                         |
   |                       |                       | -  DELETED: The stream is being deleted.                    |
   |                       |                       | -  EXPIRED: The stream has expired.                         |
   |                       |                       |                                                             |
   |                       |                       | Enumeration values:                                         |
   |                       |                       |                                                             |
   |                       |                       | -  **CREATING**                                             |
   |                       |                       | -  **ACTIVE**                                               |
   |                       |                       | -  **DELETED**                                              |
   |                       |                       | -  **EXPIRED**                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | partition_id          | String                | Unique identifier of the partition.                         |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | hash_range            | String                | Possible value range of the hash key used by the partition. |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | sequence_number_range | String                | Sequence number range of the partition.                     |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | parent_partitions     | String                | Parent partition.                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------+

.. _showtransfertask__response_obsdestinationdescriptorrequest:

.. table:: **Table 5** OBSDestinationDescriptorRequest

   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                         | Description                                                                                                                                                                                                                         |
   +=======================+==============================================================================+=====================================================================================================================================================================================================================================+
   | task_name             | String                                                                       | Name of the dump task. The task name consists of letters, digits, hyphens (-), and underscores (_). It must be a string of 1 to 64 characters.                                                                                      |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agency_name           | String                                                                       | Name of the agency created on IAM. DIS uses an agency to access your specified resources. The parameters for creating an agency are as follows:                                                                                     |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  Agency Type: Cloud service                                                                                                                                                                                                       |
   |                       |                                                                              | -  Cloud Service: DIS                                                                                                                                                                                                               |
   |                       |                                                                              | -  Validity Period: unlimited                                                                                                                                                                                                       |
   |                       |                                                                              | -  Scope: Global service, Project: OBS. Select the Tenant Administrator role for the global service project.                                                                                                                        |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | If agencies have been created, you can obtain available agencies from the agency list by using the "Listing Agencies " API.                                                                                                         |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | This parameter cannot be left blank and the parameter value cannot exceed 64 characters.                                                                                                                                            |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | If there are dump tasks on the console, the system displays a message indicating that an agency will be automatically created. The name of the automatically created agency is dis_admin_agency.                                    |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Maximum: **64**                                                                                                                                                                                                                     |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | deliver_time_interval | Integer                                                                      | User-defined interval at which data is imported from the current DIS stream into OBS. If no data is pushed to the DIS stream during the current interval, no dump file package will be generated.                                   |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Value range: 30-900                                                                                                                                                                                                                 |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default value: 300                                                                                                                                                                                                                  |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Unit: second                                                                                                                                                                                                                        |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Minimum: **30**                                                                                                                                                                                                                     |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Maximum: **900**                                                                                                                                                                                                                    |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default: **300**                                                                                                                                                                                                                    |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consumer_strategy     | String                                                                       | Offset.                                                                                                                                                                                                                             |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  LATEST: Maximum offset, indicating that the latest data will be extracted.                                                                                                                                                       |
   |                       |                                                                              | -  TRIM_HORIZON: Minimum offset, indicating that the earliest data will be extracted.                                                                                                                                               |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default value: LATEST                                                                                                                                                                                                               |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default: **LATEST**                                                                                                                                                                                                                 |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Enumeration values:                                                                                                                                                                                                                 |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  **LATEST**                                                                                                                                                                                                                       |
   |                       |                                                                              | -  **TRIM_HORIZON**                                                                                                                                                                                                                 |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_prefix           | String                                                                       | Directory to store files that will be dumped to OBS. Different directory levels are separated by slashes (/) and cannot start with slashes.                                                                                         |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | The value can contain a maximum of 50 characters, including letters, digits, underscores (_), and slashes (/).                                                                                                                      |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | This parameter is left empty by default.                                                                                                                                                                                            |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Maximum: **50**                                                                                                                                                                                                                     |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_format      | String                                                                       | Directory structure of the object file written into OBS. The directory structure is in the format of yyyy/MM/dd/HH/mm (time at which the dump task was created).                                                                    |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  N/A: Leave this parameter empty, indicating that the date and time directory is not used.                                                                                                                                        |
   |                       |                                                                              | -  yyyy: year                                                                                                                                                                                                                       |
   |                       |                                                                              | -  yyyy/MM: year/month                                                                                                                                                                                                              |
   |                       |                                                                              | -  yyyy/MM/dd: year/month/day                                                                                                                                                                                                       |
   |                       |                                                                              | -  yyyy/MM/dd/HH: year/month/day/hour                                                                                                                                                                                               |
   |                       |                                                                              | -  yyyy/MM/dd/HH/mm: year/month/day/hour/minute                                                                                                                                                                                     |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Example: in 2017/11/10/14/49, the directory structure is 2017 > 11 > 10 > 14 > 49. 2017 indicates the outermost folder.                                                                                                             |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default value: empty.                                                                                                                                                                                                               |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Note:                                                                                                                                                                                                                               |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | After data is successfully dumped, the directory structure is obs_bucket_path/file_prefix/partition_format.                                                                                                                         |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Enumeration values:                                                                                                                                                                                                                 |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  **yyyy**                                                                                                                                                                                                                         |
   |                       |                                                                              | -  **yyyy/MM**                                                                                                                                                                                                                      |
   |                       |                                                                              | -  **yyyy/MM/dd**                                                                                                                                                                                                                   |
   |                       |                                                                              | -  **yyyy/MM/dd/HH**                                                                                                                                                                                                                |
   |                       |                                                                              | -  **yyyy/MM/dd/HH/mm**                                                                                                                                                                                                             |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_bucket_path       | String                                                                       | Name of the OBS bucket used to store data from the DIS stream.                                                                                                                                                                      |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_file_type | String                                                                       | Dump file format. Possible values:                                                                                                                                                                                                  |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  Text (default)                                                                                                                                                                                                                   |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default: **text**                                                                                                                                                                                                                   |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Enumeration values:                                                                                                                                                                                                                 |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  **text**                                                                                                                                                                                                                         |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | processing_schema     | :ref:`ProcessingSchema <showtransfertask__response_processingschema>` object | Dump time directory generated based on the timestamp of the source data and the configured partition_format. Directory structure of the object file written into OBS. The directory structure is in the format of yyyy/MM/dd/HH/mm. |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | record_delimiter      | String                                                                       | Delimiter for the dump file, which is used to separate the user data that is written into the dump file.                                                                                                                            |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Value range:                                                                                                                                                                                                                        |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | -  Comma (,), which is the default value                                                                                                                                                                                            |
   |                       |                                                                              | -  Semicolon (;)                                                                                                                                                                                                                    |
   |                       |                                                                              | -  Vertical bar (|)                                                                                                                                                                                                                 |
   |                       |                                                                              | -  Newline character (\\n)                                                                                                                                                                                                          |
   |                       |                                                                              |                                                                                                                                                                                                                                     |
   |                       |                                                                              | Default: **\\n**                                                                                                                                                                                                                    |
   +-----------------------+------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _showtransfertask__response_processingschema:

.. table:: **Table 6** ProcessingSchema

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | timestamp_name        | String                | Attribute name of the source data timestamp.                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp_type        | String                | Type of the source data timestamp.                                                                                                       |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  String                                                                                                                                |
   |                       |                       | -  Timestamp: 13-bit timestamp of the long type                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp_format      | String                | OBS directory generated based on the timestamp format. This parameter is mandatory when the timestamp type of the source data is String. |
   |                       |                       |                                                                                                                                          |
   |                       |                       | Value range:                                                                                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  yyyy/MM/dd HH:mm:ss                                                                                                                   |
   |                       |                       | -  MM/dd/yyyy HH:mm:ss                                                                                                                   |
   |                       |                       | -  dd/MM/yyyy HH:mm:ss                                                                                                                   |
   |                       |                       | -  yyyy-MM-dd HH:mm:ss                                                                                                                   |
   |                       |                       | -  MM-dd-yyyy HH:mm:ss                                                                                                                   |
   |                       |                       | -  dd-MM-yyyy HH:mm:ss                                                                                                                   |
   |                       |                       |                                                                                                                                          |
   |                       |                       | Enumeration values:                                                                                                                      |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **yyyy/MM/dd HH:mm:ss**                                                                                                               |
   |                       |                       | -  **MM/dd/yyyy HH:mm:ss**                                                                                                               |
   |                       |                       | -  **dd/MM/yyyy HH:mm:ss**                                                                                                               |
   |                       |                       | -  **yyyy-MM-dd HH:mm:ss**                                                                                                               |
   |                       |                       | -  **MM-dd-yyyy HH:mm:ss**                                                                                                               |
   |                       |                       | -  **dd-MM-yyyy HH:mm:ss**                                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Dump Task Details

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks/{task_name}

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "stream_id" : "RdMFID6edQdf8eDzc9e",
     "stream_name" : "newstream",
     "task_name" : "newtask",
     "task_id" : "As805BudhcH1lDs6gbn",
     "destination_type" : "OBS",
     "state" : "RUNNING",
     "create_time" : 1606554932552,
     "last_transfer_timestamp" : 1606984428612,
     "obs_destination_description" : {
       "agency_name" : "dis_admin_agency",
       "file_prefix\"" : "",
       "partition_format" : "yyyy/MM/dd",
       "obs_bucket_path" : "obsbucket",
       "deliver_time_interval" : 60,
       "consumer_strategy" : "LATEST",
       "retry_duration" : 0,
       "destination_file_type" : "text",
       "record_delimiter" : "\n"
     },
     "partitions" : [ {
       "partitionId" : "shardId-0000000000",
       "discard" : 0,
       "state" : "RUNNING",
       "last_transfer_timestamp" : 1606984428612,
       "last_transfer_offset" : 289897
     } ]
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
