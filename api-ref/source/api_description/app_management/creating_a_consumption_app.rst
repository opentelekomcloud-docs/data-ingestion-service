:original_name: CreateApp.html

.. _CreateApp:

Creating a Consumption App
==========================

Function
--------

This API is used to create a consumption app.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

POST /v2/{project_id}/apps

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
   | X-Auth-Token    | Yes             | String          | User token                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                            |
   +=================+=================+=================+========================================================================================================================+
   | app_name        | Yes             | String          | Name of the consumer application to be created.                                                                        |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | The application name contains 1 to 200 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed. |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | Minimum: **1**                                                                                                         |
   |                 |                 |                 |                                                                                                                        |
   |                 |                 |                 | Maximum: **200**                                                                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Creating a Consumption App

.. code-block:: text

   POST https://{Endpoint}/v2/{project_id}/apps

   {
     "app_name" : "newapp"
   }

Example Responses
-----------------

None

Status Codes
------------

=========== ===============
Status Code Description
=========== ===============
201         Normal response
=========== ===============

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
