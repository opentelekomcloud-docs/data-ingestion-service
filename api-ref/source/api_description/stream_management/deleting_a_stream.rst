:original_name: DeleteStream.html

.. _DeleteStream:

Deleting a Stream
=================

Function
--------

This API is used to delete a specified stream.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

DELETE /v2/{project_id}/streams/{stream_name}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                      |
   +=================+=================+=================+==================================+
   | project_id      | Yes             | String          | Project ID                       |
   +-----------------+-----------------+-----------------+----------------------------------+
   | stream_name     | Yes             | String          | Name of the stream to be deleted |
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

None

Example Requests
----------------

Deleting a Stream

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/streams/{stream_name}

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
