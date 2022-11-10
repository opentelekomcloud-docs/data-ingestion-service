:original_name: DeleteTransferTask.html

.. _DeleteTransferTask:

Deleting Dump Tasks
===================

Function
--------

This API is used to delete dump tasks.

URI
---

DELETE /v2/{project_id}/streams/{stream_name}/transfer-tasks/{task_name}

.. table:: **Table 1** Path parameters

   =========== ========= ====== ====================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ====================================
   project_id  Yes       String Project ID.
   stream_name Yes       String Name of the stream.
   task_name   Yes       String Name of the dump task to be deleted.
   =========== ========= ====== ====================================

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

Response Parameters
-------------------

None

Example Requests
----------------

Deleting Dump Tasks

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/streams/{stream_name}/transfer-tasks/{task_name}

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
