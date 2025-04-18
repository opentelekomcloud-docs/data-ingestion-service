:original_name: ListTags.html

.. _ListTags:

Querying All Tags of a Specified Region
=======================================

Function
--------

This API is used to query all tags of a specified region.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

GET /v2/{project_id}/stream/tags

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
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

   +-----------+--------------------------------------------------------+-------------+
   | Parameter | Type                                                   | Description |
   +===========+========================================================+=============+
   | tags      | Array of :ref:`Tags <listtags__response_tags>` objects | Tags        |
   +-----------+--------------------------------------------------------+-------------+

.. _listtags__response_tags:

.. table:: **Table 4** Tags

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                        |
   +=======================+=======================+====================================================================================================================================+
   | key                   | String                | Tag key.                                                                                                                           |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  It cannot be left blank.                                                                                                        |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  It must be unique for each resource.                                                                                            |
   |                       |                       |                                                                                                                                    |
   |                       |                       | -  It can contain uppercase and lowercase letters, digits, hyphens (-), underscores (_), and Unicode characters (\\u4E00-\\u9FFF). |
   |                       |                       |                                                                                                                                    |
   |                       |                       | Maximum: **36**                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+
   | values                | Array of strings      | Tag values.                                                                                                                        |
   |                       |                       |                                                                                                                                    |
   |                       |                       | If the value list is empty, this parameter indicates **any_value**. The values are in the OR relationship.                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying All Tags of a Specified Region

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/stream/tags

Example Responses
-----------------

**Status code: 200**

Response body of the tag set

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

=========== ============================
Status Code Description
=========== ============================
200         Response body of the tag set
=========== ============================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
