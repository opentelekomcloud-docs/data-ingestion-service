:original_name: BatchStartTransferTask.html

.. _BatchStartTransferTask:

Starting Dump Tasks in Batches
==============================

Function
--------

This API is used to start dump tasks in batches.

URI
---

POST /v2/{project_id}/streams/{stream_name}/transfer-tasks/action

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+-----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                       |
   +=================+=================+=================+===================================+
   | project_id      | Yes             | String          | Project ID.                       |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | stream_name     | Yes             | String          | Name of the stream to be queried. |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum: **60**                   |
   +-----------------+-----------------+-----------------+-----------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                          | Description                                                                |
   +=================+=================+===============================================================================================+============================================================================+
   | action          | Yes             | String                                                                                        | Dump task operation. Currently, only the following operation is supported: |
   |                 |                 |                                                                                               |                                                                            |
   |                 |                 |                                                                                               | -  start: The dump task is started.                                        |
   |                 |                 |                                                                                               |                                                                            |
   |                 |                 |                                                                                               | Enumeration values:                                                        |
   |                 |                 |                                                                                               |                                                                            |
   |                 |                 |                                                                                               | -  **start**                                                               |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | tasks           | Yes             | Array of :ref:`BatchTransferTask <batchstarttransfertask__request_batchtransfertask>` objects | List of dump tasks to be operated.                                         |
   +-----------------+-----------------+-----------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

.. _batchstarttransfertask__request_batchtransfertask:

.. table:: **Table 3** BatchTransferTask

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   id        Yes       String Dump task ID.
   ========= ========= ====== =============

Response Parameters
-------------------

None

Example Requests
----------------

Starting Dump Tasks in Batches

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks/action

   {
     "action" : "start",
     "tasks" : [ {
       "id" : "9dSu1wfCytSk1aOLxvF"
     } ]
   }

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
