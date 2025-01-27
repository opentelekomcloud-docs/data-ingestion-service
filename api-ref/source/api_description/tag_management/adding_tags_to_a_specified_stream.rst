:original_name: CreateTag.html

.. _CreateTag:

Adding Tags to a Specified Stream
=================================

Function
--------

This API is used to add tags to a specified stream.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

POST /v2/{project_id}/stream/{stream_id}/tags

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | project_id      | Yes             | String          | Project ID      |
   +-----------------+-----------------+-----------------+-----------------+
   | stream_id       | Yes             | String          | Stream ID       |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **60** |
   +-----------------+-----------------+-----------------+-----------------+

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

.. table:: **Table 3** Request body parameters

   +-----------+-----------+--------------------------------------------+-------------+
   | Parameter | Mandatory | Type                                       | Description |
   +===========+===========+============================================+=============+
   | tag       | Yes       | :ref:`Tag <createtag__request_tag>` object | Tag object  |
   +-----------+-----------+--------------------------------------------+-------------+

.. _createtag__request_tag:

.. table:: **Table 4** Tag

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================+
   | key             | No              | String          | Tag key.                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It cannot be left blank.                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It must be unique for each resource.                                                                                                         |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It can contain uppercase and lowercase letters, digits, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF).              |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Minimum: **1**                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Maximum: **36**                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value.                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It can contain a maximum of 43 characters.                                                                                                   |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It can contain uppercase and lowercase letters, digits, periods (.), hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | -  It can only contain digits, letters, hyphens (-), and underscores (_).                                                                       |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Minimum: **0**                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                 |
   |                 |                 |                 | Maximum: **43**                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Adding Tags to a Specified Stream

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/stream/{stream_id}/tags

   {
     "tag" : {
       "key" : "key",
       "value" : "value"
     }
   }

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
