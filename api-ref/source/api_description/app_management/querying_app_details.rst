:original_name: ShowApp.html

.. _ShowApp:

Querying App Details
====================

Function
--------

This API is used to query app details.

URI
---

GET /v2/{project_id}/apps/{app_name}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ==============================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==============================
   project_id Yes       String Project ID.
   app_name   Yes       String Name of the app to be queried.
   ========== ========= ====== ==============================

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------------------------+------------------+------------------------------------------------+
   | Parameter                      | Type             | Description                                    |
   +================================+==================+================================================+
   | app_name                       | String           | Name of the app.                               |
   +--------------------------------+------------------+------------------------------------------------+
   | app_id                         | String           | Unique identifier of the app.                  |
   +--------------------------------+------------------+------------------------------------------------+
   | create_time                    | Long             | Time when the app is created, in milliseconds. |
   +--------------------------------+------------------+------------------------------------------------+
   | commit_checkpoint_stream_names | Array of strings | List of associated streams.                    |
   +--------------------------------+------------------+------------------------------------------------+

Example Requests
----------------

Querying App Details

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/apps/{app_name}

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "app_id" : "bd6IPpvgiIflQPMpi9M",
     "app_name" : "newstream",
     "create_time" : 1593569685875,
     "commit_checkpoint_stream_names" : [ "newstream" ]
   }

Status Codes
------------

=========== ================
Status Code Description
=========== ================
200         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
