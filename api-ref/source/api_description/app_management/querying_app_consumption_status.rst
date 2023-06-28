:original_name: ShowConsumerState.html

.. _ShowConsumerState:

Querying App Consumption Status
===============================

Function
--------

This API is used to query the consumption status of apps.

URI
---

GET /v2/{project_id}/apps/{app_name}/streams/{stream_name}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------------------------+
   | Parameter       | Mandatory       | Type            | Description                       |
   +=================+=================+=================+===================================+
   | project_id      | Yes             | String          | Project ID.                       |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | app_name        | Yes             | String          | Name of the app to be queried.    |
   +-----------------+-----------------+-----------------+-----------------------------------+
   | stream_name     | Yes             | String          | Name of the stream to be queried. |
   |                 |                 |                 |                                   |
   |                 |                 |                 | Maximum: **60**                   |
   +-----------------+-----------------+-----------------+-----------------------------------+

.. table:: **Table 2** Query Parameters

   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                              |
   +====================+=================+=================+==========================================================================================================================================+
   | limit              | No              | Integer         | Max. number of partitions to list in a single API call. The minimum value is 1 and the maximum value is 1,000. The default value is 100. |
   |                    |                 |                 |                                                                                                                                          |
   |                    |                 |                 | Minimum: **1**                                                                                                                           |
   |                    |                 |                 |                                                                                                                                          |
   |                    |                 |                 | Maximum: **1000**                                                                                                                        |
   |                    |                 |                 |                                                                                                                                          |
   |                    |                 |                 | Default: **100**                                                                                                                         |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | start_partition_id | No              | String          | Name of the partition to start the partition list with. The returned partition list does not contain this partition.                     |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | checkpoint_type    | Yes             | String          | Type of the checkpoint                                                                                                                   |
   |                    |                 |                 |                                                                                                                                          |
   |                    |                 |                 | -  **LAST_READ**: Only sequence numbers are recorded in databases.                                                                       |
   |                    |                 |                 |                                                                                                                                          |
   |                    |                 |                 | Enumeration values:                                                                                                                      |
   |                    |                 |                 |                                                                                                                                          |
   |                    |                 |                 | -  **LAST_READ**                                                                                                                         |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response body parameters

   +----------------------------+-----------------------+-------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                   |
   +============================+=======================+===============================================================================+
   | has_more                   | String                | Specify whether there are more matching DIS streams to list. Possible values: |
   |                            |                       |                                                                               |
   |                            |                       | -  true: yes                                                                  |
   |                            |                       | -  false: no                                                                  |
   |                            |                       |                                                                               |
   |                            |                       | Default: **false**.                                                           |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------+
   | stream_name                | String                | Stream Name                                                                   |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------+
   | app_name                   | String                | App Name                                                                      |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------+
   | partition_consuming_states | Array of strings      | partition consuming state list                                                |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------+

.. table:: **Table 5** Partition_consuming_states

   +-----------------------+-----------------------+-------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                 |
   +=======================+=======================+=============================================================+
   | partition_id          | String                | Partition Id                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | sequence_number       | String                | Partition Sequence Number                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | latest_offset         | Long                  | partition data latest offset                                |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | earliest_offset       | Long                  | partition data earliest offset                              |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | metadata              | String                | user-defined metadata information                           |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | checkpoint_type       | String                | Type of the checkpoint.                                     |
   |                       |                       |                                                             |
   |                       |                       | LAST_READ: Only sequence numbers are recorded in databases. |
   |                       |                       |                                                             |
   |                       |                       | Enumeration values:                                         |
   |                       |                       |                                                             |
   |                       |                       | LAST_READ                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | status                | String                | Partition Status:                                           |
   |                       |                       |                                                             |
   |                       |                       | CREATING                                                    |
   |                       |                       |                                                             |
   |                       |                       | ACTIVE                                                      |
   |                       |                       |                                                             |
   |                       |                       | DELETED                                                     |
   |                       |                       |                                                             |
   |                       |                       | EXPIRED                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------+

Example Requests
----------------

Querying App Consumption Status

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/apps/{app_name}/streams/{stream_name}

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "stream_name" : "newstream",
     "app_name" : "newapp",
     "partition_consuming_states" : [ {
       "partition_id" : "2",
       "sequence_number" : "485",
       "latest_offset" : "1000",
       "earliest_offset" : "10",
       "checkpoint_type" : "LAST_READ"
     } ]
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
