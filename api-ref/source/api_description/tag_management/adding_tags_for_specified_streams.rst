:original_name: CreateTag.html

.. _CreateTag:

Adding Tags for Specified Streams
=================================

Function
--------

This API is used to add tags to specified streams.

URI
---

POST /v2/{project_id}/stream/{stream_id}/tags

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+-----------------+
   | Parameter       | Mandatory       | Type            | Description     |
   +=================+=================+=================+=================+
   | project_id      | Yes             | String          | Project ID.     |
   +-----------------+-----------------+-----------------+-----------------+
   | stream_id       | Yes             | String          | Stream ID.      |
   |                 |                 |                 |                 |
   |                 |                 |                 | Maximum: **60** |
   +-----------------+-----------------+-----------------+-----------------+

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

.. table:: **Table 3** Request body parameters

   +-----------+-----------+--------------------------------------------+---------------+
   | Parameter | Mandatory | Type                                       | Description   |
   +===========+===========+============================================+===============+
   | tag       | Yes       | :ref:`Tag <createtag__request_tag>` object | Label object. |
   +-----------+-----------+--------------------------------------------+---------------+

.. _createtag__request_tag:

.. table:: **Table 4** Tag

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                |
   +=================+=================+=================+============================================================================================+
   | key             | No              | String          | Key.                                                                                       |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  This field cannot be left blank.                                                        |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  The key value of a resource must be unique.                                             |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  Character set: A-Z, a-z, 0-9, '-', '_', and Unicode characters (\\u4E00-\\u9FFF).       |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                             |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Maximum: **36**                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value.                                                                                     |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  The value contains a maximum of 43 characters.                                          |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  Character set: A-Z, a-z, 0-9, '. ', '-', '_', and Unicode characters (\\u4E00-\\u9FFF). |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | -  The value can contain only digits, letters, hyphens (-), and underscores (_).           |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Minimum: **0**                                                                             |
   |                 |                 |                 |                                                                                            |
   |                 |                 |                 | Maximum: **43**                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Adding Tags for Specified Streams

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

=========== ================
Status Code Description
=========== ================
204         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
