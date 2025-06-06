:original_name: DeleteTag.html

.. _DeleteTag:

Deleting Tags of a Specified Stream
===================================

Function
--------

This API is used to delete tags of a specified stream.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

DELETE /v2/{project_id}/stream/{stream_id}/tags/{key}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   stream_id  Yes       String Stream ID
   key        Yes       String Tag key
   ========== ========= ====== ===========

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

None

Example Requests
----------------

Deleting Tags of a Specified Stream

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/stream/{stream_id}/tags/{key}

Example Responses
-----------------

None

Status Codes
------------

=========== ===============
Status Code Description
=========== ===============
204         Normal response
=========== ===============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
