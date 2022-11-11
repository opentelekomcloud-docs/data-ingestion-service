:original_name: dis_06_0023.html

.. _dis_06_0023:

Initializing a DIS SDK Asynchronous Client Instance
===================================================

Initialize a DIS SDK asynchronous client instance. For details about **endpoint**, **ak**, **sk**, **region**, and **projectId**, see :ref:`Obtaining Authentication Information <dis_01_0043>`.

.. code-block::

   //Create a DIS client instance.
   DISAsync dicAsync = DISClientAsyncBuilder.standard()
               .withEndpoint("https://ip:port")
               .withAk("xxxx")
               .withSk("xxxx")
               .withProjectId("xxxx")
               .withRegion("xxxx")
               .withExecutorFactory(new DefaultExecutorFactory())
               .build();
