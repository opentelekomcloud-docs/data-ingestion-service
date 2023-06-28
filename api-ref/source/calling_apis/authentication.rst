:original_name: dis_02_0517.html

.. _dis_02_0517:

Authentication
==============

Requests for calling an API can be authenticated using either of the following methods:

-  Token-based authentication: Requests are authenticated using a token.
-  AK/SK-based authentication: Requests are authenticated by encrypting the request body using an AK/SK pair. AK/SK-based authentication is recommended because it is more secure than token-based authentication.

.. _dis_02_0517__en-us_topic_0183235768_en-us_topic_0181281305_dis_02_0517_en-us_topic_0121671869_section2417768214391:

Token-based Authentication
--------------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to a request to get permissions for calling the API.

When calling the API to obtain a user token, you must set **auth.scope** in the request body to **project**.

.. code-block::

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "id": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }

After a token is obtained, the X-Auth-Token header field must be added to requests to specify the token when calling other APIs, for example, the API used to query a connection list. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:

.. code-block::

   GET https://{{endpoint}}/v1/{project_id}/connections
   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....

AK/SK-based Authentication
--------------------------

.. note::

   AK/SK-based authentication supports API requests with a body not larger than 12 MB. For API requests with a larger body, token-based authentication is recommended.

In AK/SK-based authentication, AK/SK is used to sign requests and the signature is then added to the requests for authentication.

-  AK: access key ID, which is a unique identifier used in conjunction with a secret access key to sign requests cryptographically.
-  SK: secret access key used in conjunction with an AK to sign requests cryptographically. It identifies a request sender and prevents the request from being modified.

To obtain an access key, perform the following steps:

#. Log in to the management console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.

#. On the **My Credentials** page, choose **Access Keys**, and click **Create Access Key**. See :ref:`Figure 1 <dis_02_0517__en-us_topic_0183235768_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.

   .. _dis_02_0517__en-us_topic_0183235768_en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:

   .. figure:: /_static/images/en-us_image_0000001135802808.png
      :alt: **Figure 1** Clicking Create Access Key

      **Figure 1** Clicking Create Access Key

#. Click **OK** and save the access key file as prompted. The access key file will be saved to your browser's configured download location. Open the **credentials.csv** file to view **Access Key Id** and **Secret Access Key**.

   .. note::

      -  Only two access keys can be added for each user.
      -  To ensure access key security, the access key is automatically downloaded only when it is generated for the first time and cannot be obtained from the management console later. Keep them properly.

In AK/SK-based authentication, you can use an AK/SK to sign requests based on the signature algorithm or use the signing SDK to sign requests. For details about how to sign requests and use the signature SDK, see API Request Signing Guide.

.. important::

   The signing SDKs are only used for signing requests and different from the SDKs provided by services.
