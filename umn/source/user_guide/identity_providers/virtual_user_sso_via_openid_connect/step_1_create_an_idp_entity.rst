:original_name: iam_08_0009.html

.. _iam_08_0009:

Step 1: Create an IdP Entity
============================

To establish a trust relationship between an enterprise IdP and the cloud platform, set the user redirect URLs and create OAuth 2.0 credentials in the enterprise IdP. On the IAM console, create an IdP entity and configure authorization information.

Prerequisites
-------------

-  The enterprise administrator has created an account in the cloud platform, and has created user groups and assigned them permissions in IAM. For details, see :ref:`Creating a User Group and Assigning Permissions <en-us_topic_0046611269>`. The user groups created in IAM will be mapped to federated users so that the federated users can obtain the permissions of the user groups to use cloud resources.
-  The enterprise administrator has read the help documentation of the enterprise IdP or has understood how to use the enterprise IdP. Configurations of different enterprise IdPs differ greatly, so they are not described in this document. For details about how to obtain the enterprise IdP's OAuth 2.0 credentials, see the IdP help documentation.

.. _iam_08_0009__en-us_topic_0272448422_section81252015115012:

Creating OAuth 2.0 Credentials in the Enterprise IdP
----------------------------------------------------

#. Set redirect URLs **https:///authui/oidc/redirect** and **https:///authui/oidc/post** in the enterprise IdP so that users can be redirected to the OpenID Connect IdP in the cloud platform.
#. Obtain OAuth 2.0 credentials of the enterprise IdP.

Creating an IdP Entity on the Cloud Platform
--------------------------------------------

Create an IdP entity and configure authorization information in IAM to establish a trust relationship between the enterprise IdP and IAM

#. Log in to the IAM console, choose **Identity Providers** from the navigation pane, and click **Create Identity Provider** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001656303721.png
      :alt: **Figure 1** Creating an IdP entity

      **Figure 1** Creating an IdP entity

#. Enter an IdP name, select **OpenID Connect** and **Enabled**, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001606944408.png
      :alt: **Figure 2** Setting IdP parameters

      **Figure 2** Setting IdP parameters

   .. note::

      The IdP name must be unique under your account.

Configuring Authorization Information in the Cloud Platform
-----------------------------------------------------------

#. Click **Modify** in the **Operation** column of the row containing the IdP you want to modify.


   .. figure:: /_static/images/en-us_image_0000001656344889.png
      :alt: **Figure 3** Modifying an IdP

      **Figure 3** Modifying an IdP

#. Select an access type.


   .. figure:: /_static/images/en-us_image_0000001606945160.png
      :alt: **Figure 4** Access type description

      **Figure 4** Access type description

   .. table:: **Table 1** Access type description

      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Access Type                                       | Description                                                                                                                                                     |
      +===================================================+=================================================================================================================================================================+
      | Programmatic access and management console access | -  Programmatic access: Federated users can use development tools (including APIs, CLI, and SDKs) that support key authentication to access the cloud platform. |
      |                                                   |                                                                                                                                                                 |
      |                                                   | -  Management console access: Federated users can log in to the cloud platform by using their own usernames and passwords.                                      |
      |                                                   |                                                                                                                                                                 |
      |                                                   |    Select this access type if you want users to access the cloud platform through SSO.                                                                          |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Programmatic access                               | Federated users can only use development tools (including APIs, CLI, and SDKs) that support key authentication to access the cloud platform.                    |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Specify the configuration information.

   .. table:: **Table 2** Configuration information

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================================================================================================+
      | Identity Provider URL             | URL of the OpenID Connect IdP.                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | Specify this parameter as the value of **issuer** in the **Openid-configuration**.                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |    **Openid-configuration** indicates a URL defined in OpenID Connect, containing configurations of an enterprise IdP. The URL format is **https://**\ *{base URL}*\ **/.well-known/openid-configuration**, where *base URL* is defined by the enterprise IdP. For example, the **Openid-configuration** of Google is **https://accounts.google.com/.well-known/openid-configuration**. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Client ID                         | ID of a client registered with the OpenID Connect IdP. The client ID is :ref:`an OAuth 2.0 credential created in the enterprise IdP <iam_08_0009__en-us_topic_0272448422_section81252015115012>`.                                                                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Authorization Endpoint            | Authorization endpoint of the OpenID Connect IdP. Specify this parameter as the value of **authorization_endpoint** in **Openid-configuration**.                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | This parameter is required only if you set **Access Type** to **Programmatic access and management console access**.                                                                                                                                                                                                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scopes                            | Scopes of authorization requests. **openid** is selected by default.                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | This parameter is required only if you set **Access Type** to **Programmatic access and management console access**.                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | Enumerated values:                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | -  openid                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   | -  email                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | -  profile                                                                                                                                                                                                                                                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Response Type                     | Response type of authorization requests. The default value is **id_token**.                                                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | This parameter is required only if you set **Access Type** to **Programmatic access and management console access**.                                                                                                                                                                                                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Response Mode                     | Response mode of authorization requests. The options include **form_post** and **fragment**. **form_post** is recommended.                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | This parameter is required only if you set **Access Type** to **Programmatic access and management console access**.                                                                                                                                                                                                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Signing Key                       | Public key used to sign the ID token of the OpenID Connect IdP. For account security purposes, change the signing key periodically.                                                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Verifying the Federated Login
-----------------------------

#. Click the login link displayed on the IdP details page and check if the login page of the enterprise IdP server is displayed.

   a. On the **Identity Providers** page, click **Modify** in the **Operation** column of the identity provider.

   b. Copy the login link displayed on the **Modify Identity Provider** page and visit the link using a browser.


      .. figure:: /_static/images/en-us_image_0000001656585157.png
         :alt: **Figure 5** Copying the login link

         **Figure 5** Copying the login link

   c. If the enterprise IdP login page is not displayed, check the configurations of the IdP and the enterprise IdP server.

#. Enter the username and password of a user that was created in the enterprise management system.

   -  If the login is successful, add the login link to the enterprise management system.
   -  If the login fails, check the username and password.

   .. note::

      Federated users only have read permissions for the cloud platform by default. To assign permissions to federated users, configure identity conversion rules for the IdP. For details, see :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0008>`.

Related Operations
------------------

-  Viewing IdP information: In the IdP list, click **View** in the row containing the IdP, and view its basic information, metadata, and identity conversion rules.

   .. note::

      To modify the configuration of an IdP, click **Modify** at the bottom of the details page.

-  Modifying an IdP: In the IdP list, click **Modify** in the row containing the IdP, and then change its status or modify the description, metadata, or identity conversion rules.
-  Deleting an IdP: In the IdP list, click **Delete** in the row containing the IdP, and click **Yes** in the displayed dialog box.

Follow-Up Procedure
-------------------

-  Configure identity conversion rules to map enterprise IdP users to IAM user groups and assign permissions to the users. For details, see :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0008>`.
-  Configure the enterprise management system to allow users to access the cloud platform through SSO. For details, see :ref:`(Optional) Step 3: Configure Login Link in the Enterprise Management System <iam_08_0007>`.
