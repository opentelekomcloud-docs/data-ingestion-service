:original_name: dis_06_0506.html

.. _dis_06_0506:

Creating a Demo Class
=====================

Creating a FileProducerAsyncDemo Class
--------------------------------------

In the Project Explorer pane, right-click **com.bigdata.dis.sdk.demo**, and choose **New > Class** from the shortcut menu. The **New Java Class** dialog box is displayed. Set the category name to **FileProducerAsyncDemo**. Add the following codes to the new category:

.. code-block::

   package com.bigdata.dis.sdk.demo;

   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;

   import com.bigdata.dis.data.iface.request.PutFilesRequest;
   import com.bigdata.dis.data.iface.response.PutFilesResult;
   import com.bigdata.dis.sdk.DISAsync;
   import com.bigdata.dis.sdk.DISClientAsyncBuilder;
   import com.bigdata.dis.sdk.core.builder.DefaultExecutorFactory;
   import com.bigdata.dis.sdk.core.handler.AsyncHandler;

   public class FileProducerAsyncDemo
   {
       private static final Logger log = LoggerFactory.getLogger(FileProducerAsyncDemo.class);

       public static void main(String args[])
           throws Exception
       {
           DISAsync dicAsync = DISClientAsyncBuilder.standard()
               .withEndpoint("https://ip:port")
               .withAk("xxxx")
               .withSk("xxxx")
               .withProjectId("xxxx")
               .withRegion("xxxx")
               .withExecutorFactory(new DefaultExecutorFactory())
               .build();

           // Configure the stream name.
           String streamName = "fileUploadStream";

           PutFilesRequest putFilesRequest = new PutFilesRequest();
           putFilesRequest.setStreamName(streamName);

           //Configure the path of the file to be uploaded.
           putFilesRequest.setFilePath("xxxx");

           //Configure the file name for storing the uploaded real-time data file.
           putFilesRequest.setFileName("xxxx");

           dicAsync.putFilesAsync(putFilesRequest, new AsyncHandler<PutFilesResult>()
           {

               @Override
               public void onSuccess(PutFilesResult result)
               {
                   log.info("Upload file to DIS successful!");
               }

               @Override
               public void onError(Exception exception)
               {
                   log.error("Fail to upload file to DIS.", exception);
               }
           });


       }
   }
