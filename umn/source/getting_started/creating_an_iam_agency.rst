:original_name: dis_01_0605.html

.. _dis_01_0605:

Creating an IAM Agency
======================

Introduction
------------

If you choose to dump data from DIS to OBS, create an IAM agency that grants DIS permissions to access OBS.


Creating an IAM Agency
----------------------

#. Log in to the management console.

#. Click **Service List**. Under **Management & Deployment**, select **Identify and Access Management**.

#. Select **Agencies** in the navigation tree pane, and click **Create Agency**.


   .. figure:: /_static/images/en-us_image_0124319023.jpg
      :alt: **Figure 1** Creating an IAM agency

      **Figure 1** Creating an IAM agency

#. Configure agency parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0124319248.jpg
      :alt: **Figure 2** Configuring agency parameters

      **Figure 2** Configuring agency parameters

   .. table:: **Table 1** Agency parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                |
      +===================================+============================================================================================================================================================+
      | Agency Name                       | Name of the agency to be created. The value of this parameter is 1 to 64 characters long and cannot be left unspecified.                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency Type                       | Type of the agency to be created. This parameter must be set to **Cloud service**.                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cloud Service                     | Click **Select** next to **Cloud Service**. In the **Select Cloud Service** dialog box, select **DIS** and click **OK**.                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Validity Period                   | Select **Unlimited**.                                                                                                                                      |
      |                                   |                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                  |
      |                                   |                                                                                                                                                            |
      |                                   |    Currently, this parameter must be set to **Unlimited**. Using another value may result in authorization failures.                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Agency description. The entered description cannot exceed 255 characters.                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Permissions                       | If **Dump Destination** is **OBS**, policy settings are as follows: Region: Global service Project: OBS Policy: Tenant Administrator                       |
      |                                   |                                                                                                                                                            |
      |                                   | To modify agency policies, click **Modify** in the **Operation** column. In the **Available Policies** area, select your required policy and click **OK**. |
      |                                   |                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                  |
      |                                   |                                                                                                                                                            |
      |                                   |    After an agency is created, its policies cannot be modified.                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
