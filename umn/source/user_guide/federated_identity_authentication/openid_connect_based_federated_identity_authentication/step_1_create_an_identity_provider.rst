:original_name: iam_08_0009.html

.. _iam_08_0009:

Step 1: Create an Identity Provider
===================================

To establish a trust relationship between an enterprise identity provider and the cloud system, create an identity provider and configure authorization information on the IAM console, and set the user redirect URLs and create OAuth 2.0 credentials in the enterprise identity provider.

Prerequisites
-------------

As an enterprise administrator, you have registered an account in the cloud system and created user groups and granted them permissions in IAM.

.. note::

   The user groups created in IAM will be used to assign permissions to identity provider users mapped to the cloud system.

.. _iam_08_0009__section1114401807:

Creating OAuth 2.0 Credentials in the Enterprise Identity Provider
------------------------------------------------------------------

#. The enterprise IdP redirects users to an OpenID Connect identity provider on the cloud platform through a browser. In the IdP system, set the redirect URLs to the following:

   **https://auth.otc.t-systems.com/authui/oidc/redirect** and **https://auth.otc.t-systems.com/authui/oidc/post**

#. Obtain OAuth 2.0 credentials (see :ref:`Table 2 <iam_08_0009__table563516315348>`) of the enterprise IdP. For details, see the documentation of your enterprise IdP.

Creating an Identity Provider
-----------------------------

Create an identity provider and configure authorization information in IAM.

#. Log in to the IAM console, and choose **Identity Providers** from the navigation pane. Then click **Create Identity Provider**.
#. Enter an identity provider name, select **OpenID Connect** and **Enabled**, and click **OK**.

   .. note::

      The identity provider name must be unique under your account.

Configuring Authorization Information
-------------------------------------

#. Click **Modify** in the **Operation** column of the row containing the identity provider you want to modify.

#. Select an access type.

   .. table:: **Table 1** Access type

      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Access Type                                       | Description                                                                                                                                                                                                                       |
      +===================================================+===================================================================================================================================================================================================================================+
      | Programmatic access and management console access | -  Programmatic access: Federated users can obtain a token for the cloud system by using an ID token and then use development tools (including APIs, CLI, and SDKs) that support token authentication to access the cloud system. |
      |                                                   |                                                                                                                                                                                                                                   |
      |                                                   | -  Management console access: Federated users can log in to the management console by using their own usernames and passwords.                                                                                                    |
      |                                                   |                                                                                                                                                                                                                                   |
      |                                                   |    **Select this access type if you want to access the cloud system using SSO.**                                                                                                                                                  |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Programmatic access                               | Federated users can only obtain a token for the cloud system by using an ID token and then use development tools (including APIs, CLI, and SDKs) that support token authentication to access the cloud system.                    |
      +---------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Specify the configuration information.

   .. _iam_08_0009__table563516315348:

   .. table:: **Table 2** Configuration information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================================================================================+
      | Identity Provider URL             | URL of the OpenID Connect identity provider.                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | Specify this parameter as the value of **issuer** in the **Openid-configuration**.                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | .. note::                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   |    **Openid-configuration** indicates a URL defined in OpenID Connect, containing configurations of an enterprise identity provider. The URL format is *https://{base URL}/.well-known/openid-configuration*, where *base URL* is defined by the enterprise identity provider. |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   |    For example, the **Openid-configuration** of Google is **https://accounts.google.com/.well-known/openid-configuration**. Therefore, the identity provider URL is **https://accounts.google.com**.                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Client ID                         | ID of a client registered with the OpenID Connect identity provider. that is, :ref:`an OAuth 2.0 credential created in the enterprise identity provider <iam_08_0009__section1114401807>`.                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Authorization Endpoint            | Authorization endpoint of the OpenID Connect identity provider. Specify this parameter as the value of **authorization_endpoint** in the **Openid-configuration**.                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | **This parameter is required only if you set Access Type to Programmatic access and management console access.**                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scopes                            | Scopes of authorization requests. **openid** is selected by default.                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | **This parameter is required only if you set Access Type to Programmatic access and management console access.**                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | Enumerated values:                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | -  openid                                                                                                                                                                                                                                                                      |
      |                                   | -  email                                                                                                                                                                                                                                                                       |
      |                                   | -  profile                                                                                                                                                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Response Type                     | Response type of authorization requests. The default value is **id_token**.                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | **This parameter is required only if you set Access Type to Programmatic access and management console access.**                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Response Mode                     | Response mode of authorization requests. The options include **form_post** and **fragment**. **form_post** is recommended.                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | -  **form_post**: If this mode is selected, set the redirect URL to **http://auth.**\ *example*\ **.com/authul/oidc/post** in the enterprise identity provider.                                                                                                                |
      |                                   | -  **fragment**: If this mode is selected, set the redirect URL to **https://auth.**\ *example*\ **.com/authui/oidc/redirect** in the enterprise identity provider.                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | **This parameter is required only if you set Access Type to Programmatic access and management console access.**                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Signing Key                       | Public key used to sign the ID token of the OpenID Connect identity provider. For example: **NqMhxWVZf2PcPQRc6aBlpd3k...**                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   | .. note::                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                |
      |                                   |    For account security purposes, **change the signing key periodically**.                                                                                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Logging In as a Federated User
------------------------------

#. Click the login link displayed on the identity provider details page to check if the login page of the IdP server is displayed.

   a. On the **Identity Providers** page, click **View** in the **Operation** column of the identity provider.
   b. Copy the login link displayed on the identity provider details page and visit the link using a browser.
   c. If the identity provider login page is not displayed, check the configurations of the identity provider and the identity provider server.

#. Enter the username and password of a user that was created in the enterprise management system.

   -  If the login is successful, add the login link to the enterprise's official website.
   -  If the login fails, check the username and password.

   .. note::

      Federated users only have read permissions for the cloud system by default. To assign permissions to federated users, configure identity conversion rules for the identity provider. For more information, see :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0008>`.

Related Operations
------------------

-  Viewing identity provider information: In the identity provider list, click **View** in the row containing the identity provider, and view its basic information, access type, configurations, and identity conversion rules.

   .. note::

      To modify the configurations of an identity provider, click **Modify** at the bottom of the details page.

-  Modifying an identity provider: In the identity provider list, click **Modify** in the row containing the identity provider, and then change its status and modify the description, access type, configurations, and identity conversion rules.
-  Deleting an identity provider: In the identity provider list, click **Delete** in the row containing the identity provider, and click **Yes**.

Follow-Up Procedure
-------------------

-  Configure identity conversion rules to map identity provider users to IAM user groups. For details, see :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0008>`.
-  Configure the enterprise management system to allow users to access the cloud system through SSO. For details, see :ref:`Step 3: Configure Login Link in the Enterprise Management System <iam_08_0007>`.
