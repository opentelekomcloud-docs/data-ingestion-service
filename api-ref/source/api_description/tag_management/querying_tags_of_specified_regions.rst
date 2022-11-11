:original_name: ListTags.html

.. _ListTags:

Querying Tags of Specified Regions
==================================

Function
--------

This API is used to query all tags of specified regions.

URI
---

GET /v2/{project_id}/stream/tags

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
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

   +-----------+--------------------------------------------------------+-------------+
   | Parameter | Type                                                   | Description |
   +===========+========================================================+=============+
   | tags      | Array of :ref:`Tags <listtags__response_tags>` objects | Tag list.   |
   +-----------+--------------------------------------------------------+-------------+

.. _listtags__response_tags:

.. table:: **Table 4** Tags

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                          |
   +=======================+=======================+======================================================================================+
   | key                   | String                | Key.                                                                                 |
   |                       |                       |                                                                                      |
   |                       |                       | -  This field cannot be left blank.                                                  |
   |                       |                       |                                                                                      |
   |                       |                       | -  The key value of a resource must be unique.                                       |
   |                       |                       |                                                                                      |
   |                       |                       | -  Character set: A-Z, a-z, 0-9, '-', '_', and Unicode characters (\\u4E00-\\u9FFF). |
   |                       |                       |                                                                                      |
   |                       |                       | Maximum: **36**                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | values                | Array of strings      | Tag value list.                                                                      |
   |                       |                       |                                                                                      |
   |                       |                       | If values are null, it indicates any_value. The relationship between values is OR.   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Tags of Specified Regions

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/stream/tags

Example Responses
-----------------

**Status code: 200**

Response body of the tag set.

.. code-block::

   {
     "tags" : [ {
       "key" : "key1",
       "values" : [ "value1", "value2" ]
     }, {
       "key" : "key2",
       "values" : [ "value1", "value2" ]
     } ]
   }

Status Codes
------------

=========== =============================
Status Code Description
=========== =============================
200         Response body of the tag set.
=========== =============================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
