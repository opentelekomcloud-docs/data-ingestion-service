:original_name: CreatePolicies.html

.. _CreatePolicies:

Adding Permission Policies
==========================

Function
--------

This API is used to add permission policies to specified streams.

URI
---

POST /v2/{project_id}/streams/{stream_name}/policies

.. table:: **Table 1** Path parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | project_id      | Yes             | String          | Project ID.                                                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | stream_name     | Yes             | String          | Name of the stream for which you want to add an authorization policy. |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | Maximum: **64**                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================+
   | stream_id       | Yes             | String          | Unique ID of the stream.                                                                                                                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | principal_name  | Yes             | String          | Authorized user.                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | If the permission is granted to a specified tenant, the format is domainName.*. If the permission is granted to a specified sub-user of a tenant, the format is domainName.userName. |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | Multiple accounts can be added and separated by commas (,), for example, domainName1.userName1,domainName2.userName2.                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action_type     | Yes             | String          | Authorization operation type.                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  putRecords: Upload data.                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  getRecords: Download data.                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **putRecords**                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **getRecords**                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | effect          | Yes             | String          | Authorization impact type.                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  accept: The authorization operation is allowed.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                      |
   |                 |                 |                 | -  **accept**                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

-  Adding Permission Policies for Tenants

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/policies

      {
        "stream_id" : "CiFdELMr0401K9GGZlp",
        "principal_name" : "domainname1",
        "action_type" : "putRecords",
        "effect" : "accept"
      }

-  Adding Permission Policies for Sub-users

   .. code-block:: text

      POST https://{Endpoint}/v2/{project_id}/streams/{stream_name}/policies

      {
        "stream_id" : "CiFdELMr0401K9GGZlp",
        "principal_name" : "domainname1.username1",
        "action_type" : "putRecords",
        "effect" : "accept"
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
