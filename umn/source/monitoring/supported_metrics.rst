:original_name: dis_01_0131.html

.. _dis_01_0131:

Supported Metrics
=================

Description
-----------

This section describes metrics reported by DIS to Cloud Eye as well as their namespaces and dimensions. You can use Cloud Eye to query metric information generated for DIS.

Namespace
---------

SYS.DAYU

Metrics
-------

:ref:`Table 1 <dis_01_0131__table77137321225>` lists the DIS metrics.

.. _dis_01_0131__table77137321225:

.. table:: **Table 1** DIS metrics

   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Metric Name                                  | Description                                                                                       | Value Range | Monitored Object | Monitoring Period (Raw Data) |
   +==============================================+===================================================================================================+=============+==================+==============================+
   | Total Input Traffic                          | The amount of data uploaded through a stream during a specific period.                            | >= 0        | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: byte/s                                                                                      |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Total Output Traffic                         | The amount of data downloaded through a stream during a specific period.                          | >= 0        | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: byte/s                                                                                      |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Total Input Records                          | The number of records uploaded through a stream during a specific period.                         | >= 0        | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: count/s                                                                                     |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Total Output Records                         | The number of records downloaded through a stream during a specific period.                       | >= 0        | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: count/s                                                                                     |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Successful Upload Requests                   | The number of successful requests for uploading data through a stream during a specific period.   | >= 0        | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: count/s                                                                                     |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Successful Download Requests                 | The number of successful requests for downloading data through a stream during a specific period. | >= 0        | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: count/s                                                                                     |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Average Processing Time of Upload Requests   | Average upload request delay of a stream during a specific period.                                | 0 to 50 ms  | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: ms                                                                                          |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Average Processing Time of Download Requests | Average download request delay of a stream during a specific period.                              | 0 to 50 ms  | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: ms                                                                                          |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Throttled Upload Requests                    | The number of rejected upload requests due to flow control.                                       | 0 to 1      | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: count/s                                                                                     |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+
   | Throttled Download Requests                  | The number of rejected download requests due to flow control.                                     | 0 to 1      | Stream           | 1 minute                     |
   |                                              |                                                                                                   |             |                  |                              |
   |                                              | Unit: count/s                                                                                     |             |                  |                              |
   +----------------------------------------------+---------------------------------------------------------------------------------------------------+-------------+------------------+------------------------------+

Dimension
---------

========= ========================
Key       Value
========= ========================
stream_id Real-time data ingestion
========= ========================
