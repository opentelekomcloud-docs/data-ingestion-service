:original_name: dis_06_0507.html

.. _dis_06_0507:

Uploading Files
===============

Configuring a Stream for Uploading Real-Time Files
--------------------------------------------------

You must use the enabled stream to transmit real-time files. Here, **fileUploadStream** is used as an example.

The value of **streamName** must be the same as that of **Stream Name** configured in :ref:`Step 1: Creating a DIS Stream <dis_01_0601>`.

.. code-block::

   //Configure the stream name.
   String streamName = "fileUploadStream";

Specifying the Path of the Real-Time File to Be Uploaded
--------------------------------------------------------

Enter the absolute path of the file to be uploaded.

.. code-block::

   //Specify the path of the file to be uploaded.
   putFilesRequest.setFilePath("xxxx");

Specifying the Name of the File for Storing the Uploaded Real-Time Data
-----------------------------------------------------------------------

Set the file name to be uploaded. If the file name contains the backslash (\\), use the escape character to escape the backslash.

.. code-block::

   //Specify the file name for storing the uploaded file.
   putFilesRequest.setFileName("xxxx");

Running the Program
-------------------

Right-click the program and choose **Run As > 1 Java Application** from the shortcut menu. If the program is run successfully, you can view the information similar to the following on the console:

.. code-block::

   17:47:09.103 [main] INFO  com.bigdata.dis.sdk.DISConfig - get from classLoader
   17:47:10.275 [pool-2-thread-1] INFO  com.bigdata.dis.sdk.util.config.ConfigurationUtils - get from classLoader
   17:47:10.291 [pool-2-thread-1] INFO  com.bigdata.dis.sdk.util.config.ConfigurationUtils - propertyMapFromFile size : 2
   17:47:20.012 [pool-2-thread-1] INFO  com.bigdata.dis.sdk.demo.FileProducerAsyncDemo - Upload file to DIS successful!
