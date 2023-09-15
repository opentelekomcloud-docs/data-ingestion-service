:original_name: dis_faq_0014.html

.. _dis_faq_0014:

How Can I Configure Agent to Listen To Multiple Directories or Files?
=====================================================================

DIS Agent can listen to multiple directories or files. For example, to collect logs of the **/home/folder1/file1** and **/home/folder2/file2** files, configure multiple DIS streams.

.. code-block::

   ---
   region: REGION
   ak: YOUR_AK
   sk: YOUR_SK
   projectId: YOUR_PROJECTID
   endpoint: ENDPOINT
   flows:
     - DISStream: YOUR_STREAM
       filePattern: /home/folder1/file1
       initialPosition: START_OF_FILE
       maxBufferAgeMillis: 5000

     - DISStream: YOUR_STREAM
       filePattern: /home/folder2/file2
       initialPosition: START_OF_FILE
       maxBufferAgeMillis: 5000
