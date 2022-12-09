:original_name: dis_01_0229.html

.. _dis_01_0229:

The CDR Specification
=====================

Charging requirement: Charging starts from the time when the DIS instance is created and stops when the DIS instance is deleted.

CDR record cycle: The minimum granularity is minute, and the current cycle is 60 minutes. The interval for uploading offline CDR files is one hour.

There are three types of Product ID corresponding to three billing factors in DIS. The detail information of the product ID looks like below:

.. table:: **Table 1** DIS Product ID

   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
   | ResourceTypeCode               | ID Commercial Product | Describe of Commercial Product EN                           | Unit of Measure |
   +================================+=======================+=============================================================+=================+
   | *otc*.resource.type.dispart    | OTC_DIS_GEN_TIME      | The length of time the user is using the general partition  | second          |
   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
   |                                | OTC_DIS_ADV_TIME      | The length of time the user is using the advanced partition | second          |
   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
   | *otc*.resource.type.dispayunit | OTC_DIS_GEN_UNIT      | The number of the PUT Payload Unit for general partition    | number          |
   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
   |                                | OTC_DIS_ADV_UNIT      | The number of the PUT Payload Unit for advanced partition   | number          |
   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
   | *otc*.resource.type.dissize    | OTC_DIS_GEN_STORE     | The data storage size in general partition.                 | byte            |
   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
   |                                | OTC_DIS_ADV_STORE     | The data storage size in advanced partition.                | byte            |
   +--------------------------------+-----------------------+-------------------------------------------------------------+-----------------+
