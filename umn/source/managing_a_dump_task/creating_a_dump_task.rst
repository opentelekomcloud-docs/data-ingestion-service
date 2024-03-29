:original_name: dis_01_0047.html

.. _dis_01_0047:

Creating a Dump Task
====================

If a dump task is created for a DIS stream, data sent to the DIS stream can be automatically dumped to the selected target specified in the dump task.

#. Use the account to log in to the DIS console.

#. Click |image1| in the upper left corner of the page and select a region and project.

#. In the left navigation pane, choose Stream Management.

#. Click the name of a stream that you want to view. On the displayed page, click the **Dump Management** tab.

#. Click **Add Dump Task**. On the **Add Dump Task** page, configure dump parameters. For details about the dump task parameters, see :ref:`Table 1 <dis_01_0047__table1544912219359>`.

   .. note::

      A maximum of five dump tasks can be created for each stream.

#. Click **Create Now**.

#. In the **Operation** column of the corresponding **Task Name**, click **More** > **View Dump Log** to view the dump task details of the stream. :ref:`Table 2 <dis_01_0047__table104664221353>` describes the dump log parameters.

   .. _dis_01_0047__table1544912219359:

   .. table:: **Table 1** Dump task parameters

      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter                            | Description                                                                                                                                                                                                                             | Remarks                              |
      +======================================+=========================================================================================================================================================================================================================================+======================================+
      | **Data Dumping**                     |                                                                                                                                                                                                                                         |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      | Location to save data in the stream. |                                                                                                                                                                                                                                         |                                      |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Dump Destination                     | **OBS**: After the streaming data is stored to DIS, it is then periodically imported to OBS.                                                                                                                                            | ``-``                                |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Task Name                            | Name of the dump task. The names of dump tasks created for the same stream must be unique. A task name must be unique in the stream and is 1 to 64 characters long. Only letters, digits, hyphens (-), and underscores (_) are allowed. | ``-``                                |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Dump File Format                     | Text                                                                                                                                                                                                                                    | Only text data can be dumped to OBS. |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Dump Bucket                          | Name of the OBS bucket used to store data from the DIS stream. The bucket name is created when you create a bucket in OBS.                                                                                                              | ``-``                                |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | File Directory                       | Directory created in OBS to store files from the DIS stream. Different directory levels are separated by a forward slash (/). The value cannot start with a forward slash.                                                              | ``-``                                |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | This directory name is 0 to 50 characters long.                                                                                                                                                                                         |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | By default, this parameter is left unspecified.                                                                                                                                                                                         |                                      |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Time Directory Format                | Directory format based on the time. Data will be saved to the directory in the format of time layer under the dump file directory in the OBS bucket.                                                                                    | ``-``                                |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | For example, if the time directory is accurate to day, the data save path is "bucket name/dump file directory/year/month/day".                                                                                                          |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | Possible values are as follows:                                                                                                                                                                                                         |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | -  N/A: If this field is left blank, the time directory format will not be used.                                                                                                                                                        |                                      |
      |                                      | -  yyyy: year.                                                                                                                                                                                                                          |                                      |
      |                                      | -  yyyy/MM: year and month.                                                                                                                                                                                                             |                                      |
      |                                      | -  yyyy/MM/dd: year, month, and day.                                                                                                                                                                                                    |                                      |
      |                                      | -  yyyy/MM/dd/HH: year, month, day, and hour.                                                                                                                                                                                           |                                      |
      |                                      | -  yyyy/MM/dd/HH/mm: year, month, day, hour, and minute.                                                                                                                                                                                |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | You can only select but not enter a value in this field.                                                                                                                                                                                |                                      |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Record Delimiter                     | Delimiter used to separate different dump records.                                                                                                                                                                                      | ``-``                                |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | Possible values are as follows:                                                                                                                                                                                                         |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | -  Comma (,)                                                                                                                                                                                                                            |                                      |
      |                                      | -  Semicolon (;)                                                                                                                                                                                                                        |                                      |
      |                                      | -  Vertical bar (|)                                                                                                                                                                                                                     |                                      |
      |                                      | -  Newline (\\n)                                                                                                                                                                                                                        |                                      |
      |                                      | -  NULL                                                                                                                                                                                                                                 |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | You can only select but not enter a value in this field.                                                                                                                                                                                |                                      |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Dump Interval (s)                    | User-defined interval at which data is imported from the current DIS stream into OBS. If no data is pushed to the DIS stream during the current interval, no dump file package will be generated.                                       | ``-``                                |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | Value range: 30s to 900s                                                                                                                                                                                                                |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | Unit: second                                                                                                                                                                                                                            |                                      |
      |                                      |                                                                                                                                                                                                                                         |                                      |
      |                                      | Default value: 300s                                                                                                                                                                                                                     |                                      |
      +--------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

   .. _dis_01_0047__table104664221353:

   .. table:: **Table 2** Dump log parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================+
      | Start Time                        | Time when the dump log is created.                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                |
      |                                   | Format: YYYY/MM/dd HH:mm:ss GTM                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  YYYY: year.                                                                                                                                                                                 |
      |                                   | -  MM: month.                                                                                                                                                                                  |
      |                                   | -  dd: date.                                                                                                                                                                                   |
      |                                   | -  HH: hour.                                                                                                                                                                                   |
      |                                   | -  mm: minute.                                                                                                                                                                                 |
      |                                   | -  ss: second.                                                                                                                                                                                 |
      |                                   | -  GMT: time zone.                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | End Time                          | Time when you finish creating the dump log.                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                |
      |                                   | Format: YYYY/MM/dd HH:mm:ss GTM                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  YYYY: year.                                                                                                                                                                                 |
      |                                   | -  MM: month.                                                                                                                                                                                  |
      |                                   | -  dd: date.                                                                                                                                                                                   |
      |                                   | -  HH: hour.                                                                                                                                                                                   |
      |                                   | -  mm: minute.                                                                                                                                                                                 |
      |                                   | -  ss: second.                                                                                                                                                                                 |
      |                                   | -  GMT: time zone.                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Dump status.                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  Succeeded                                                                                                                                                                                   |
      |                                   | -  Failed                                                                                                                                                                                      |
      |                                   | -  Abnormal                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Dump File Name                    | Name of the file that is dumped to the target service. The user records read from the stream are written into the file and then dumped to the target service (such as OBS) in the file format. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Records                           | Number of the records uploaded between the time when you start to create a dump log to the time when you finish creating it.                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Amount (bytes)               | Amount of the data uploaded between the time when you start to create the dump log to the time when you finish creating it.                                                                    |
      |                                   |                                                                                                                                                                                                |
      |                                   | Unit: byte                                                                                                                                                                                     |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Dump failure details.                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  If **Status** is **Succeeded**, the column is not operable.                                                                                                                                 |
      |                                   | -  If **Status** is **Failed**, click **View Details** to view dump details.                                                                                                                   |
      |                                   | -  If **Status** is **Abnormal**, click **View Details** to view dump details.                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Modifying and Enabling Dump Tasks
---------------------------------

After creating a stream and adding a dump task successfully, you can modify the attributes of the created stream.

#. Log in to the DIS console.
#. Click |image2| in the upper left corner of the page and select a region and project.
#. In the navigation tree, choose **Stream Management**.
#. Click the name of a stream that you want to view. On the displayed page, click the **Dump Management** tab. Alternatively, in the **Operation** column of a stream that you want to view, click **More** and choose **View Dump Task** from the drop-down list.
#. In the **Operation** column of the stream for which a dump task has been added, perform the following operations:

   a. Choose **More > Modify** to modify the dump task.
   b. Choose **More > Start** to start the dump task.
   c. Choose **More > Pause** to pause the dump task.

.. |image1| image:: /_static/images/en-us_image_0238223179.png
.. |image2| image:: /_static/images/en-us_image_0238223179.png
