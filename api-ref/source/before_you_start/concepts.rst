:original_name: dis_02_0515.html

.. _dis_02_0515:

Concepts
========

-  Domain

   A domain is created upon successful registration. The domain has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The domain is a payment entity and should not be used directly to perform routine management. For security purposes, create users and grant them permissions for routine management.

-  User

   A user is created using an accounta domain to use cloud services. Each user has its own identity credentials (password and access keys).

   The account, username, and password will be required for API authentication.

-  Project

   Projects group and isolate resources (including compute, storage, and network resources) across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. For more refined access control, create subprojects under a project and create resources in the subprojects. Users can then be assigned permissions to access only specific resources in the subprojects.


   .. figure:: /_static/images/en-us_image_0000001782070012.png
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model

-  Checkpoint

   When an application consumes data, the latest SN of the consumed data is recorded as a checkpoint. When the data is reconsumed, the consumption can be continued based on this checkpoint.

-  Application

   Multiple applications can consume data in the same stream. The consumed data in the stream by each application is recorded by checkpoints generated for each application.
