:original_name: dis_01_0076.html

.. _dis_01_0076:

Managing Applications
=====================

An application is a program identifier. Multiple applications can access data in the same stream. Checkpoints generated for each application are used to record the consumed data in the stream by each application.

You can create applications and view details about existing application on the DIS console.

Creating an Application
-----------------------

#. Use the account to log in to the DIS console.

#. Click |image1| in the upper left corner of the page and select a region and project.

#. In the navigation tree, select **App Management**.

   On the **Applications** page, click **Create App** and enter an application name.

Viewing an Application
----------------------

#. Use the account to log in to the DIS console.

#. Click |image2| in the upper left corner of the page and select a region and project.

#. In the navigation tree on the left, choose **Stream Management**.

#. Click the name of a stream that you want to view.

#. Click **Applications** to view all applications that access the stream.

   You can view the names, IDs, and creation time of the applications that access the stream.

   After you click **Remove All Checkpoints**, all checkpoints of the application will be deleted.

   .. note::

      When an application consumes data, the latest SN of the consumed data is recorded as a checkpoint. When the data is reconsumed, the consumption can be continued based on this checkpoint.


   .. figure:: /_static/images/en-us_image_0165229968.jpg
      :alt: **Figure 1** Viewing applications

      **Figure 1** Viewing applications

#. Click a specific application to view its consumption details about the stream.


   .. figure:: /_static/images/en-us_image_0165286917.jpg
      :alt: **Figure 2** Viewing stream consumption details

      **Figure 2** Viewing stream consumption details

.. |image1| image:: /_static/images/en-us_image_0165093532.png
.. |image2| image:: /_static/images/en-us_image_0165094364.png
