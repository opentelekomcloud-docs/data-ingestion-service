:original_name: ShowStreamTags.html

.. _ShowStreamTags:

Querying Tags of Specified Streams
==================================

Function
--------

This API is used to query tags of specified streams.

URI
---

GET /v2/{project_id}/stream/{stream_id}/tags

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   stream_id  Yes       String Stream ID.
   ========== ========= ====== ===========

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

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+------------------------------------------------------------+-------------+
   | Parameter | Type                                                       | Description |
   +===========+============================================================+=============+
   | tags      | Array of :ref:`Tag <showstreamtags__response_tag>` objects | Label list. |
   +-----------+------------------------------------------------------------+-------------+

.. _showstreamtags__response_tag:

.. table:: **Table 4** Tag

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                |
   +=======================+=======================+============================================================================================+
   | key                   | String                | Key.                                                                                       |
   |                       |                       |                                                                                            |
   |                       |                       | -  This field cannot be left blank.                                                        |
   |                       |                       |                                                                                            |
   |                       |                       | -  The key value of a resource must be unique.                                             |
   |                       |                       |                                                                                            |
   |                       |                       | -  Character set: A-Z, a-z, 0-9, '-', '_', and Unicode characters (\\u4E00-\\u9FFF).       |
   |                       |                       |                                                                                            |
   |                       |                       | Minimum: **1**                                                                             |
   |                       |                       |                                                                                            |
   |                       |                       | Maximum: **36**                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+
   | value                 | String                | Value.                                                                                     |
   |                       |                       |                                                                                            |
   |                       |                       | -  The value contains a maximum of 43 characters.                                          |
   |                       |                       |                                                                                            |
   |                       |                       | -  Character set: A-Z, a-z, 0-9, '. ', '-', '_', and Unicode characters (\\u4E00-\\u9FFF). |
   |                       |                       |                                                                                            |
   |                       |                       | -  The value can contain only digits, letters, hyphens (-), and underscores (_).           |
   |                       |                       |                                                                                            |
   |                       |                       | Minimum: **0**                                                                             |
   |                       |                       |                                                                                            |
   |                       |                       | Maximum: **43**                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------+

Example Requests
----------------

This API is used to query tags of specified streams.

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
