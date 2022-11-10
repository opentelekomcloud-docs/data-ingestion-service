:original_name: CreateApp.html

.. _CreateApp:

Creating Consumption Apps
=========================

Function
--------

This API is used to create consumption apps.

URI
---

POST /v2/{project_id}/apps

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                     |
   +=================+=================+=================+=================================================================================================================+
   | app_name        | Yes             | String          | Unique identifier of the consumer application to be created.                                                    |
   |                 |                 |                 |                                                                                                                 |
   |                 |                 |                 | The application name contains 1 to 200 characters, including letters, digits, underscores (_), and hyphens (-). |
   |                 |                 |                 |                                                                                                                 |
   |                 |                 |                 | Minimum: **1**                                                                                                  |
   |                 |                 |                 |                                                                                                                 |
   |                 |                 |                 | Maximum: **200**                                                                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Creating Consumption Apps

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

=========== ================
Status Code Description
=========== ================
201         Normal response.
=========== ================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
