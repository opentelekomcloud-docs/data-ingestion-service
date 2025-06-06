:original_name: ShowStreamTags.html

.. _ShowStreamTags:

Querying Tags of a Specified Stream
===================================

Function
--------

This API is used to query tags of a specified stream.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

GET /v2/{project_id}/stream/{stream_id}/tags

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   stream_id  Yes       String Stream ID
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

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+------------------------------------------------------------+-------------+
   | Parameter | Type                                                       | Description |
   +===========+============================================================+=============+
   | tags      | Array of :ref:`Tag <showstreamtags__response_tag>` objects | Tags        |
   +-----------+------------------------------------------------------------+-------------+

.. _showstreamtags__response_tag:

.. table:: **Table 4** Tag

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================+
   | key                   | String                | Tag key.                                                                                                                                        |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  It cannot be left blank.                                                                                                                     |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  It must be unique for each resource.                                                                                                         |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  It can contain uppercase and lowercase letters, digits, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF).              |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Minimum: **1**                                                                                                                                  |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Maximum: **36**                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Value.                                                                                                                                          |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  It can contain a maximum of 43 characters.                                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  It can contain uppercase and lowercase letters, digits, periods (.), hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  It can only contain digits, letters, hyphens (-), and underscores (_).                                                                       |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Minimum: **0**                                                                                                                                  |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | Maximum: **43**                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Tags of a Specified Stream

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/stream/{stream_id}/tags

Example Responses
-----------------

**Status code: 200**

Response body of the stream tag information.

.. code-block::

   {
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value3"
     } ]
   }

Status Codes
------------

=========== ============================================
Status Code Description
=========== ============================================
200         Response body of the stream tag information.
=========== ============================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
