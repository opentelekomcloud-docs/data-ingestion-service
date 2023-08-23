:original_name: dis_01_0045.html

.. _dis_01_0045:

Interconnecting with OBS
========================

Introduction
------------

DIS can upload data to Object Storage Service (OBS).

Prerequisites
-------------

An IAM agency has been created by following the procedure in :ref:`Creating an IAM Agency <dis_01_0605>`. This IAM agency entrusts DIS to access your OBS resources.

Data Dumping
------------

You can set **Dump Bucket** when :ref:`Creating a Dump Task <dis_01_0047>`. If Dump Destination is set to **OBS**, DIS periodically imports data from DIS streams to OBS.
