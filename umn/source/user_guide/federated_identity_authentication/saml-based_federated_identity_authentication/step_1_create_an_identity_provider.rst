:original_name: iam_08_0003.html

.. _iam_08_0003:

Step 1: Create an Identity Provider
===================================

To establish a trust relationship between an enterprise identity provider and the cloud system, upload the metadata file of the cloud system to the identity provider, and then create an identity provider and upload the metadata file of the identity provider on the IAM console.

Prerequisites
-------------

As an enterprise administrator, you have registered an account in the cloud system and created user groups and granted them permissions in IAM.

.. note::

   The user groups created in IAM will be used to assign permissions to identity provider users mapped to the cloud system.

.. _iam_08_0003__section122531649172219:

Establishing a Trust Relationship
---------------------------------

To establish a trust relationship between the enterprise identity provider and the cloud system, exchange their metadata files.

#. Download the metadata file of the cloud system. If both WebSSO and API calling need to be used, download the metadata files for the two functions.

   -  WebSSO: Visit https://auth.otc.t-systems.com/authui/saml/metadata.xml. Right-click, choose **Save As**, and set a file name, for example, **websso-metadata.xml**.

   -  API calling: Visit "https://*Endpoint address of a region*/v3-ext/auth/OS-FEDERATION/SSO/metadata", right-click on the page, choose **Save As**, and set a file name, for example, **api-metadata-region.xml**.

      The cloud system provides different API gateways for users in different regions to call APIs. To allow users to access resources in multiple regions, download metadata files of all these regions.

#. Upload the metadata file to the identity provider server. For details about how to upload the metadata file, see the documentation of your identity provider.
#. Obtain the metadata file of the enterprise identity provider. For details about how to obtain the metadata file, see the documentation of your identity provider.

Creating an Identity Provider
-----------------------------

Create an identity provider and configure the metadata file in IAM.

#. Log in to the IAM console, and choose **Identity Providers** from the navigation pane. Then click **Create Identity Provider**.
#. On the displayed page, enter an identity provider name, select **SAML** for **Protocol** and **Enabled** for **Status**. Then, click **OK**.

   .. note::

      The identity provider name must be unique under your account.

#. Click **OK**.

Configuring the Metadata File
-----------------------------

Configure the metadata file of the enterprise IdP in the cloud system.

IAM provides **preconfigured metadata**. You can directly use or modify the preconfigured metadata. If you have obtained the metadata file of your enterprise IdP, **upload** the file.

For a metadata file larger than 500 KB, manually configure the metadata. If the metadata has changed, upload the latest metadata file or edit the existing metadata to ensure that the federated users can log in to the cloud system.

.. note::

   For details about how to obtain the metadata file, see the documentation of the enterprise identity provider.

-  **Using preconfigured metadata**

   #. Click **Modify** in the row containing the identity provider.
   #. Click **Select** next to **Use preconfigured metadata**. The preconfigured enterprise IdPs and their metadata are displayed.
   #. Select an enterprise IdP, select the metadata, and click **OK**.
   #. Click **Configured Metadata** to view or modify the metadata.

-  **Uploading a metadata file**

   #. click **Modify** in the row containing the identity provider.
   #. Click **Select File** and select the metadata file you have obtained.
   #. Click **Upload**. The metadata extracted from the uploaded file is displayed. Click **OK**.

      -  If the uploaded metadata file contains multiple identity providers, select the identity provider you want to use from the **Entity ID** drop-down list.
      -  If a message is displayed indicating that no entity ID is specified or the signing certificate has expired, check the metadata file and upload it again, or configure the metadata manually.

   #. Click **OK**.

-  **Manually configuring metadata**

   #. Click **Manually configure**.
   #. In the **Configure Metadata** dialog box, set the metadata parameters, such as the entity ID, signing certificate, and **SingleSignOnService**.

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================================================================================================================================================+
      | Entity ID             | Yes                   | The unique identifier of an identity provider. Enter the value of **entityID** displayed in the identity provider metadata file.                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                                                                                               |
      |                       |                       | If the metadata file contains multiple identity providers, choose the one you want to use.                                                                                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol              | Yes                   | The SAML protocol is used for federated identity authentication between an enterprise identity provider and service provider.                                                                                                                                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | NameIdFormat          | No                    | Enter the value of **NameIdFormat** displayed in the metadata file.                                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                                                               |
      |                       |                       | This parameter indicates the username and ID format used for communication between the identity provider and federated users.                                                                                                                                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Signing Certificate   | Yes                   | Enter the value of **<X509Certificate>** displayed in the metadata file.                                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                               |
      |                       |                       | A signing certificate is a public key certificate used for signature verification. For security purposes, enter a public key containing no less than 2048 bits. The signing certificate is used during federated identity authentication to ensure that assertions are credible and complete. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SingleSignOnService   | Yes                   | Enter the value of **SingleSignOnService** displayed in the metadata file.                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                               |
      |                       |                       | This parameter defines how SAML requests are sent during the SSO process. **SingleSignOnService** must support HTTP Redirect or HTTP POST.                                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SingleLogoutService   | No                    | Enter the value of **SingleLogoutService** displayed in the metadata file.                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                               |
      |                       |                       | This parameter indicates the address to which federated users will be redirected after logging out their sessions. The **SingleLogoutService** parameter in the metadata file must support HTTP Redirect or HTTP POST.                                                                        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   #. Click **OK**.

-  Click **OK** to save the settings.

Logging In as a Federated User
------------------------------

#. Click the login link displayed on the identity provider details page to check if the login page of the identity provider server is displayed.

   a. On the **Identity Providers** page, click **View** in the **Operation** column of the identity provider. Copy the login link displayed on the identity provider details page and visit the link using a browser.
   b. If the login page is not displayed, check the metadata file and configurations of the identity provider server.

#. Enter the username and password of a user that was created in the enterprise management system.

   -  If the login is successful, add the login link to the enterprise's official website.
   -  If the login fails, check the username and password.

   .. note::

      Federated users only have read permissions for the cloud system by default. To assign permissions to federated users, configure identity conversion rules for the identity provider. For more information, see :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0004>`.

Related Operations
------------------

-  Viewing identity provider information: In the identity provider list, click **View** in the row containing the identity provider, and view its basic information, metadata, and identity conversion rules.

   .. note::

      To modify the configurations of an identity provider, click **Modify** at the bottom of the details page.

-  Modifying an identity provider: In the identity provider list, click **Modify** in the row containing the identity provider, and then change its status and modify the description, metadata, and identity conversion rules.
-  Deleting an identity provider: In the identity provider list, click **Delete** in the row containing the identity provider, and click **Yes**.

Follow-Up Procedure
-------------------

-  In the **Identity Conversion Rules** area, create an identity conversion rule. For details, see :ref:`Step 2: Configure Identity Conversion Rules <iam_08_0004>`.
-  Configure the enterprise management system to allow users to access the cloud system through SSO. For details, see :ref:`Step 3: Configure Login Link in the Enterprise Management System <iam_08_0005>`.
