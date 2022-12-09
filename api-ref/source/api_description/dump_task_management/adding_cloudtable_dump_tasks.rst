:original_name: CreateCloudTableTransferTask.html

.. _CreateCloudTableTransferTask:

Adding CloudTable Dump Tasks
============================

Function
--------

This API is used to add CloudTable dump tasks.

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

   +-----------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | Parameter                         | Mandatory       | Type                                                                                                                                | Description                                                                      |
   +===================================+=================+=====================================================================================================================================+==================================================================================+
   | destination_type                  | Yes             | String                                                                                                                              | Dump destination. Possible values:                                               |
   |                                   |                 |                                                                                                                                     |                                                                                  |
   |                                   |                 |                                                                                                                                     | -  OBS: Data is dumped to OBS.                                                   |
   |                                   |                 |                                                                                                                                     | -  MRS: Data is dumped to MRS.                                                   |
   |                                   |                 |                                                                                                                                     | -  DLI: Data is dumped to DLI.                                                   |
   |                                   |                 |                                                                                                                                     | -  CLOUDTABLE: Data is dumped to CloudTable.                                     |
   |                                   |                 |                                                                                                                                     | -  DWS: Data is dumped to DWS.                                                   |
   |                                   |                 |                                                                                                                                     |                                                                                  |
   |                                   |                 |                                                                                                                                     | Default: **NOWHERE**                                                             |
   |                                   |                 |                                                                                                                                     |                                                                                  |
   |                                   |                 |                                                                                                                                     | Enumeration values:                                                              |
   |                                   |                 |                                                                                                                                     |                                                                                  |
   |                                   |                 |                                                                                                                                     | -  **CLOUDTABLE**                                                                |
   +-----------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | cloudtable_destination_descriptor | No              | :ref:`CloudtableDestinationDescriptorRequest <createcloudtabletransfertask__request_cloudtabledestinationdescriptorrequest>` object | Parameter list of the CloudTable to which data in the DIS stream will be dumped. |
   +-----------------------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_cloudtabledestinationdescriptorrequest:

.. table:: **Table 4** CloudtableDestinationDescriptorRequest

   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory       | Type                                                                                          | Description                                                                                                                                                                                                                                                                                                                    |
   +==============================+=================+===============================================================================================+================================================================================================================================================================================================================================================================================================================================+
   | task_name                    | Yes             | String                                                                                        | Name of the dump task. The task name consists of letters, digits, hyphens (-), and underscores (_). It must be a string of 1 to 64 characters.                                                                                                                                                                                 |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | agency_name                  | Yes             | String                                                                                        | Name of the agency created on IAM. DIS uses an agency to access your specified resources. The parameters for creating an agency are as follows:                                                                                                                                                                                |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | -  Agency Type: Cloud service                                                                                                                                                                                                                                                                                                  |
   |                              |                 |                                                                                               | -  Cloud Service: DIS                                                                                                                                                                                                                                                                                                          |
   |                              |                 |                                                                                               | -  Validity Period: unlimited                                                                                                                                                                                                                                                                                                  |
   |                              |                 |                                                                                               | -  Scope: Global service, Project: OBS. Select the Tenant Administrator role for the global service project.                                                                                                                                                                                                                   |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | If agencies have been created, you can obtain available agencies from the agency list by using the "Listing Agencies " API.                                                                                                                                                                                                    |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | This parameter cannot be left blank and the parameter value cannot exceed 64 characters.                                                                                                                                                                                                                                       |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | If there are dump tasks on the console, the system displays a message indicating that an agency will be automatically created. The name of the automatically created agency is dis_admin_agency.                                                                                                                               |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Maximum: **64**                                                                                                                                                                                                                                                                                                                |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | deliver_time_interval        | Yes             | Integer                                                                                       | User-defined interval at which data is imported from the current DIS stream into OBS. If no data is pushed to the DIS stream during the current interval, no dump file package will be generated.                                                                                                                              |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Value range: 30-900                                                                                                                                                                                                                                                                                                            |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Default value: 300                                                                                                                                                                                                                                                                                                             |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Unit: second                                                                                                                                                                                                                                                                                                                   |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Minimum: **30**                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Maximum: **900**                                                                                                                                                                                                                                                                                                               |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Default: **300**                                                                                                                                                                                                                                                                                                               |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consumer_strategy            | No              | String                                                                                        | Offset.                                                                                                                                                                                                                                                                                                                        |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | -  LATEST: Maximum offset, indicating that the latest data will be extracted.                                                                                                                                                                                                                                                  |
   |                              |                 |                                                                                               | -  TRIM_HORIZON: Minimum offset, indicating that the earliest data will be extracted.                                                                                                                                                                                                                                          |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Default value: LATEST                                                                                                                                                                                                                                                                                                          |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Default: **LATEST**                                                                                                                                                                                                                                                                                                            |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Enumeration values:                                                                                                                                                                                                                                                                                                            |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | -  **LATEST**                                                                                                                                                                                                                                                                                                                  |
   |                              |                 |                                                                                               | -  **TRIM_HORIZON**                                                                                                                                                                                                                                                                                                            |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloudtable_cluster_name      | Yes             | String                                                                                        | Name of the CloudTable cluster to which data will be dumped.                                                                                                                                                                                                                                                                   |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | If you choose to dump data to OpenTSDB, OpenTSDB must be enabled for the cluster.                                                                                                                                                                                                                                              |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloudtable_cluster_id        | Yes             | String                                                                                        | ID of the CloudTable cluster to which data will be dumped.                                                                                                                                                                                                                                                                     |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | If you choose to dump data to OpenTSDB, OpenTSDB must be enabled for the cluster.                                                                                                                                                                                                                                              |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloudtable_table_name        | No              | String                                                                                        | HBase table name of the CloudTable cluster to which data will be dumped. The parameter is mandatory when data is dumped to the CloudTable HBase.                                                                                                                                                                               |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloudtable_schema            | No              | :ref:`CloudtableSchema <createcloudtabletransfertask__request_cloudtableschema>` object       | Schema configuration of the CloudTable HBase data. You can set either this parameter or opentsdb_schema, but this parameter is mandatory when data will be dumped to HBase. After this parameter is set, the JSON data in the stream can be converted to another format and then be imported to the CloudTable HBase.          |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | opentsdb_schema              | No              | Array of :ref:`OpenTSDBSchema <createcloudtabletransfertask__request_opentsdbschema>` objects | Schema configuration of the CloudTable OpenTSDB data. You can set either this parameter or opentsdb_schema, but this parameter is mandatory when data will be dumped to OpenTSDB. After this parameter is set, the JSON data in the stream can be converted to another format and then be imported to the CloudTable OpenTSDB. |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cloudtable_row_key_delimiter | No              | String                                                                                        | Delimiter used to separate the user data that generates HBase row keys. Value range: , . \| ; \\ - \_ and ~                                                                                                                                                                                                                    |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Default value: .                                                                                                                                                                                                                                                                                                               |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_backup_bucket_path       | No              | String                                                                                        | Name of the OBS bucket used to back up data that failed to be dumped to CloudTable.                                                                                                                                                                                                                                            |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_file_prefix           | No              | String                                                                                        | Self-defined directory created in the OBS bucket and used to back up data that failed to be dumped to CloudTable. Directory levels are separated by slashes (/) and cannot start with slashes.                                                                                                                                 |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Value range: a string of letters, digits, and underscores (_)                                                                                                                                                                                                                                                                  |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | The maximum length is 50 characters.                                                                                                                                                                                                                                                                                           |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | This parameter is left empty by default.                                                                                                                                                                                                                                                                                       |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | retry_duration               | No              | String                                                                                        | Time duration for DIS to retry if data fails to be dumped to CloudTable. If this threshold is exceeded, the data that fails to be dumped will be backed up to the OBS bucket/backup_file_prefix /cloudtable_error or OBS bucket/backup_file_prefix/opentsdb_error directory.                                                   |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Value range: 0-7,200                                                                                                                                                                                                                                                                                                           |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Unit: second                                                                                                                                                                                                                                                                                                                   |
   |                              |                 |                                                                                               |                                                                                                                                                                                                                                                                                                                                |
   |                              |                 |                                                                                               | Default value: 1,800                                                                                                                                                                                                                                                                                                           |
   +------------------------------+-----------------+-----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_cloudtableschema:

.. table:: **Table 5** CloudtableSchema

   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                          | Description                                                                                 |
   +=================+=================+===============================================================================+=============================================================================================+
   | row_key         | Yes             | Array of :ref:`RowKey <createcloudtabletransfertask__request_rowkey>` objects | HBase rowkey schema used by the CloudTable cluster to convert JSON data into HBase rowkeys. |
   |                 |                 |                                                                               |                                                                                             |
   |                 |                 |                                                                               | Value range: 1-64                                                                           |
   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | columns         | Yes             | Array of :ref:`Column <createcloudtabletransfertask__request_column>` objects | HBase column schema used by the CloudTable cluster to convert JSON data into HBase columns. |
   |                 |                 |                                                                               |                                                                                             |
   |                 |                 |                                                                               | Value range: 1 to 4,096                                                                     |
   +-----------------+-----------------+-------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_rowkey:

.. table:: **Table 6** RowKey

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | value           | Yes             | String          | JSON attribute name, which is used to generate HBase rowkeys for JSON data in the DIS stream. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | JSON attribute type of JSON data in the DIS stream. Value range:                              |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  Bigint                                                                                     |
   |                 |                 |                 | -  Double                                                                                     |
   |                 |                 |                 | -  Boolean                                                                                    |
   |                 |                 |                 | -  Timestamp                                                                                  |
   |                 |                 |                 | -  String                                                                                     |
   |                 |                 |                 | -  Decimal                                                                                    |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | Enumeration values:                                                                           |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | -  **Bigint**                                                                                 |
   |                 |                 |                 | -  **Double**                                                                                 |
   |                 |                 |                 | -  **Boolean**                                                                                |
   |                 |                 |                 | -  **Timestamp**                                                                              |
   |                 |                 |                 | -  **String**                                                                                 |
   |                 |                 |                 | -  **Decimal**                                                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_column:

.. table:: **Table 7** Column

   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                          |
   +====================+=================+=================+======================================================================================================+
   | column_family_name | Yes             | String          | Name of the HBase column family to which data will be dumped.                                        |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | column_name        | Yes             | String          | Name of the HBase column to which data will be dumped.                                               |
   |                    |                 |                 |                                                                                                      |
   |                    |                 |                 | Value range: a string of 1 to 32 characters, consisting of only letters, digits, and underscores (_) |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | value              | Yes             | String          | JSON attribute name, which is used to generate HBase column values for JSON data in the DIS stream.  |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | type               | Yes             | String          | JSON attribute type of JSON data in the DIS stream.                                                  |
   |                    |                 |                 |                                                                                                      |
   |                    |                 |                 | Value range:                                                                                         |
   |                    |                 |                 |                                                                                                      |
   |                    |                 |                 | -  Bigint                                                                                            |
   |                    |                 |                 | -  Double                                                                                            |
   |                    |                 |                 | -  Boolean                                                                                           |
   |                    |                 |                 | -  Timestamp                                                                                         |
   |                    |                 |                 | -  String                                                                                            |
   |                    |                 |                 | -  Decimal                                                                                           |
   |                    |                 |                 |                                                                                                      |
   |                    |                 |                 | Enumeration values:                                                                                  |
   |                    |                 |                 |                                                                                                      |
   |                    |                 |                 | -  **Bigint**                                                                                        |
   |                    |                 |                 | -  **Double**                                                                                        |
   |                    |                 |                 | -  **Boolean**                                                                                       |
   |                    |                 |                 | -  **Timestamp**                                                                                     |
   |                    |                 |                 | -  **String**                                                                                        |
   |                    |                 |                 | -  **Decimal**                                                                                       |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_opentsdbschema:

.. table:: **Table 8** OpenTSDBSchema

   +-----------+-----------+-----------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                          | Description                                                                                                                                                                                     |
   +===========+===========+===============================================================================================+=================================================================================================================================================================================================+
   | metric    | Yes       | Array of :ref:`OpenTSDBMetric <createcloudtabletransfertask__request_opentsdbmetric>` objects | Schema configuration of the OpenTSDB data metric in the CloudTable cluster. After this parameter is set, the JSON data in the stream can be converted to the metric of the OpenTSDB data.       |
   +-----------+-----------+-----------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp | Yes       | :ref:`OpenTSDBTimestamp <createcloudtabletransfertask__request_opentsdbtimestamp>` object     | Schema configuration of the OpenTSDB data timestamp in the CloudTable cluster. After this parameter is set, the JSON data in the stream can be converted to the timestamp of the OpenTSDB data. |
   +-----------+-----------+-----------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value     | Yes       | :ref:`OpenTSDBValue <createcloudtabletransfertask__request_opentsdbvalue>` object             | Schema configuration of the OpenTSDB data value in the CloudTable cluster. After this parameter is set, the JSON data in the stream can be converted to the value of the OpenTSDB data.         |
   +-----------+-----------+-----------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags      | Yes       | Array of :ref:`OpenTSDBTags <createcloudtabletransfertask__request_opentsdbtags>` objects     | Schema configuration of the OpenTSDB data tags in the CloudTable cluster. After this parameter is set, the JSON data in the stream can be converted to the tags of the OpenTSDB data.           |
   +-----------+-----------+-----------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_opentsdbmetric:

.. table:: **Table 9** OpenTSDBMetric

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================+
   | type            | Yes             | String          | -  When type is set to Constant, the value of metric is the value of Value.                                                                                     |
   |                 |                 |                 | -  When value is set to String, the value of metric is the value of the JSON attribute of the user data in the stream.                                          |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | Enumeration values:                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | -  **Constant**                                                                                                                                                 |
   |                 |                 |                 | -  **String**                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Constant value or JSON attribute name of the user data in the stream. This value is 1 to 32 characters long. Only letters, digits, and periods (.) are allowed. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_opentsdbtimestamp:

.. table:: **Table 10** OpenTSDBTimestamp

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================================================================================================+
   | type            | Yes             | String          | -  When type is set to Timestamp, the value type of the JSON attribute of the user data in the stream is Timestamp, and the timestamp of OpenTSDB can be generated without converting the data format.                         |
   |                 |                 |                 | -  When type is set to String, the value type of the JSON attribute of the user data in the stream is Date, and the timestamp of OpenTSDB can be generated only after the data format is converted.                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | JSON attribute name of the user data in the stream. Value range: a string of 1 to 32 characters, consisting of only letters, digits, and underscores (_)                                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | format          | Yes             | String          | This parameter is mandatory when type is set to String. When the value type of the JSON attribute of the user data in the stream is Date, format is required to convert the data format to generate the timestamp of OpenTSDB. |
   |                 |                 |                 |                                                                                                                                                                                                                                |
   |                 |                 |                 | Value range:                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                |
   |                 |                 |                 | -  yyyy/MM/dd HH:mm:ss                                                                                                                                                                                                         |
   |                 |                 |                 | -  MM/dd/yyyy HH:mm:ss                                                                                                                                                                                                         |
   |                 |                 |                 | -  dd/MM/yyyy HH:mm:ss                                                                                                                                                                                                         |
   |                 |                 |                 | -  yyyy-MM-dd HH:mm:ss                                                                                                                                                                                                         |
   |                 |                 |                 | -  MM-dd-yyyy HH:mm:ss                                                                                                                                                                                                         |
   |                 |                 |                 | -  dd-MM-yyyy HH:mm:ss                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                |
   |                 |                 |                 | -  **yyyy/MM/dd HH:mm:ss**                                                                                                                                                                                                     |
   |                 |                 |                 | -  **MM/dd/yyyy HH:mm:ss**                                                                                                                                                                                                     |
   |                 |                 |                 | -  **dd/MM/yyyy HH:mm:ss**                                                                                                                                                                                                     |
   |                 |                 |                 | -  **yyyy-MM-dd HH:mm:ss**                                                                                                                                                                                                     |
   |                 |                 |                 | -  **MM-dd-yyyy HH:mm:ss**                                                                                                                                                                                                     |
   |                 |                 |                 | -  **dd-MM-yyyy HH:mm:ss**                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_opentsdbvalue:

.. table:: **Table 11** OpenTSDBValue

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================+
   | type            | Yes             | String          | Dump destination. Possible values: Value range:                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  Bigint                                                                                                                                                                  |
   |                 |                 |                 | -  Double                                                                                                                                                                  |
   |                 |                 |                 | -  Boolean                                                                                                                                                                 |
   |                 |                 |                 | -  Timestamp                                                                                                                                                               |
   |                 |                 |                 | -  String                                                                                                                                                                  |
   |                 |                 |                 | -  Decimal                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Constant value or JSON attribute name of the user data in the stream. Value range: a string of 1 to 32 characters, consisting of only letters, digits, and underscores (_) |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createcloudtabletransfertask__request_opentsdbtags:

.. table:: **Table 12** OpenTSDBTags

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================+
   | name            | Yes             | String          | Tag name of the OpenTSDB data that stores the data in the stream. Value range: a string of 1 to 32 characters, consisting of only letters, digits, and underscores (_)     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Type name of the JSON attribute of the user data in the stream.                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Value range:                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  Bigint                                                                                                                                                                  |
   |                 |                 |                 | -  Double                                                                                                                                                                  |
   |                 |                 |                 | -  Boolean                                                                                                                                                                 |
   |                 |                 |                 | -  Timestamp                                                                                                                                                               |
   |                 |                 |                 | -  String                                                                                                                                                                  |
   |                 |                 |                 | -  Decimal                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Constant value or JSON attribute name of the user data in the stream. Value range: a string of 1 to 32 characters, consisting of only letters, digits, and underscores (_) |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

-  Adding CloudTable HBase Dump Tasks

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks

      {
        "destination_type" : "CLOUDTABLE",
        "cloudtable_destination_descriptor" : {
          "task_name" : "hbasetask",
          "consumer_strategy" : "TRIM_HORIZON",
          "agency_name" : "dis_admin_agency",
          "cloudtable_cluster_name" : "cloudtablecluster",
          "cloudtable_cluster_id" : "b8c095e2-db5f-4732-8a1d-eacd662e35dc",
          "cloudtable_table_name" : "cloudtabletable",
          "cloudtable_row_key_delimiter" : "|",
          "retry_duration" : 1800,
          "obs_backup_bucket_path" : "obsbackupbucket",
          "backup_file_prefix" : "",
          "cloudtable_schema" : {
            "row_key" : [ {
              "value" : "datavalue",
              "type" : "String"
            } ],
            "columns" : [ {
              "column_family_name" : "cfname1",
              "column_name" : "ID",
              "value" : "datavalue1",
              "type" : "String"
            }, {
              "column_family_name" : "cfname2",
              "column_name" : "VALUE",
              "value" : "datavalue2",
              "type" : "String"
            } ]
          }
        }
      }

-  Adding CloudTable OpenTSDB Dump Tasks

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks

      {
        "destination_type" : "CLOUDTABLE",
        "cloudtable_destination_descriptor" : {
          "task_name" : "opentsdbtask",
          "consumer_strategy" : "LATEST",
          "agency_name" : "dis_admin_agency",
          "cloudtable_cluster_name" : "cloudtablecluster",
          "cloudtable_cluster_id" : "b8c095e2-db5f-4732-8a1d-eacd662e35dc",
          "retry_duration" : 1800,
          "obs_backup_bucket_path" : "obsbackupbucket",
          "backup_file_prefix" : "",
          "opentsdb_schema" : [ {
            "metric" : [ {
              "type" : "Constant",
              "value" : "age"
            } ],
            "timestamp" : {
              "value" : "date",
              "type" : "String",
              "format" : "yyyy/MM/dd HH:mm:ss"
            },
            "value" : {
              "value" : "value",
              "type" : "Bigint"
            },
            "tags" : [ {
              "name" : "name",
              "value" : "name",
              "type" : "Bigint"
            } ]
          } ]
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
