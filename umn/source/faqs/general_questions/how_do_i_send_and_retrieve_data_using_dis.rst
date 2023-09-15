:original_name: dis_faq_0003.html

.. _dis_faq_0003:

How Do I Send and Retrieve Data Using DIS?
==========================================

#. Create a DIS stream. Obtain your Access Key ID/Secret Access Key (AK/SK) pair from the Identity and Access Management (IAM) service.

#. Download and decompress the DIS SDK software package.

   Verify integrity of the DIS SDK software package by following the procedure in :ref:`How Do I Check Software Package Integrity? <dis_faq_0009>`

   -  Download link of the DIS SDK software package:

      https://dis.obs.eu-de.otc.t-systems.com/dis/download/dis-sdk-1.2.3.zip

   -  Download link of the package integrity verification file:

      https://dis.obs.eu-de.otc.t-systems.com/dis/download/dis-sdk-1.2.3.zip.sha256sum

#. Create a producer project and configure the user AK/SK, endpoint, project ID, region, stream name, and the number of partitions.

#. Run the producer application to send data.

#. Create a consumer project and configure the user AK/SK, endpoint, project, region, stream name, partition ID, and startingSequenceNumber.

#. Run the consumer application to retrieve data.
