:original_name: dis_02_0410.html

.. _dis_02_0410:

Adding OBS Dump Tasks
=====================

Function
--------

This API is used to add OBS dump tasks.

URI
---

POST /v2/{project_id}/streams/{stream_name}/transfer-tasks

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+---------------------+
   | Parameter       | Mandatory       | Type            | Description         |
   +=================+=================+=================+=====================+
   | project_id      | Yes             | String          | Project ID.         |
   +-----------------+-----------------+-----------------+---------------------+
   | stream_name     | Yes             | String          | Name of the stream. |
   |                 |                 |                 |                     |
   |                 |                 |                 | Maximum: **60**     |
   +-----------------+-----------------+-----------------+---------------------+

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

   +----------------------------+-----------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | Parameter                  | Mandatory       | Type                                                                                                 | Description                                                           |
   +============================+=================+======================================================================================================+=======================================================================+
   | destination_type           | Yes             | String                                                                                               | Dump destination. Possible values:                                    |
   |                            |                 |                                                                                                      |                                                                       |
   |                            |                 |                                                                                                      | -  OBS: Data is dumped to OBS.                                        |
   |                            |                 |                                                                                                      | -  MRS: Data is dumped to MRS.                                        |
   |                            |                 |                                                                                                      | -  DLI: Data is dumped to DLI.                                        |
   |                            |                 |                                                                                                      | -  CLOUDTABLE: Data is dumped to CloudTable.                          |
   |                            |                 |                                                                                                      | -  DWS: Data is dumped to DWS.                                        |
   |                            |                 |                                                                                                      |                                                                       |
   |                            |                 |                                                                                                      | Default: **NOWHERE**                                                  |
   |                            |                 |                                                                                                      |                                                                       |
   |                            |                 |                                                                                                      | Enumeration values:                                                   |
   |                            |                 |                                                                                                      |                                                                       |
   |                            |                 |                                                                                                      | -  **OBS**                                                            |
   +----------------------------+-----------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+
   | obs_destination_descriptor | No              | :ref:`OBSDestinationDescriptorRequest <dis_02_0410__request_obsdestinationdescriptorrequest>` object | Parameter list of OBS to which data in the DIS stream will be dumped. |
   +----------------------------+-----------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------+

.. _dis_02_0410__request_obsdestinationdescriptorrequest:

.. table:: **Table 4** OBSDestinationDescriptorRequest

   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                   | Description                                                                                                                                                                                                                         |
   +=======================+=================+========================================================================+=====================================================================================================================================================================================================================================+
   | task_name             | Yes             | String                                                                 | Name of the dump task. The task name consists of letters, digits, hyphens (-), and underscores (_). It must be a string of 1 to 64 characters.                                                                                      |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agency_name           | Yes             | String                                                                 | Name of the agency created on IAM. DIS uses an agency to access your specified resources. The parameters for creating an agency are as follows:                                                                                     |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  Agency Type: Cloud service                                                                                                                                                                                                       |
   |                       |                 |                                                                        | -  Cloud Service: DIS                                                                                                                                                                                                               |
   |                       |                 |                                                                        | -  Validity Period: unlimited                                                                                                                                                                                                       |
   |                       |                 |                                                                        | -  Scope: Global service, Project: OBS. Select the Tenant Administrator role for the global service project.                                                                                                                        |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | If agencies have been created, you can obtain available agencies from the agency list by using the "Listing Agencies " API.                                                                                                         |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | This parameter cannot be left blank and the parameter value cannot exceed 64 characters.                                                                                                                                            |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | If there are dump tasks on the console, the system displays a message indicating that an agency will be automatically created. The name of the automatically created agency is dis_admin_agency.                                    |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Maximum: **64**                                                                                                                                                                                                                     |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | deliver_time_interval | Yes             | Integer                                                                | User-defined interval at which data is imported from the current DIS stream into OBS. If no data is pushed to the DIS stream during the current interval, no dump file package will be generated.                                   |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Value range: 30-900                                                                                                                                                                                                                 |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default value: 300                                                                                                                                                                                                                  |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Unit: second                                                                                                                                                                                                                        |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Minimum: **30**                                                                                                                                                                                                                     |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Maximum: **900**                                                                                                                                                                                                                    |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default: **300**                                                                                                                                                                                                                    |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consumer_strategy     | No              | String                                                                 | Offset.                                                                                                                                                                                                                             |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  LATEST: Maximum offset, indicating that the latest data will be extracted.                                                                                                                                                       |
   |                       |                 |                                                                        | -  TRIM_HORIZON: Minimum offset, indicating that the earliest data will be extracted.                                                                                                                                               |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default value: LATEST                                                                                                                                                                                                               |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default: **LATEST**                                                                                                                                                                                                                 |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Enumeration values:                                                                                                                                                                                                                 |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  **LATEST**                                                                                                                                                                                                                       |
   |                       |                 |                                                                        | -  **TRIM_HORIZON**                                                                                                                                                                                                                 |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_prefix           | No              | String                                                                 | Directory to store files that will be dumped to OBS. Different directory levels are separated by slashes (/) and cannot start with slashes.                                                                                         |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | The value can contain a maximum of 50 characters, including letters, digits, underscores (_), and slashes (/).                                                                                                                      |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | This parameter is left empty by default.                                                                                                                                                                                            |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Maximum: **50**                                                                                                                                                                                                                     |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_format      | No              | String                                                                 | Directory structure of the object file written into OBS. The directory structure is in the format of yyyy/MM/dd/HH/mm (time at which the dump task was created).                                                                    |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  N/A: Leave this parameter empty, indicating that the date and time directory is not used.                                                                                                                                        |
   |                       |                 |                                                                        | -  yyyy: year                                                                                                                                                                                                                       |
   |                       |                 |                                                                        | -  yyyy/MM: year/month                                                                                                                                                                                                              |
   |                       |                 |                                                                        | -  yyyy/MM/dd: year/month/day                                                                                                                                                                                                       |
   |                       |                 |                                                                        | -  yyyy/MM/dd/HH: year/month/day/hour                                                                                                                                                                                               |
   |                       |                 |                                                                        | -  yyyy/MM/dd/HH/mm: year/month/day/hour/minute                                                                                                                                                                                     |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Example: in 2017/11/10/14/49, the directory structure is 2017 > 11 > 10 > 14 > 49. 2017 indicates the outermost folder.                                                                                                             |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default value: empty.                                                                                                                                                                                                               |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Note:                                                                                                                                                                                                                               |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | After data is successfully dumped, the directory structure is obs_bucket_path/file_prefix/partition_format.                                                                                                                         |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Enumeration values:                                                                                                                                                                                                                 |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  **yyyy**                                                                                                                                                                                                                         |
   |                       |                 |                                                                        | -  **yyyy/MM**                                                                                                                                                                                                                      |
   |                       |                 |                                                                        | -  **yyyy/MM/dd**                                                                                                                                                                                                                   |
   |                       |                 |                                                                        | -  **yyyy/MM/dd/HH**                                                                                                                                                                                                                |
   |                       |                 |                                                                        | -  **yyyy/MM/dd/HH/mm**                                                                                                                                                                                                             |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_bucket_path       | Yes             | String                                                                 | Name of the OBS bucket used to store data from the DIS stream.                                                                                                                                                                      |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | destination_file_type | No              | String                                                                 | Dump file format. Possible values:                                                                                                                                                                                                  |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  Text (default)                                                                                                                                                                                                                   |
   |                       |                 |                                                                        | -  Parquet                                                                                                                                                                                                                          |
   |                       |                 |                                                                        | -  CarbonData                                                                                                                                                                                                                       |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Note:                                                                                                                                                                                                                               |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | You can select Parquet or CarbonData only when Source Data Type is set to JSON and Dump Destination is set to OBS.                                                                                                                  |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default: **text**                                                                                                                                                                                                                   |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Enumeration values:                                                                                                                                                                                                                 |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  **text**                                                                                                                                                                                                                         |
   |                       |                 |                                                                        | -  **parquet**                                                                                                                                                                                                                      |
   |                       |                 |                                                                        | -  **carbon**                                                                                                                                                                                                                       |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | processing_schema     | No              | :ref:`ProcessingSchema <dis_02_0410__request_processingschema>` object | Dump time directory generated based on the timestamp of the source data and the configured partition_format. Directory structure of the object file written into OBS. The directory structure is in the format of yyyy/MM/dd/HH/mm. |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | record_delimiter      | No              | String                                                                 | Delimiter for the dump file, which is used to separate the user data that is written into the dump file.                                                                                                                            |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Value range:                                                                                                                                                                                                                        |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | -  Comma (,), which is the default value                                                                                                                                                                                            |
   |                       |                 |                                                                        | -  Semicolon (;)                                                                                                                                                                                                                    |
   |                       |                 |                                                                        | -  Vertical bar (|)                                                                                                                                                                                                                 |
   |                       |                 |                                                                        | -  Newline character (\\n)                                                                                                                                                                                                          |
   |                       |                 |                                                                        |                                                                                                                                                                                                                                     |
   |                       |                 |                                                                        | Default: **\\n**                                                                                                                                                                                                                    |
   +-----------------------+-----------------+------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _dis_02_0410__request_processingschema:

.. table:: **Table 5** ProcessingSchema

   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                              |
   +==================+=================+=================+==========================================================================================================================================+
   | timestamp_name   | Yes             | String          | Attribute name of the source data timestamp.                                                                                             |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp_type   | Yes             | String          | Type of the source data timestamp.                                                                                                       |
   |                  |                 |                 |                                                                                                                                          |
   |                  |                 |                 | -  String                                                                                                                                |
   |                  |                 |                 | -  Timestamp: 13-bit timestamp of the long type                                                                                          |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp_format | No              | String          | OBS directory generated based on the timestamp format. This parameter is mandatory when the timestamp type of the source data is String. |
   |                  |                 |                 |                                                                                                                                          |
   |                  |                 |                 | Value range:                                                                                                                             |
   |                  |                 |                 |                                                                                                                                          |
   |                  |                 |                 | -  yyyy/MM/dd HH:mm:ss                                                                                                                   |
   |                  |                 |                 | -  MM/dd/yyyy HH:mm:ss                                                                                                                   |
   |                  |                 |                 | -  dd/MM/yyyy HH:mm:ss                                                                                                                   |
   |                  |                 |                 | -  yyyy-MM-dd HH:mm:ss                                                                                                                   |
   |                  |                 |                 | -  MM-dd-yyyy HH:mm:ss                                                                                                                   |
   |                  |                 |                 | -  dd-MM-yyyy HH:mm:ss                                                                                                                   |
   |                  |                 |                 |                                                                                                                                          |
   |                  |                 |                 | Enumeration values:                                                                                                                      |
   |                  |                 |                 |                                                                                                                                          |
   |                  |                 |                 | -  **yyyy/MM/dd HH:mm:ss**                                                                                                               |
   |                  |                 |                 | -  **MM/dd/yyyy HH:mm:ss**                                                                                                               |
   |                  |                 |                 | -  **dd/MM/yyyy HH:mm:ss**                                                                                                               |
   |                  |                 |                 | -  **yyyy-MM-dd HH:mm:ss**                                                                                                               |
   |                  |                 |                 | -  **MM-dd-yyyy HH:mm:ss**                                                                                                               |
   |                  |                 |                 | -  **dd-MM-yyyy HH:mm:ss**                                                                                                               |
   +------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

-  Adding OBS Dump Tasks

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks

      {
        "destination_type" : "OBS",
        "obs_destination_descriptor" : {
          "task_name" : "newtask",
          "consumer_strategy" : "LATEST",
          "agency_name" : "dis_admin_agency",
          "destination_file_type" : "text",
          "obs_bucket_path" : "obsbucket",
          "file_prefix" : "",
          "partition_format" : "yyyy/MM/dd/HH/mm",
          "record_delimiter" : "|",
          "deliver_time_interval" : 30
        }
      }

-  Adding OBS Dump Tasks (The dump file format is Parquet.)

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks

      {
        "destination_type" : "OBS",
        "obs_destination_descriptor" : {
          "task_name" : "newtask",
          "consumer_strategy" : "LATEST",
          "agency_name" : "dis_admin_agency",
          "destination_file_type" : "parquet",
          "obs_bucket_path" : "obsbucket",
          "file_prefix" : "",
          "partition_format" : "yyyy/MM/dd/HH/mm",
          "record_delimiter" : "|",
          "deliver_time_interval" : 30
        }
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
