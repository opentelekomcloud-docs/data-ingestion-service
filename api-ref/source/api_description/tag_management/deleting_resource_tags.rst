:original_name: BatchDeleteTags.html

.. _BatchDeleteTags:

Deleting Resource Tags
======================

Function
--------

This API is used to delete resource tags (stream tags). This API is idempotent. If the deleted tag does not exist, the deletion is considered successful by default. The tag character set range is not verified during tag deletion. When you delete tags, the tags structure cannot be missing, and the key cannot be left blank or be an empty string.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

POST /v2/{project_id}/stream/{stream_id}/tags/action

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------+--------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                       | Description                                                  |
   +=================+=================+============================================================+==============================================================+
   | action          | Yes             | String                                                     | Operation to be performed. The value can be **delete** only. |
   |                 |                 |                                                            |                                                              |
   |                 |                 |                                                            | -  **delete**: batch deletion                                |
   |                 |                 |                                                            |                                                              |
   |                 |                 |                                                            | Enumeration values:                                          |
   |                 |                 |                                                            |                                                              |
   |                 |                 |                                                            | -  **delete**                                                |
   +-----------------+-----------------+------------------------------------------------------------+--------------------------------------------------------------+
   | tags            | Yes             | Array of :ref:`Tag <batchdeletetags__request_tag>` objects | Tags                                                         |
   +-----------------+-----------------+------------------------------------------------------------+--------------------------------------------------------------+

.. _batchdeletetags__request_tag:

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

Deleting Resource Tags

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/stream/{stream_id}/tags/action

   {
     "action" : "delete",
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value3"
     } ]
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
