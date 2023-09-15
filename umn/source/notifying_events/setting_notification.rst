:original_name: dis_01_0053.html

.. _dis_01_0053:

Setting Notification
====================

After enabling Notification for subscribed events, you will receive notifications by email or SMS when management, monitoring, or security events occur in a specific cluster or dump task.

Creating a Subscription
-----------------------

#. Use the account to log in to the DIS console.

#. Click **Event Management**.

#. On the **Event Management** page, choose **Subscriptions** > **Create Subscription**.

#. .. _dis_01_0053__en-us_topic_0107811181_li18772435125416:

   In the **Subscription Settings** area, set basic subscription information and event filtering.

   The **Events** area displays the events filtered by the system based on the subscription settings.

   .. table:: **Table 1** Subscription parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================================+
      | Notification                      | Enable or disable event subscription.                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                               |
      |                                   | |image1| indicates that notification is enabled and |image2| indicates that notification is disabled. By default, notification is disabled. After notification is disabled, the system stops sending notifications of subscribed events but does not delete the subscription. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subscription Name                 | Enter the name of a subscription.                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                               |
      |                                   | -  The name can contain letters (upper or lower case), digits, hyphens (-), and underscores (_) and must start with a letter or digit.                                                                                                                                        |
      |                                   | -  The name contains 1 to 64 characters.                                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subscription Stream               | Specifies whether to enable subscription to alarms of a specified stream.                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                               |
      |                                   | |image3| indicates that subscription to alarms of a specified stream is enabled. |image4| indicates that subscription to alarms of a specified channel is disabled. By default, the function is disabled.                                                                     |
      |                                   |                                                                                                                                                                                                                                                                               |
      |                                   | After this function is enabled, the alarms sent from your specified stream are received, and sent from other streams will not be received.                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subscription Type                 | Two subscription types are supported: SMN and DIS.                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                               |
      |                                   |    -  If **Subscription Type** is set to **SMN**, go to :ref:`Step 5 <dis_01_0053__en-us_topic_0107811181_li89041225162317>`.                                                                                                                                                 |
      |                                   |    -  If **Subscription Type** is set to **DIS**, go to :ref:`5 <dis_01_0053__en-us_topic_0107811181_li89041225162317>` to select a stream.                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. .. _dis_01_0053__en-us_topic_0107811181_li89041225162317:

   Select a message notification topic from the **SMN Topic** drop-down list.

   You can perform the following operations to create a message notification topic as required.

   a. Click **Create SMN Topic**. The **Topics** page of SMN is displayed. You can click **Create Topic** in the upper right corner to create a topic. For details, see section **Creating a Topic** in the *Simple Message Notification User Guide*.
   b. In the **Operation** column of a topic, choose **More** > **Configure Topic Policy** and select **DIS** under **Services that can publish messages to this topic** to enable SMN to publish DIS topics.
   c. In the row containing the created topic, click **Add Subscription** to add a subscription to the topic. For details, see **Adding a Subscription** in the *Simple Message Notification User Guide*.

#. .. _dis_01_0053__en-us_topic_0107811181_li164751612342:

   Click **OK**.

Modifying the Subscription
--------------------------

#. Choose **Event Management** > **Subscriptions**.
#. In the **Operation** column of a specified subscription name, choose **More** > **Modify**.
#. On the **Subscription Settings** page, set the parameters that you want to modify. For details, see :ref:`Step 4 <dis_01_0053__en-us_topic_0107811181_li18772435125416>` to :ref:`Step 6 <dis_01_0053__en-us_topic_0107811181_li164751612342>` in section **Creating a Subscription**.

Deleting the Subscription
-------------------------

#. Choose **Event Management** > **Subscriptions**.

#. In the **Operation** column of a specified subscription name, choose **More** > **Delete**. The **Delete Subscription** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0130822560.png
      :alt: **Figure 1** Confirming deletion

      **Figure 1** Confirming deletion

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001274606310.png
.. |image2| image:: /_static/images/en-us_image_0000001325286261.png
.. |image3| image:: /_static/images/en-us_image_0000001325622881.png
.. |image4| image:: /_static/images/en-us_image_0000001274783064.png
