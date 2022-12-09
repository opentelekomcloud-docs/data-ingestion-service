:original_name: ListPolicies.html

.. _ListPolicies:

Querying Permission Policies
============================

Function
--------

This API is used to query permission policies of specified streams.

URI
---

GET /v2/{project_id}/streams/{stream_name}/policies

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+---------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                           |
   +=================+=================+=================+=======================================+
   | project_id      | Yes             | String          | Project ID.                           |
   +-----------------+-----------------+-----------------+---------------------------------------+
   | stream_name     | Yes             | String          | Name of the DIS stream to be created. |
   |                 |                 |                 |                                       |
   |                 |                 |                 | Maximum: **60**                       |
   +-----------------+-----------------+-----------------+---------------------------------------+

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

   +-----------+------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter | Type                                                                         | Description                                |
   +===========+==============================================================================+============================================+
   | stream_id | String                                                                       | Unique ID of the stream.                   |
   +-----------+------------------------------------------------------------------------------+--------------------------------------------+
   | rules     | Array of :ref:`PrincipalRule <listpolicies__response_principalrule>` objects | List of authorization information records. |
   +-----------+------------------------------------------------------------------------------+--------------------------------------------+

.. _listpolicies__response_principalrule:

.. table:: **Table 4** PrincipalRule

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                 |
   +=======================+=======================+=============================================================================================================================================================================================+
   | principal             | String                | ID of the authorized user.                                                                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | principal_name        | String                | Name of the authorized user.                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | If the permission is granted to all sub-users of a tenant, the format is domainName.*. If the permission is granted to a specified sub-user of a tenant, the format is domainName.userName. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action_type           | String                | Authorization operation type.                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | -  putRecords: Upload data.                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | -  getRecords: Download data.                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | Enumeration values:                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | -  **putRecords**                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | -  **getRecords**                                                                                                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | effect                | String                | Authorization impact type.                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | -  accept: The authorization operation is allowed.                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | Enumeration values:                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                             |
   |                       |                       | -  **accept**                                                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Permission Policies

.. code-block:: text

   GET https://{Endpoint}/v2/{project_id}/streams/{stream_name}/policies

Example Responses
-----------------

**Status code: 200**

Normal response.

.. code-block::

   {
     "streamId" : "CiFdELMr0401K9GGZlp",
     "rules" : [ {
       "action_type" : "putRecords",
       "principal" : "3b3f237122574xxxxb74482ae11005ba.*",
       "principal_name" : "anotherusername",
       "effect" : "accept"
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
