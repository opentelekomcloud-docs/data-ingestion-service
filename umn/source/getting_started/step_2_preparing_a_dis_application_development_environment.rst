:original_name: dis_01_0602.html

.. _dis_01_0602:

Step 2: Preparing a DIS Application Development Environment
===========================================================

Before developing DIS applications, prepare an application development environment, and then obtain a software development kit (SDK) and sample project and import them to the development environment.

Prerequisites
-------------

-  JDK 1.8 or later has been installed.
-  Eclipse has been installed.

Procedure
---------

#. Configure a JDK using Eclipse.

   a. Start Eclipse and choose **Window** > **Preferences**. The **Preferences** dialog box is displayed.

   b. In the navigation tree, choose **Java**. On the **Java** page, configure general settings for Java development and then click **OK**.


      .. figure:: /_static/images/en-us_image_0000001266697405.png
         :alt: **Figure 1** Preferences

         **Figure 1** Preferences

   c. In the navigation tree, choose **Java** > **Installed JREs**.

      -  Ensure that configured JDK environmental variables are displayed on the **Installed JREs** page. Then go to :ref:`1.c.i <dis_01_0602__li12377149194529>`.
      -  To configure different variables for different versions of JDK, perform :ref:`1.c.ii <dis_01_0602__li40268681153416>` to :ref:`1.c.iv <dis_01_0602__li6851708153416>`.


      .. figure:: /_static/images/en-us_image_0000001266777405.png
         :alt: **Figure 2** Installed JREs

         **Figure 2** Installed JREs

      #. .. _dis_01_0602__li12377149194529:

         Select the installed JDK and click **OK**.

      #. .. _dis_01_0602__li40268681153416:

         Click **Add**. The **Add JRE** dialog box is displayed.


         .. figure:: /_static/images/en-us_image_0000001222257286.png
            :alt: **Figure 3** JRE Type

            **Figure 3** JRE Type

      #. Select a JRE type and click **Next**.


         .. figure:: /_static/images/en-us_image_0000001266897385.png
            :alt: **Figure 4** JRE Definition

            **Figure 4** JRE Definition

      #. .. _dis_01_0602__li6851708153416:

         Configure the basic information about JDK and click **Finish**.

         -  JRE home: JDK installation path.
         -  Default VM arguments: JDK running parameters.

#. Download resource packages.

   Download the DIS SDK from https://dis.obs.eu-de.otc.t-systems.com/dis/download/dis-sdk-1.2.3.zip and its integrity check file from https://dis.obs.eu-de.otctest.t-systems.com/dis/download/dis-sdk-1.2.3.zip.sha256sum.

#. Import the Eclipse project.

   a. Start Eclipse. Choose **File** > **Import**. The **Import** dialog box is displayed.

   b. Choose **General** > **Existing Projects into Workspace** and click **Next**. The **Import** dialog box is displayed.

   c. Click **Browse** and select a save location for the **dis-sdk-demo** sample project. In the **Projects** area, select a sample project.


      .. figure:: /_static/images/en-us_image_0000001222417242.png
         :alt: **Figure 5** Importing a project

         **Figure 5** Importing a project

   d. Click **Finish**.

#. Configure the demo project.

   a. Set the project code to **UTF-8**.

      #. In the navigation tree, right-click the required project under **Project Explorer** and choose **Properties** from the shortcut menu. The **Properties for dis-sdk-demo** dialog box is displayed.
      #. In the navigation tree, choose **Resource**. The **Resource** page is displayed in the right pane.
      #. In the **Other** drop-down list, select **UTF-8**.
      #. Click **Apply and Close**.

   b. Import a dependency package.

      #. In the navigation pane, choose **Project Explorer**. Right-click the chosen project and choose **Properties** from the shortcut menu.
      #. In the navigation tree, choose **Java Build Path**. The **Java Build Path** page is displayed in the right pane.
      #. Click the **Libraries** tab, and then click **Add External JARs**. The **JAR Selection** dialog box is displayed.
      #. Select the directory where the **dis-sdk** folder is located and click **Open**.
      #. On the **Properties for dis-sdk-demo** page, click **Apply and Close** to import all the **.jar** files in the current path and the **third_lib** folder to the project.


      .. figure:: /_static/images/en-us_image_0000001222097282.png
         :alt: **Figure 6** Java Build Path

         **Figure 6** Java Build Path

   c. Add the JDK.

      #. In the navigation pane, choose **Project Explorer**. Right-click the chosen project and choose **Properties** from the shortcut menu.
      #. In the navigation tree, choose **Java Build Path**. The **Java Build Path** page is displayed in the right pane.
      #. Click the **Libraries** tab, and then click **Add Library**. The **Add Library** dialog box is displayed.
      #. Select **JRE System Library** and click **Next**. Verify that the version of **Workspace default JRE** is **jdk1.8** or later.
      #. Click **Finish** to exit the **Add Library** dialog box.
      #. Click **Apply and Close**.

#. Initialize a DIS client sample. For details about **endpoint**, **ak**, **sk**, **region**, and **projectId**, see :ref:`Obtaining Authentication Information <dis_01_0043>`.
