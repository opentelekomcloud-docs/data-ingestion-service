:original_name: dis_faq_0009.html

.. _dis_faq_0009:

How Do I Check Software Package Integrity?
==========================================

This section describes how to verify integrity of the DIS SDK software package on a Linux system by using a verification file.

Prerequisites
-------------

-  The PuTTY tool is available.
-  The WinSCP tool is available.

Procedure
---------

#. Upload the DIS SDK software package **sdk-dis-x.x.x1.2.3.zip** to any directory on the Linux system by using WinSCP.

   .. note::

      In **sdk-dis-x.x.x.zip**, **x.x.x** indicates the version number of the DIS SDK software package.

#. Log in to the Linux system by using PuTTY. In the directory in which **sdk-dis-x.x.x1.2.3.zip** is stored, run the following command to obtain the verification code of the DIS SDK software package

   **sha256sum sdk-dis-x.x.x.zip**

   Example verification code:

   .. code-block::

      # sha256sum dis-sdk-x.x.x.zip
      8be2c937e8d78b1a9b99777cee4e7131f8bf231de3f839cf214e7c5b5ba3c088 cloud-sdk-dis-x.x.x.zip

#. Open the DIS SDK verification file **sdk-dis-x.x.x1.2.3.zip.sha256sum** and compare it with the verification code obtained in **Step 2**.

   -  If they are consistent, the DIS-SDK compression package has not been tampered with.
   -  If they are inconsistent, the DIS SDK software package is tampered with and you need to obtain it again.
