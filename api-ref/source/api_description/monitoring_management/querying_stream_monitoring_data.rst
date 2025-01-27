:original_name: ShowStreamMetrics.html

.. _ShowStreamMetrics:

Querying Stream Monitoring Data
===============================

Function
--------

This API is used to query the monitoring data of a specified stream.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

GET /v2/{project_id}/streams/{stream_name}/metrics

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | project_id      | Yes             | String          | Project ID      |
   +-----------------+-----------------+-----------------+-----------------+
   | stream_name     | Yes             | String          | Stream name     |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **60** |
   +-----------------+-----------------+-----------------+-----------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================================+
   | label           | No              | String          | Stream monitoring metric (Either **label** or **label_list** must be specified. If both **label_list** and **label** exist, **label_list** is used.)                                                    |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_bytes_per_stream**: total input traffic (byte)                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_bytes_per_stream**: total output traffic (byte)                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_records_per_stream**: total input records                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_records_per_stream**: total output records                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_req_latency**: average processing time (milliseconds) of upload requests                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_req_latency**: average processing time (milliseconds) of download requests                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_req_suc_per_stream**: number of successful upload requests                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_req_suc_per_stream**: number of successful download requests                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **traffic_controll_put**: number of rejected upload requests due to flow control                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **traffic_controll_get**: number of rejected download requests due to flow control                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_bytes_per_stream**                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_bytes_per_stream**                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_records_per_stream**                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_records_per_stream**                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_req_latency**                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_req_latency**                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_put_req_suc_per_stream**                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **total_get_req_suc_per_stream**                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **traffic_control_put**                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                         |
   |                 |                 |                 | -  **traffic_control_get**                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | label_list      | No              | String          | List of labels separated by commas (,) to query multiple labels in batches. (Either **label** or **label_list** must be specified. If both **label_list** and **label** exist, **label_list** is used.) |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time      | Yes             | Long            | Monitoring start time, which is a 10-digit timestamp                                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time        | Yes             | Long            | Monitoring end time, which is a 10-digit timestamp                                                                                                                                                      |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------+-----------------------------------------------------------------------+--------------------------------+
   | Parameter    | Type                                                                  | Description                    |
   +==============+=======================================================================+================================+
   | metrics      | :ref:`Metrics <showstreammetrics__response_metrics>` object           | Data object                    |
   +--------------+-----------------------------------------------------------------------+--------------------------------+
   | metrics_list | Array of :ref:`Metrics <showstreammetrics__response_metrics>` objects | List of monitored data objects |
   +--------------+-----------------------------------------------------------------------+--------------------------------+

.. _showstreammetrics__response_metrics:

.. table:: **Table 5** Metrics

   +------------+---------------------------------------------------------------------------+-------------------+
   | Parameter  | Type                                                                      | Description       |
   +============+===========================================================================+===================+
   | dataPoints | Array of :ref:`DataPoint <showstreammetrics__response_datapoint>` objects | Monitoring data   |
   +------------+---------------------------------------------------------------------------+-------------------+
   | label      | String                                                                    | Monitoring metric |
   +------------+---------------------------------------------------------------------------+-------------------+

.. _showstreammetrics__response_datapoint:

.. table:: **Table 6** DataPoint

   ========= ==== ===============================================
   Parameter Type Description
   ========= ==== ===============================================
   timestamp Long Timestamp
   value     Long Monitoring value corresponding to the timestamp
   ========= ==== ===============================================

Example Requests
----------------

Querying Stream Monitoring Data

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/streams/{stream_name}/metrics

Example Responses
-----------------

None

Status Codes
------------

=========== ===============
Status Code Description
=========== ===============
200         Normal response
=========== ===============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
