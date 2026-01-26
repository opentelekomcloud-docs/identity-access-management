:original_name: iam_08_0005.html

.. _iam_08_0005:

Configuring a Federated Login Entry in the Enterprise IdP
=========================================================

Configure a federated login entry in the enterprise IdP so that enterprise users can use the login link to access the cloud platform.

Prerequisites
-------------

-  An IdP entity has been created on the cloud platform. For details about how to create an IdP entity, see :ref:`Creating an IdP Entity <iam_08_0003>`.
-  The login entry for logging in to the cloud platform has been configured in the enterprise management system.

Procedure
---------

#. Log in to the IAM console. In the navigation pane, choose **Identity Providers**.

#. Click **View** in the row containing the IdP.


   .. figure:: /_static/images/en-us_image_0000001607219512.png
      :alt: **Figure 1** Viewing IdP details

      **Figure 1** Viewing IdP details

#. Copy the login link by clicking |image1| in the **Login Link** row.


   .. figure:: /_static/images/en-us_image_0000001607259280.png
      :alt: **Figure 2** Copying the login link

      **Figure 2** Copying the login link

#. Add the following statement to the page file of the enterprise management system:

   .. code-block::

      <a href="<Login link>"> Cloud platform login entry </a>

#. Log in to the enterprise management system using your enterprise account, and click the configured login link to access the cloud platform.

.. |image1| image:: /_static/images/en-us_image_0000001646367745.png
