:original_name: dis_faq_0004.html

.. _dis_faq_0004:

What Can I Do with DIS?
=======================

You can use DIS for rapid data intake from producers and continuous data processing. The following are typical scenarios for using DIS:

-  Accelerated log or data transmission: Users do not need to wait for batch data processing. Data is put into a DIS stream immediately after it is generated by a data producer, preventing data loss in case of faults in the data producer. For example, system and application logs can be continuously put into a stream and processed within seconds.
-  Real-time metrics and reporting: You can retrieve data from DIS streams for simple data analysis and reporting in real time. For example, your DIS applications can work on metrics and reporting for system and application logs as streaming data is being pushed to DIS streams using application programming interfaces (APIs), rather than wait to receive batches of data.
-  Real-time data analysis: DIS combines the power of parallel processing with the value of real-time data. For example, you can transform data into valuable information and business intelligence by simply putting data into a DIS stream. This can be done in minutes instead of hours or days.
-  Complex stream processing: You can create Directed Acyclic Graphs (DAGs) of DIS applications and streams. This typically involves putting data from one or multiple DIS applications into another stream for downstream processing by a different DIS application.
