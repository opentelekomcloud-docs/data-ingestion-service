:original_name: dis_02_0003.html

.. _dis_02_0003:

Application Example
===================

Scenarios
---------

DIS provides efficient collection, transmission, and distribution capabilities for real-time data and provides a variety of APIs to help you quickly build real-time data applications.

The following describes how to create a DIS stream by calling the :ref:`Before You Start <dis_02_0511>` API. For details, see :ref:`Calling APIs <dis_02_0516>`.

.. note::

   The token obtained on IAM is valid for only 24 hours. If you want to use one token for authentication, you can cache it to avoid frequent calling.

Involved APIs
-------------

If you use a token for authentication, you must obtain the token and add **X-Auth-Token** to the request header of the API request.

-  API for obtaining a token from IAM
-  API for creating a DIS stream

Prerequisites
-------------

You have planned the region where DIS is located and determined the endpoint for calling an API based on the region.

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints of the service from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

Creating a Stream
-----------------

The following is an example of creating a stream with the simplest configuration.

#. Obtain the token by following the instructions in :ref:`Token-based Authentication <dis_02_0517__en-us_topic_0183235768_en-us_topic_0181281305_dis_02_0517_en-us_topic_0121671869_section2417768214391>`.

#. Send **POST https://Endpoint of DIS/v2/{project_id}/streams**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
      "stream_name": "dis-DLpR",
      "partition_count": 1,
      "stream_type": "COMMON",
      "data_duration": 24
      }

   -  **stream_name** indicates the stream name, which can be customized, for example, **newstream**.
   -  **partition_count** indicates the number of partitions. A partition is the base throughput unit of a DIS stream. You can specify the number of partitions based on your service throughput requirements.
   -  **stream_type** indicates the stream type. **COMMON** indicates a common partition. A single partition supports a maximum of 1 MB/s for data writing and a maximum of 2 MB/s for data reading.
   -  **data_duration** indicates the lifecycle of a stream, that is, the duration for storing data in the stream partition.

   If the request is successful, 201 Created is returned.

   If the request fails, an error code and error information are returned. For details, see :ref:`Error Codes <errorcode>`.

Creating a Stream That Supports Auto Scaling
--------------------------------------------

You can also create a stream that supports auto scaling. The number of partitions can be automatically increased or decreased based on the stream traffic. The following is an example configuration:

#. Obtain the token by following the instructions provided in :ref:`Token-based Authentication <dis_02_0517__en-us_topic_0183235768_en-us_topic_0181281305_dis_02_0517_en-us_topic_0121671869_section2417768214391>`.

#. Send **POST https://Endpoint of DIS/v2/{project_id}/streams**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
      "stream_name": "dis-DLpR",
      "partition_count": 1,
      "stream_type": "COMMON",
      "data_duration": 24
      "auto_scale_enabled": true,
      "auto_scale_min_partition_count": 2,
      "auto_scale_max_partition_count": 10
      }

   In this example, a stream that supports auto scaling is created. The number of partitions to scale ranges from 2 to 10. If the stream has 10 partitions, auto scaling-out will not be triggered.

   -  **auto_scale_enabled** specifies whether to enable auto scaling. The value **true** indicates that auto scaling is enabled.
   -  **auto_scale_min_partition_count** indicates the minimum number of partitions allowed when auto scale-in is enabled. In this example, as there are two partitions, automatic scale-in will not be triggered.
   -  **auto_scale_max_partition_count** indicates the maximum number of partitions allowed when auto scale-out is enabled. In this example, as there are 10 partitions, automatic scale-out will not be triggered.

   If the request is successful, 201 Created is returned.

   If the request fails, an error code and error information are returned. For details, see :ref:`Error Codes <errorcode>`.

Creating a Stream with Data Schemas
-----------------------------------

You can also configure a schema for the stream. When using DIS to dump data to other services, you can map data based on the schema configured for the stream. The following is an example configuration:

#. Obtain the token by following the instructions provided in :ref:`Token-based Authentication <dis_02_0517__en-us_topic_0183235768_en-us_topic_0181281305_dis_02_0517_en-us_topic_0121671869_section2417768214391>`.

#. Send **POST https://Endpoint of DIS/v2/{project_id}/streams**.

#. Add **X-Auth-Token** to the request header.

#. Specify the following parameters in the request body:

   .. code-block::

      {
      "stream_name": "dis-DLpR",
      "partition_count": 1,
      "stream_type": "COMMON",
      "data_duration": 24
      "auto_scale_enabled": true,
      "auto_scale_min_partition_count": 1,
      "auto_scale_max_partition_count": 10
      "data_type": "BLOG",
      }

   If the request is successful, 201 Created is returned.

   If the request fails, an error code and error information are returned. For details, see :ref:`Error Codes <errorcode>`.
