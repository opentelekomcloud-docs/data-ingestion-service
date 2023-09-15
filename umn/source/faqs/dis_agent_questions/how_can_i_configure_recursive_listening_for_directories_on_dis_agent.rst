:original_name: dis_faq_0015.html

.. _dis_faq_0015:

How Can I Configure Recursive Listening for Directories on DIS Agent?
=====================================================================

On DIS Agent, set **directoryRecursionEnabled** to **true**. For example, the following configuration can match **/home/one.log**, **/home/child/two.log**, and **/home/child/child/three.log**:

.. code-block::

   ---
   region: REGION
   ak: YOUR_AK
   sk: YOUR_SK
   projectId: YOUR_PROJECTID
   endpoint: ENDPOINT
   flows:
     - DISStream: YOUR_STREAM
       filePattern: /home/*.log
       directoryRecursionEnabled: true
       initialPosition: START_OF_FILE
       maxBufferAgeMillis: 5000
