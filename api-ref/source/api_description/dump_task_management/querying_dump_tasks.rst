:original_name: ListTransferTasks.html

.. _ListTransferTasks:

Querying Dump Tasks
===================

Function
--------

This API is used to query dump tasks.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

GET /v2/{project_id}/streams/{stream_name}/transfer-tasks

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                      |
   +=================+=================+=================+==================================+
   | project_id      | Yes             | String          | Project ID                       |
   +-----------------+-----------------+-----------------+----------------------------------+
   | stream_name     | Yes             | String          | Name of the stream to be queried |
   |                 |                 |                 |                                  |
   |                 |                 |                 | Maximum: **60**                  |
   +-----------------+-----------------+-----------------+----------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Response body parameters

   +--------------+---------------------------------------------------------------------------------+--------------------------------------------------+
   | Parameter    | Type                                                                            | Description                                      |
   +==============+=================================================================================+==================================================+
   | total_number | Integer                                                                         | Total number of dump tasks                       |
   +--------------+---------------------------------------------------------------------------------+--------------------------------------------------+
   | quota        | Integer                                                                         | Maximum number of dump tasks that can be created |
   +--------------+---------------------------------------------------------------------------------+--------------------------------------------------+
   | tasks        | Array of :ref:`TransferTask <listtransfertasks__response_transfertask>` objects | List of dump tasks                               |
   +--------------+---------------------------------------------------------------------------------+--------------------------------------------------+

.. _listtransfertasks__response_transfertask:

.. table:: **Table 4** TransferTask

   +-------------------------+-----------------------+--------------------------------------------------+
   | Parameter               | Type                  | Description                                      |
   +=========================+=======================+==================================================+
   | task_name               | String                | Name of the dump task                            |
   +-------------------------+-----------------------+--------------------------------------------------+
   | state                   | String                | Dump task status.                                |
   |                         |                       |                                                  |
   |                         |                       | -  **ERROR**: An error occurs.                   |
   |                         |                       |                                                  |
   |                         |                       | -  **STARTING**: The task is starting.           |
   |                         |                       |                                                  |
   |                         |                       | -  **PAUSED**: The task has been stopped.        |
   |                         |                       |                                                  |
   |                         |                       | -  RUNNING: The task is being executed.          |
   |                         |                       |                                                  |
   |                         |                       | -  **DELETE**: The task has been deleted.        |
   |                         |                       |                                                  |
   |                         |                       | -  **ABNORMAL**: The task is abnormal.           |
   |                         |                       |                                                  |
   |                         |                       | Enumeration values:                              |
   |                         |                       |                                                  |
   |                         |                       | -  **ERROR**                                     |
   |                         |                       |                                                  |
   |                         |                       | -  **STARTING**                                  |
   |                         |                       |                                                  |
   |                         |                       | -  **PAUSED**                                    |
   |                         |                       |                                                  |
   |                         |                       | -  **RUNNING**                                   |
   |                         |                       |                                                  |
   |                         |                       | -  **DELETE**                                    |
   |                         |                       |                                                  |
   |                         |                       | -  **ABNORMAL**                                  |
   +-------------------------+-----------------------+--------------------------------------------------+
   | destination_type        | String                | Type of the dump task.                           |
   |                         |                       |                                                  |
   |                         |                       | -  **OBS**: Data is dumped to OBS.               |
   |                         |                       |                                                  |
   |                         |                       | -  **MRS**: Data is dumped to MRS.               |
   |                         |                       |                                                  |
   |                         |                       | -  **DLI**: Data is dumped to DLI.               |
   |                         |                       |                                                  |
   |                         |                       | -  **CLOUDTABLE**: Data is dumped to CloudTable. |
   |                         |                       |                                                  |
   |                         |                       | -  **DWS**: Data is dumped to DWS.               |
   |                         |                       |                                                  |
   |                         |                       | Enumeration values:                              |
   |                         |                       |                                                  |
   |                         |                       | -  **OBS**                                       |
   |                         |                       |                                                  |
   |                         |                       | -  **MRS**                                       |
   |                         |                       |                                                  |
   |                         |                       | -  **DLI**                                       |
   |                         |                       |                                                  |
   |                         |                       | -  **CLOUDTABLE**                                |
   |                         |                       |                                                  |
   |                         |                       | -  **DWS**                                       |
   +-------------------------+-----------------------+--------------------------------------------------+
   | create_time             | Long                  | Time when the dump task is created               |
   +-------------------------+-----------------------+--------------------------------------------------+
   | last_transfer_timestamp | Long                  | Latest dump time of the dump task                |
   +-------------------------+-----------------------+--------------------------------------------------+

Example Requests
----------------

Querying Dump Tasks

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks

Example Responses
-----------------

**Status code: 200**

Normal response

.. code-block::

   {
     "tasks" : [ {
       "task_id" : "As805BudhcH1lDs6gbn",
       "destination_type" : "OBS",
       "task_name" : "newtask",
       "create_time" : 1606554932552,
       "state" : "RUNNING",
       "last_transfer_timestamp" : 1606984428612
     } ],
     "total_number" : 1
   }

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
