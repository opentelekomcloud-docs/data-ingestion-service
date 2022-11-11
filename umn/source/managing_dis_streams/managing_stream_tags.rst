:original_name: dis_01_0050.html

.. _dis_01_0050:

Managing Stream Tags
====================

A tag is an identifier of a stream. Adding tags to streams can help you identify and manage your stream resources.

You can add a maximum of 10 tags to a stream when creating the stream or add them on the details page of the created stream.

A tag consists of a tag key and a tag value. :ref:`Table 1 <dis_01_0050__en-us_topic_0110219762_table16316649132010>` describes the rules for naming the tag key and value.

.. _dis_01_0050__en-us_topic_0110219762_table16316649132010:

.. table:: **Table 1** Naming rules for a tag key and value

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Rule                                                                                                                       | Example               |
   +=======================+============================================================================================================================+=======================+
   | Key                   | A tag key cannot be left blank.                                                                                            | Organization          |
   |                       |                                                                                                                            |                       |
   |                       | A tag key must be unique for a stream.                                                                                     |                       |
   |                       |                                                                                                                            |                       |
   |                       | A tag key contains a maximum of 36 characters.                                                                             |                       |
   |                       |                                                                                                                            |                       |
   |                       | A tag value cannot contain special characters ``=*<>\,|/`` or start or end with a space.                                   |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Tag value             | A tag value contains a maximum of 43 characters.                                                                           | Apache                |
   |                       |                                                                                                                            |                       |
   |                       | A tag value cannot contain special characters ``=*<>\,|/`` or start or end with a space. This parameter can be left blank. |                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------------+

Adding a Tag to a Stream
------------------------

You can add a tag to a stream on the **Buy Stream** page.

#. Log in to the management console.

#. Choose **Enterprise Intelligence** > **Data Ingestion Service**.

#. On the DIS management console, click **Buy Stream**.

#. On the **Advanced Settings** tab page, select **Configure**.

   Enter the key and value of a tag to be added.

   You can add a maximum of 10 tags to the stream and use intersections of tags to search for the target stream.

   .. note::

      You can also add tags to existing streams. For details, see :ref:`Managing Tags <dis_01_0050__section188067265123>`.

Searching for a Target Stream
-----------------------------

You can search for a target stream by tag on the **Stream Management** page.

#. Log in to the management console.

#. Choose **EI Enterprise Intelligent** > **Data Ingestion Service**.

#. In the navigation tree, choose **Ingestion Management** > **Stream Management**. In the upper right corner of the page, click **Search by Tag**.

#. Enter the tag key and value of the stream you are searching for.

   You can select a tag key or tag value from its drop-down list. When the tag key or tag value is exactly matched, the system can automatically locate the target stream. If you enter multiple tags, their intersections are used to search for the stream.

#. Click **Search**.

   The system searches for the target stream by tag key or value.

.. _dis_01_0050__section188067265123:

Managing Tags
-------------

You can add, delete, modify, and view tags on the **Tags** tab page of a stream.

#. Log in to the management console.

#. Choose **EI Enterprise Intelligent** > **Data Ingestion Service**.

#. In the navigation tree, choose **Ingestion Management** > **Stream Management**. Click a stream to which the tags to be managed belong to.

   The stream details page is displayed.

#. Click the **Tags** tab and add, deleted, modify, and view tags.

   -  View

      On the **Tags** tab page, you can view details about tags of the stream, including the number of tags and the key and value of each tag.

   -  Add

      Click **Add Tag** in the upper left corner. In the displayed **Add Tag** dialog box, enter the key and value of the tag to be added, and click **OK**.

   -  Modify

      In the **Operation** column of a tag, click **Edit**. In the displayed **Edit Tag** page, enter a new tag key and value and click **OK**.

   -  Delete

      In the **Operation** column of the tag, click **Delete**. After confirmation, click **OK** on the displayed **Delete Tag** page.
