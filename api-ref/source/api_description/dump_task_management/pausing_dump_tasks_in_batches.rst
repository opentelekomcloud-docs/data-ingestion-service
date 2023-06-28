:original_name: BatchStopTransferTask.html

.. _BatchStopTransferTask:

Pausing Dump Tasks in Batches
=============================

Function
--------

This API is used to pause dump tasks in batches.

URI
---

POST /v2/{project_id}/streams/{stream_name}/transfer-tasks/action

.. table:: **Table 1** Path Parameters

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

   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                         | Description                                                                                |
   +=================+=================+==============================================================================================+============================================================================================+
   | action          | Yes             | String                                                                                       | Dump task operation. The value can only be **stop**, which indicates stopping a dump task. |
   |                 |                 |                                                                                              |                                                                                            |
   |                 |                 |                                                                                              | Enumeration values:                                                                        |
   |                 |                 |                                                                                              |                                                                                            |
   |                 |                 |                                                                                              | -  **stop**                                                                                |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | tasks           | Yes             | Array of :ref:`BatchTransferTask <batchstoptransfertask__request_batchtransfertask>` objects | List of dump tasks to be paused.                                                           |
   +-----------------+-----------------+----------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _batchstoptransfertask__request_batchtransfertask:

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

Pausing Dump Tasks in Batches

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks/action

   {
     "action" : "stop",
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
