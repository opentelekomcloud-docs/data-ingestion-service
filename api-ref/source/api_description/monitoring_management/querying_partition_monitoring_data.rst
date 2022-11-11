:original_name: ShowPartitionMetrics.html

.. _ShowPartitionMetrics:

Querying Partition Monitoring Data
==================================

Function
--------

This API is used to query the monitoring data of a specified partition of a stream.

URI
---

GET /v2/{project_id}/streams/{stream_name}/partitions/{partition_id}/metrics

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID.                                                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | stream_name     | Yes             | String          | Name of the stream.                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | Maximum: **60**                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | partition_id    | Yes             | String          | Partition No. The value can be in either of the following formats:                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  shardId-0000000000                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | -  0                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                            |
   |                 |                 |                 | For example, if a stream has three partitions, the partition identifiers are 0, 1, and 2, or shardId-0000000000, shardId-0000000001, and shardId-0000000002, respectively. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================+
   | label           | No              | String          | Partition monitoring metric. (Either label or label_list must be specified. If both label_list and label are specified, label_list prevails.)                                        |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  total_put_bytes_per_partition: total input traffic of the partition (byte)                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  total_get_bytes_per_partition: total output traffic of the partition (byte)                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  total_put_records_per_partition: total number of input records of the partition                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  total_get_records_per_partition: total number of output records of the partition                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **total_put_bytes_per_partition**                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **total_get_bytes_per_partition**                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **total_put_records_per_partition**                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **total_get_records_per_partition**                                                                                                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | label_list      | No              | String          | List of labels separated by commas (,) to query multiple labels in batches. (Either label or label_list must be specified. If both label_list and label exist, label_list prevails.) |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time      | Yes             | Long            | Monitoring start time, which is a 10-digit timestamp.                                                                                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time        | Yes             | String          | Monitoring end time, which is a 10-digit timestamp.                                                                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+----------------------------------------------------------------+--------------+
   | Parameter | Type                                                           | Description  |
   +===========+================================================================+==============+
   | metrics   | :ref:`Metrics <showpartitionmetrics__response_metrics>` object | Data object. |
   +-----------+----------------------------------------------------------------+--------------+

.. _showpartitionmetrics__response_metrics:

.. table:: **Table 5** Metrics

   +------------+------------------------------------------------------------------------------+------------------+
   | Parameter  | Type                                                                         | Description      |
   +============+==============================================================================+==================+
   | dataPoints | Array of :ref:`DataPoint <showpartitionmetrics__response_datapoint>` objects | Monitoring data. |
   +------------+------------------------------------------------------------------------------+------------------+
   | label      | String                                                                       | Metric.          |
   +------------+------------------------------------------------------------------------------+------------------+

.. _showpartitionmetrics__response_datapoint:

.. table:: **Table 6** DataPoint

   ========= ==== ================================================
   Parameter Type Description
   ========= ==== ================================================
   timestamp Long Timestamp.
   value     Long Monitoring value corresponding to the timestamp.
   ========= ==== ================================================

Example Requests
----------------

Querying Partition Monitoring Data

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/streams/{stream_name}/partitions/{partition_id}/metrics

Example Responses
-----------------

None

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
