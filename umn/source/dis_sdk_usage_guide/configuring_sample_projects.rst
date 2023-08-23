:original_name: dis_06_0013.html

.. _dis_06_0013:

Configuring Sample Projects
===========================

Download the **dis-sdk-**\ *1.2.3*\ **.zip** package from the URL noted in section :ref:`Downloading SDKs <dis_06_0005>`. The package provides a sample project. You can use a development tool (such as Eclipse) on the local server to compile and run the sample project. You can also develop your applications based on the sample project. The sample project code is available in the **\\dis-sdk-demo\\src\\com\\bigdata\\dis\\sdk\\demo** directory.

================= ====================
Sample Code       Description
================= ====================
ConsumerDemo.java How to download data
ProducerDemo.java How to upload data
================= ====================

Procedure
---------

#. Decompress the **dis-sdk-**\ *1.2.3*\ **.zip** package obtained in :ref:`Downloading SDKs <dis_06_0005>` to obtain the **dis-sdk-demo** package and sample project.
#. Import the Eclipse project.

   a. Start Eclipse and choose **File** > **Import**. The **Import** dialog box is displayed.

   b. Choose **General** > **Existing Projects into Workspace** and click **Next**. The **Import** dialog box is displayed.

   c. Click **Browse** and select a save location for the **dis-sdk-demo** sample project. In the **Projects** area, select a sample project, as shown in :ref:`Figure 1 <dis_06_0013__f23cd224614d04888bfa7c759107662f3>`.

      .. _dis_06_0013__f23cd224614d04888bfa7c759107662f3:

      .. figure:: /_static/images/en-us_image_0124306701.png
         :alt: **Figure 1** Import Projects

         **Figure 1** Import Projects

   d. Click **Finish** to import the project.

#. Configure the demo project.

   a. Set the project code to **UTF-8**.

      #. In the navigation tree, right-click the required project under **Project Explorer** and choose **Properties** from the shortcut menu. The **Properties for dis-sdk-demo** dialog box is displayed.
      #. In the navigation tree, choose **Resource**. The **Resource** page is displayed in the right pane.
      #. In the **Other** drop-down list, select **UTF-8**.
      #. Click **Apply and Close**.


      .. figure:: /_static/images/en-us_image_0000001499513972.png
         :alt: **Figure 2** Resource

         **Figure 2** Resource

   b. Import a JAR dependency package.

      #. In the navigation tree, right-click the required project under **Project Explorer** and choose **Properties** from the shortcut menu. The **Properties for dis-sdk-demo** dialog box is displayed.
      #. In the navigation tree, choose **Java Build Path**. The **Java Build Path** page is displayed in the right pane.
      #. Click the **Libraries** tab, and then click **Add External JARs**. The **JAR Selection** dialog box is displayed.
      #. Select the location of the **dis-sdk** folder in the decompressed **dis-sdk-**\ 1.2.3 file, and then click **Open**.
      #. On the **Properties for dis-sdk-demo** page, click **Apply and Close** to import all the **.jar** files in the current path and the **third_lib** folder to the project.


      .. figure:: /_static/images/en-us_image_0124306705.png
         :alt: **Figure 3** Java Build Path

         **Figure 3** Java Build Path

   c. Add the JDK.

      #. In the navigation tree, right-click the required project under **Project Explorer** and choose **Properties** from the shortcut menu. The **Properties for dis-sdk-demo** dialog box is displayed.
      #. In the navigation tree, choose **Java Build Path**. The **Java Build Path** page is displayed in the right pane.
      #. Click the **Libraries** tab, and then click **Add Library**. The **Add Library** dialog box is displayed.
      #. Select **JRE System Library** and click **Next**. Verify that the version of **Workspace default JRE** is **jdk1.8** or later.
      #. Click **Finish** to exit the **Add Library** dialog box.
      #. Click **Apply and Close**.
