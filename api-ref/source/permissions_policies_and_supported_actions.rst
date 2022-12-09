:original_name: en-us_topic_0000001079240698.html

.. _en-us_topic_0000001079240698:

Permissions Policies and Supported Actions
==========================================

This chapter describes fine-grained permissions management for your DIS. If your cloud account does not need individual IAM users, then you may skip over this chapter.

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign permissions policies to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on DIS based on the permissions.

You can grant users permissions by using roles and policies. Roles are a type of coarse-grained authorization mechanism provided by IAM that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

Note:

Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all of the permissions required to call all APIs, but IAM users must have the required permissions specifically assigned. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user queries MRS clusters using an API, the user must have been granted permissions that allow the **dis:streams:list** action.

**Supported Actions**

DIS provides system-defined policies that can be directly used in IAM. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

· Permission: A statement in a policy that allows or denies certain operations.

· APIs: REST APIs that can be called in a custom policy.

· Action: Specific operations that are allowed or denied.

· IAM or enterprise projects: Type of projects for which an action will take effect. Policies that contain actions supporting both IAM and enterprise projects can be assigned to user groups and take effect in both IAM and Enterprise Management. Policies that only contain actions for IAM projects can be used and only take effect for IAM.

Note:

The check mark (Y) indicates that an action takes effect. The cross mark (x) indicates that an action does not take effect.

:ref:`Table 1 <en-us_topic_0000001079240698__table538416112711>` lists the actions that can be defined in custom policies of DIS. All actions listed in the following table support both Project and Enterprise Project.

.. _en-us_topic_0000001079240698__table538416112711:

.. table:: **Table 1** Permissions policies and supported actions

   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Permissions                                      | APIs                                                              | Actions                   | Project     | Enterprise Project |
   +==================================================+===================================================================+===========================+=============+====================+
   | Creating a consumer app                          | POST /v2/{project_id}/apps                                        | dis:apps:create           | Y           | x                  |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting an app                                  | DELETE /v2/{project_id}/apps/{app_name}                           | dis:apps:delete           | Y           | x                  |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying apps                                    | GET                                                               | dis:apps:list             | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/apps                                             |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying app details                             | GET                                                               | dis:apps:get              | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/apps/{app_name}                                  |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying the app consumption status              | GET                                                               | dis:appState:get          | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/apps/{app}/streams/{stream_name}                 |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying all events of a user in pagination mode | GET                                                               | dis:events:list           | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v1/{project_id}/events                                           |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Creating a subscription                          | POST                                                              | dis:eventEnumSubs:create  | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v1/{project_id}/event-subs                                       |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a subscription                          | DELETE                                                            | dis:eventEnumSubs:delete  | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v1/{project_id}/event-subs/{sub_id}                              |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Modifying a subscription                         | PUT                                                               | dis:eventEnumSubs:update  | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v1/{project_id}/event-subs/{sub_id}                              |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying all subscriptions of a user             | GET                                                               | dis:eventEnumSubs:list    | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v1/{project_id}/event-subs                                       |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Adding a permission policy                       | POST                                                              | dis:streamPolicies:create | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{streamName}/policies                    |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying permission policies                     | GET                                                               | dis:streamPolicies:list   | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{streamName}/policies                    |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a permission policy of a stream         | DELETE                                                            | dis:streamPolicies:delete | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{streamName}/policies                    |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying details of a stream                     | GET                                                               | dis:streams:get           | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{streamName}                             |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Creating a stream                                | POST                                                              | dis:streams:create        | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams                                          |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a Stream                                | DELETE                                                            | dis:streams:delete        | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}                            |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying streams                                 | GET                                                               | dis:streams:list          | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams                                          |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Updating stream information                      | PUT                                                               | dis:streams:update        | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}/update                     |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Creating a dump task                             | POST                                                              | dis:transferTasks:create  | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}/transfer-tasks             |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Updating a dump task                             | PUT                                                               | dis:transferTasks:update  | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}/transfer-tasks             |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying dump tasks                              | GET                                                               | dis:transferTasks:list    | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}/transfer-tasks             |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying details of a dump task                  | GET                                                               | dis:transferTasks:get     | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}/transfer-tasks/{task_name} |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a dump task                             | DELETE                                                            | dis:transferTasks:delete  | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/streams/{stream_name}/transfer-tasks/{task_name} |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Uploading Data to a DIS Stream                   | POST                                                              | dis:records:write         | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/records                                          |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Obtaining a data cursor                          | GET                                                               | dis:records:readCursor    | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/cursors                                          |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Downloading data from a DIS stream               | GET                                                               | dis:records:read          | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/records                                          |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Adding a checkpoint                              | POST                                                              | dis:checkpoints:commit    | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/checkpoints                                      |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying checkpoint details                      | GET                                                               | dis:checkpoints:get       | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/checkpoints                                      |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a checkpoint                            | DELETE                                                            | dis:checkpoints:delete    | Y           | Y                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /v2/{project_id}/checkpoints                                      |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Filtering streams by tag                         | POST                                                              | dis:tagResources:list     | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /{project_id}/{resource_type}/resource_instances/action           |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Adding or deleting resource tags in batches      | POST                                                              | dis:tagResources:update   | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /{project_id}/{resource_type}/{resource_id}/tags/action           |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Adding a Tag to a Specified Stream               | POST                                                              | dis:tagResources:create   | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /{project_id}/{resource_type}/{resource_id}/tags                  |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a tag of a specified stream             | DELETE                                                            | dis:tagResources:delete   | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /{project_id}/{resource_type}/{resource_id}/tags/{key}            |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying all tags of a specified region          | GET                                                               | dis:tags:list             | Y           | x                  |
   |                                                  |                                                                   |                           |             |                    |
   |                                                  | /{project_id}/{resource_type}/tags                                |                           |             |                    |
   +--------------------------------------------------+-------------------------------------------------------------------+---------------------------+-------------+--------------------+

Note: For the actions not listed :ref:`Table 1 <en-us_topic_0000001079240698__table538416112711>`, for example, viewing app quota (/{projectId}/quotas) and viewing DIS resource statistics on the homepage (/v1/{projectId}/statistics), configure system-defined policy **DIS User**, **DIS ReadOnlyAccess**, **DIS CommonOperations**, or **DIS FullAccess** for users.
