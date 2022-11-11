:original_name: CreateMrsTransferTask.html

.. _CreateMrsTransferTask:

Adding MRS Dump Tasks
=====================

Function
--------

This API is used to add MRS dump tasks.

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

   +----------------------------+-----------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | Parameter                  | Mandatory       | Type                                                                                                           | Description                                                               |
   +============================+=================+================================================================================================================+===========================================================================+
   | destination_type           | Yes             | String                                                                                                         | Dump destination. Possible values:                                        |
   |                            |                 |                                                                                                                |                                                                           |
   |                            |                 |                                                                                                                | -  OBS: Data is dumped to OBS.                                            |
   |                            |                 |                                                                                                                | -  MRS: Data is dumped to MRS.                                            |
   |                            |                 |                                                                                                                | -  DLI: Data is dumped to DLI.                                            |
   |                            |                 |                                                                                                                | -  CLOUDTABLE: Data is dumped to CloudTable.                              |
   |                            |                 |                                                                                                                | -  DWS: Data is dumped to DWS.                                            |
   |                            |                 |                                                                                                                |                                                                           |
   |                            |                 |                                                                                                                | Default: **NOWHERE**                                                      |
   |                            |                 |                                                                                                                |                                                                           |
   |                            |                 |                                                                                                                | Enumeration values:                                                       |
   |                            |                 |                                                                                                                |                                                                           |
   |                            |                 |                                                                                                                | -  **MRS**                                                                |
   +----------------------------+-----------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | mrs_destination_descriptor | No              | :ref:`MRSDestinationDescriptorRequest <createmrstransfertask__request_mrsdestinationdescriptorrequest>` object | Parameter list of the MRS to which data in the DIS stream will be dumped. |
   +----------------------------+-----------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+

.. _createmrstransfertask__request_mrsdestinationdescriptorrequest:

.. table:: **Table 4** MRSDestinationDescriptorRequest

   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                                                                                         |
   +=======================+=================+=================+=====================================================================================================================================================================================================================+
   | task_name             | Yes             | String          | Name of the dump task. The task name consists of letters, digits, hyphens (-), and underscores (_). It must be a string of 1 to 64 characters.                                                                      |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agency_name           | Yes             | String          | Name of the agency created on IAM. DIS uses an agency to access your specified resources. The parameters for creating an agency are as follows:                                                                     |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | -  Agency Type: Cloud service                                                                                                                                                                                       |
   |                       |                 |                 | -  Cloud Service: DIS                                                                                                                                                                                               |
   |                       |                 |                 | -  Validity Period: unlimited                                                                                                                                                                                       |
   |                       |                 |                 | -  Scope: Global service, Project: OBS. Select the Tenant Administrator role for the global service project.                                                                                                        |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | If agencies have been created, you can obtain available agencies from the agency list by using the "Listing Agencies " API.                                                                                         |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | This parameter cannot be left blank and the parameter value cannot exceed 64 characters.                                                                                                                            |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | If there are dump tasks on the console, the system displays a message indicating that an agency will be automatically created. The name of the automatically created agency is dis_admin_agency.                    |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Maximum: **64**                                                                                                                                                                                                     |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | deliver_time_interval | Yes             | Integer         | User-defined interval at which data is imported from the current DIS stream into OBS. If no data is pushed to the DIS stream during the current interval, no dump file package will be generated.                   |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Value range: 30-900                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Default value: 300                                                                                                                                                                                                  |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Unit: second                                                                                                                                                                                                        |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Minimum: **30**                                                                                                                                                                                                     |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Maximum: **900**                                                                                                                                                                                                    |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Default: **300**                                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consumer_strategy     | No              | String          | Offset.                                                                                                                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | -  LATEST: Maximum offset, indicating that the latest data will be extracted.                                                                                                                                       |
   |                       |                 |                 | -  TRIM_HORIZON: Minimum offset, indicating that the earliest data will be extracted.                                                                                                                               |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Default value: LATEST                                                                                                                                                                                               |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Default: **LATEST**                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Enumeration values:                                                                                                                                                                                                 |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | -  **LATEST**                                                                                                                                                                                                       |
   |                       |                 |                 | -  **TRIM_HORIZON**                                                                                                                                                                                                 |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mrs_cluster_name      | Yes             | String          | Name of the MRS cluster to which data in the DIS stream will be dumped.                                                                                                                                             |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Note:                                                                                                                                                                                                               |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Only MRS clusters with non-Kerberos authentication are supported.                                                                                                                                                   |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mrs_cluster_id        | Yes             | String          | ID of the MRS cluster to which data in the DIS stream will be dumped.                                                                                                                                               |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mrs_hdfs_path         | Yes             | String          | Hadoop Distributed File System (HDFS) path of the MRS cluster to which data in the DIS stream will be dumped.                                                                                                       |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_prefix           | No              | String          | Self-defined directory created in the OBS bucket and used to temporarily store data in the DIS stream. Directory levels are separated by slashes (/) and cannot start with slashes.                                 |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | The value can contain a maximum of 50 characters, including letters, digits, underscores (_), and slashes (/).                                                                                                      |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | This parameter is left empty by default.                                                                                                                                                                            |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hdfs_prefix_folder    | No              | String          | Directory to store files that will be dumped to the chosen MRS cluster. Different directory levels are separated by slash (/). Value range: a string of 0 to 50 characters This parameter is left empty by default. |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_bucket_path       | Yes             | String          | Name of the OBS bucket used to temporarily store data in the DIS stream.                                                                                                                                            |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | retry_duration        | No              | String          | Time duration for DIS to retry if data fails to be dumped. If the retry time exceeds the value of this parameter, the data that fails to be dumped is backed up to the OBS bucket/file_prefix/mrs_error directory.  |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Value range: 0-7,200                                                                                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Unit: second                                                                                                                                                                                                        |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | Default value: 1,800                                                                                                                                                                                                |
   |                       |                 |                 |                                                                                                                                                                                                                     |
   |                       |                 |                 | If this parameter is set to 0, DIS does not retry when the dump fails.                                                                                                                                              |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Adding MRS Dump Tasks

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks

   {
     "destination_type" : "MRS",
     "mrs_destination_descriptor" : {
       "task_name" : "mrstask",
       "consumer_strategy" : "LATEST",
       "agency_name" : "dis_admin_agency",
       "destination_file_type" : "text",
       "mrs_cluster_id" : "f8123fa6-99f1-4ed9-83f4-c827c7277d41",
       "mrs_cluster_name" : "mrscluster",
       "mrs_hdfs_path" : "/user",
       "obs_bucket_path" : "obsbucket",
       "file_prefix" : "",
       "hdfs_prefix_folder" : "",
       "deliver_time_interval" : 30,
       "retry_duration" : 1800
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
