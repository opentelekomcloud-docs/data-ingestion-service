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

:ref:`Table 1 <en-us_topic_0000001079240698__table397013152131>`\ lists the actions that can be defined in custom policies of DIS. All actions listed in the following table support both Project and Enterprise Project.

.. _en-us_topic_0000001079240698__table397013152131:

.. table:: **Table 1** Permissions policies and supported actions

   +-------------------------------------------+-----------------------+------------------+--------------+
   | **Operation**                             | **DIS Administrator** | **DIS Operator** | **DIS User** |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Creating streams                          | Y                     | Y                | x            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Deleting streams                          | Y                     | Y                | x            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying the stream list                  | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying stream details                   | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Viewing stream monitoring information     | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying partition monitoring information | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Obtaining stream consumption information  | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Changing partition quantity               | Y                     | Y                | x            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Uploading data                            | Y                     | x                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Obtaining data cursors                    | Y                     | x                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Downloading data                          | Y                     | x                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Creating applications                     | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying application details              | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying the application list             | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Deleting applications                     | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Adding checkpoints                        | Y                     | x                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying checkpoints                      | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Deleting checkpoints                      | Y                     | x                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Creating dump tasks                       | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying dump task details                | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Querying the dump task list               | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
   | Deleting dump tasks                       | Y                     | Y                | Y            |
   +-------------------------------------------+-----------------------+------------------+--------------+
