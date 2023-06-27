:original_name: BatchCreateTags.html

.. _BatchCreateTags:

Adding Resource Tags in Batches
===============================

Function
--------

This API is used to add resource tags (such as stream tags) in batches. The API is idempotent. When you are creating tags, if there are duplicate keys in the request body, an error is reported. During tag creation, duplicate keys are not allowed. If a key exists in the database, its value will be overwritten.

URI
---

POST /v2/{project_id}/stream/{stream_id}/tags/action

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   stream_id  Yes       String Stream ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                          |
   |                 |                 |                 | The token can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                       | Description                                                                                  |
   +=================+=================+============================================================+==============================================================================================+
   | action          | Yes             | String                                                     | Operation to be performed. The value can only be **create**, which indicates batch creation. |
   |                 |                 |                                                            |                                                                                              |
   |                 |                 |                                                            | Enumeration values:                                                                          |
   |                 |                 |                                                            |                                                                                              |
   |                 |                 |                                                            | -  **create**                                                                                |
   +-----------------+-----------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------+
   | tags            | Yes             | Array of :ref:`Tag <batchcreatetags__request_tag>` objects | Tag list.                                                                                    |
   +-----------------+-----------------+------------------------------------------------------------+----------------------------------------------------------------------------------------------+

.. _batchcreatetags__request_tag:

.. table:: **Table 4** Tag

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================+
   | key             | No              | String          | Key                                                                                                                                             |
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
   | value           | No              | String          | Value                                                                                                                                           |
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

Adding Resource Tags in Batches

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/stream/{stream_id}/tags/action

   {
     "action" : "create",
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

=========== ================
Status Code Description
=========== ================
204         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
