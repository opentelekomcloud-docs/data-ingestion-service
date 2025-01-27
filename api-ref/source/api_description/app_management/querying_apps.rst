:original_name: ListApp.html

.. _ListApp:

Querying Apps
=============

Function
--------

This API is used to query apps.

Calling Method
--------------

For details, see :ref:`Calling APIs <dis_02_0400>`.

URI
---

GET /v2/{project_id}/apps

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | limit           | No              | Integer         | Maximum number of apps to list in a single API call                                           |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | Minimum: **1**                                                                                |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | Maximum: **100**                                                                              |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | Default: **10**                                                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | start_app_name  | No              | String          | Name of the app to start the list with. The returned app list does not contain this app name. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | stream_name     | No              | String          | Name of the stream whose apps will be returned                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | It can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+---------------------------------------------------------------------------------+--------------------------------------------------------+
   | Parameter             | Type                                                                            | Description                                            |
   +=======================+=================================================================================+========================================================+
   | has_more_app          | Boolean                                                                         | Whether there are more matching consumer applications. |
   |                       |                                                                                 |                                                        |
   |                       |                                                                                 | -  **true**: yes                                       |
   |                       |                                                                                 |                                                        |
   |                       |                                                                                 | -  **false**: no                                       |
   +-----------------------+---------------------------------------------------------------------------------+--------------------------------------------------------+
   | apps                  | Array of :ref:`DescribeAppResult <listapp__response_describeappresult>` objects | AppEntry list that meets the current request.          |
   +-----------------------+---------------------------------------------------------------------------------+--------------------------------------------------------+
   | total_number          | Integer                                                                         | Total number of apps that meet criteria                |
   +-----------------------+---------------------------------------------------------------------------------+--------------------------------------------------------+

.. _listapp__response_describeappresult:

.. table:: **Table 5** DescribeAppResult

   +--------------------------------+------------------+-----------------------------------------------+
   | Parameter                      | Type             | Description                                   |
   +================================+==================+===============================================+
   | app_name                       | String           | Name of the app                               |
   +--------------------------------+------------------+-----------------------------------------------+
   | app_id                         | String           | Unique identifier of the app                  |
   +--------------------------------+------------------+-----------------------------------------------+
   | create_time                    | Long             | Time when the app is created, in milliseconds |
   +--------------------------------+------------------+-----------------------------------------------+
   | commit_checkpoint_stream_names | Array of strings | List of associated streams                    |
   +--------------------------------+------------------+-----------------------------------------------+

Example Requests
----------------

Querying Apps

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/apps

Example Responses
-----------------

**Status code: 200**

Normal response

.. code-block::

   {
     "total_number" : 1,
     "apps" : [ {
       "app_id" : "bd6IPpvgiIflQPMpi9M",
       "app_name" : "newstream",
       "create_time" : 1593569685875
     } ],
     "has_more_app" : true
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         Normal response
400         Invalid Parameters
404         Application not found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
