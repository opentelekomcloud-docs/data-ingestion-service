:original_name: dis_02_0501.html

.. _dis_02_0501:

Obtaining a Project ID
======================

Obtaining a Project ID by Calling an API
----------------------------------------

You can obtain the project ID by calling the API `used to query project information <https://docs.otc.t-systems.com/api/iam/en-us_topic_0057845625.html>`__.

The API used to obtain a project ID is GET **https://{Endpoint}/v3/projects**. **{Endpoint}** is the IAM endpoint and can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. For details about API authentication, see :ref:`Authentication <dis_02_0517>`.

The following is an example response. The value of **id** is the project ID. If multiple IDs are returned, obtain the desired project ID based on the actual region (name).

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "region_name",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }

Obtaining a Project ID from the Console
---------------------------------------

A project ID is required for some URLs when an API is called. To obtain a project ID, perform the following operations:

#. Log in to the management console.

#. Click the username and select **My Credentials** from the drop-down list.

   On the **My Credentials** page, view project IDs in the project list.


.. figure:: /_static/images/en-us_image_0191919629.jpg
   :alt: **Figure 1** Viewing project IDs

   **Figure 1** Viewing project IDs
