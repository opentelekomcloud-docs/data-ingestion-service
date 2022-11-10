:original_name: DeleteApp.html

.. _DeleteApp:

Deleting Apps
=============

Function
--------

This API is used to delete apps.

URI
---

DELETE /v2/{project_id}/apps/{app_name}

.. table:: **Table 1** Path parameters

   ========== ========= ====== ==============================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==============================
   project_id Yes       String Project ID.
   app_name   Yes       String Name of the app to be deleted.
   ========== ========= ====== ==============================

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

None

Example Requests
----------------

Deleting Apps

.. code-block:: text

   DELETE https://{Endpoint}/v2/{project_id}/apps/{app_name}

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
