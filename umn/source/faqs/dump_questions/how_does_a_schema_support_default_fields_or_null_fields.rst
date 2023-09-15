:original_name: dis_faq_0017.html

.. _dis_faq_0017:

How Does a Schema Support Default Fields or NULL Fields?
========================================================

A source data schema is a user's JSON data sample used to describe the JSON data format. DIS can generate the Avro schema based on the JSON data sample. By default, the default field or NULL is not supported, as shown in :ref:`Figure 1 <dis_faq_0017__en-us_topic_0197275340_fig12811073373>`.

.. _dis_faq_0017__en-us_topic_0197275340_fig12811073373:

.. figure:: /_static/images/en-us_image_0200877126.png
   :alt: **Figure 1** Example of not supporting the default field

   **Figure 1** Example of not supporting the default field

The type of the **key1** field is **String** (**type**: **string** in Avro Schema). If the **key1** field in the source data is not transferred or the transferred value is null, the dump task reports an error.

To enable the schema generated based on the JSON data sample supports the default value or null, select the **Convert and Move** and click **Convert Source Data Sample**, as shown in :ref:`Figure 2 <dis_faq_0017__en-us_topic_0197275340_fig2624141717523>`.

.. _dis_faq_0017__en-us_topic_0197275340_fig2624141717523:

.. figure:: /_static/images/en-us_image_0200879188.png
   :alt: **Figure 2** Example of supporting the default field

   **Figure 2** Example of supporting the default field

In this case, the type of the **key1** field is **Union** (**type**: **[null, string]** in Avro Schema). If the **key1** field in the source data is not transferred or the transferred value is null, null is automatically filled as the default value. The dump task can properly convert the format.
