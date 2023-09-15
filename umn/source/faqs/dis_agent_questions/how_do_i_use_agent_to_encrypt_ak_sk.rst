:original_name: dis_faq_0021.html

.. _dis_faq_0021:

How Do I Use Agent to Encrypt AK/SK?
====================================

Secret Access Key (SK) is sensitive information. To encrypt the SK, perform the following steps:

#. Go to the **bin/** directory.

   **cd /opt/dis-agent-X.X.X/bin**

#. Run the encryption script, enter the password, and press **Enter**.

   **bash dis-encrypt.sh**

#. View the encryption result. The character string following "Encrypt result:" displayed on the console is the encryption result. Use this method to encrypt the MySQL password and SK, respectively and record the ciphertext in the configuration file.
