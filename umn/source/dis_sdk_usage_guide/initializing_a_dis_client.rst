:original_name: dis_06_0015.html

.. _dis_06_0015:

Initializing a DIS Client
=========================

You can use either of the following methods to initialize a DIS SDK client instance: For details about **endpoint**, **ak**, **sk**, **region**, and **projectId**, see :ref:`Obtaining Authentication Information <dis_01_0043>`.

-  Use the code to initialize the DIS SDK client instance. For details about the code example, see the **ProducerDemo.java** file.

   .. code-block::

      //Create a DIS client instance.
                  DIS dic = DISClientBuilder.standard()
                      .withEndpoint("https://ip:port")
                      .withAk("xxxx")
                      .withSk("xxxx")
                      .withProjectId("xxxxxxx")
                      .withRegion("xxxx")
                      .build();

-  Use the configuration file to initialize a DIS SDK client instance.

   Add the following configuration items to the **dis.propertites** file in the **dis-sdk-demo\\resources** directory:

   -  ak/sk: AK/SK created on the IAM
   -  region: region of the stream
   -  endpoint: access address of the DIS
   -  projectId: project ID of the stream

   .. code-block::

      //Create a DIS client instance.
                  DIS dic = DISClientBuilder.standard().build();
