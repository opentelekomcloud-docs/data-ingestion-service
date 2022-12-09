:original_name: dis_faq_0007.html

.. _dis_faq_0007:

What Is the Difference Between Storing Data into DIS and Dumping Data Elsewhere?
================================================================================

After DIS is enabled, data is stored to DIS by default. After a dump task is added, the data can be dumped to other resources. :ref:`Table 1 <dis_faq_0007__tdc4c4ec0b2454cfeb8421d92412355e6>` describes the specific differences.

-  Data is stored to DIS by default.
-  If **Dump Destination** is set to **OBS**, data is stored in DIS and periodically imported to Object Storage Service (OBS).

.. _dis_faq_0007__tdc4c4ec0b2454cfeb8421d92412355e6:

.. table:: **Table 1** Difference between storing data into DIS and dumping data elsewhere

   +---------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | DIS Storage                                                         | OBS Storage                                                                 |
   +=====================================================================+=============================================================================+
   | You can store data into DIS without applying for storage resources. | You must apply for OBS resources before dumping data to OBS.                |
   +---------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | No additional payment is required.                                  | Additional cost for the use of OBS. For details, see the OBS price details. |
   +---------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Data is temporarily stored in DIS for up to 168 hours.              | Data is stored in OBS until your OBS bucket expires.                        |
   +---------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Data is stored only in DIS.                                         | Data is stored in DIS and periodically dumped to OBS.                       |
   +---------------------------------------------------------------------+-----------------------------------------------------------------------------+
