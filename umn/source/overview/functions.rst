:original_name: dis_01_0003.html

.. _dis_01_0003:

Functions
=========

DIS manages the infrastructure, storage, networking, and configuration needed to stream your data. You do not have to worry about provisioning, deployment, and constant maintenance of hardware. In addition, DIS synchronously replicates data across availability zones, providing high availability and data durability.

Key Modules
-----------

DIS consists of the following four functional modules:

-  Service control

   -  Creates, deletes, and configures DIS streams; synchronizes user information to the data plane.
   -  Allocates resources and automatically deploys DIS on the data plane.

-  Data processing

   -  Receives user requests, and receives and stores authenticated data.
   -  Receives data read requests and returns the requested data to authorized users.
   -  Removes old data from DIS streams according to data aging policies.
   -  Stores user data into OBS.

-  Service maintenance

   -  Installs and upgrades DIS.
   -  Performs configuration, preventive maintenance, monitoring, and log collection and analysis for DIS.
   -  Processes service orders.

-  User SDK

   -  Provides Java APIs for users to push and pull data.
   -  Encrypts data.

Key Capabilities
----------------

-  Scalable: A DIS stream can seamlessly scale its data throughput from megabytes to terabytes per hour, and from thousands to millions of PUT records per second.
-  Easy to use: You can create a DIS stream within seconds. It is easy to put data into a stream, and build a data processing application.
-  Low cost: DIS has no upfront cost and you only pay for the resources you use.
-  Parallel processing: DIS allows you to have multiple DIS applications processing the same stream concurrently. For example, you can have one application running real-time analytics and another sending data to OBS from the same stream.
-  Secure and reliable: DIS can retain data for 24 to 72 hours to prevent data loss in case of application faults, individual machine faults, or facility faults.
