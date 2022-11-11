:original_name: UpdateStream.html

.. _UpdateStream:

Updating Stream Information
===========================

Function
--------

This API is used to update the information about specified streams.

URI
---

PUT /v3/{project_id}/streams/{stream_name}

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                      |
   +=============+===========+========+==================================================================+
   | project_id  | Yes       | String | Project ID.                                                      |
   +-------------+-----------+--------+------------------------------------------------------------------+
   | stream_name | Yes       | String | Name of the stream whose partition quantity needs to be changed. |
   +-------------+-----------+--------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Mandatory       | Type            | Description                                                                                                                                                          |
   +================================+=================+=================+======================================================================================================================================================================+
   | stream_name                    | Yes             | String          | Name of the stream to be updated.                                                                                                                                    |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Maximum: **64**                                                                                                                                                      |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_duration                  | No              | Integer         | Period of time for which data is retained in the stream. Value range: 24-72 Unit: hour Default value: 24 If this parameter is left blank, the default value is used. |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Maximum: **168**                                                                                                                                                     |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Default: **24**                                                                                                                                                      |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_type                      | No              | String          | Source data type.                                                                                                                                                    |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  BLOB: a collection of binary data stored as a single entity in a database management system.                                                                      |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  JSON: an open-standard file format that uses human-readable text to transmit data objects consisting of attribute-value pairs and array data types.               |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  CSV: a simple text format for storing tabular data in a plain text file. Commas are used as delimiters.                                                           |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Default value: BLOB                                                                                                                                                  |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Enumeration values:                                                                                                                                                  |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  **BLOB**                                                                                                                                                          |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  **JSON**                                                                                                                                                          |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  **CSV**                                                                                                                                                           |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_schema                    | No              | String          | Source data structure that defines JSON and CSV formats. It is described in the syntax of the Avro schema.                                                           |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_enabled             | No              | Boolean         | Specifies whether to enable auto scaling.                                                                                                                            |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  true: auto scaling is enabled.                                                                                                                                    |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  false: auto scaling is disabled. This function is disabled by default.                                                                                            |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Default: **false**                                                                                                                                                   |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Enumeration values:                                                                                                                                                  |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  **true**                                                                                                                                                          |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | -  **false**                                                                                                                                                         |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_min_partition_count | No              | Long            | Minimum number of partitions for automatic scale-down when auto scaling is enabled.                                                                                  |
   |                                |                 |                 |                                                                                                                                                                      |
   |                                |                 |                 | Minimum: **1**                                                                                                                                                       |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | auto_scale_max_partition_count | No              | Long            | Maximum number of partitions for automatic scale-up when auto scaling is enabled.                                                                                    |
   +--------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

-  Updating Lifecycles of Streams

   .. code-block:: text

      PUT https://{Endpoint}/v3/{project_id}/streams/{stream_name}

      {
        "stream_name" : "stz_test",
        "data_duration" : 48
      }

-  Updating Stream Types

   .. code-block:: text

      PUT https://{Endpoint}/v3/{project_id}/streams/{stream_name}

      {
        "stream_name" : "stz_test",
        "data_type" : "JSON"
      }

Example Responses
-----------------

None

Status Codes
------------

=========== ================
Status Code Description
=========== ================
204         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
