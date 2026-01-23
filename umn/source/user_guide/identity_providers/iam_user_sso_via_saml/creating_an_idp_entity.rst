:original_name: iam_08_0255.html

.. _iam_08_0255:

Creating an IdP Entity
======================

To establish a trust relationship between an enterprise IdP and the cloud platform, upload the metadata file of the cloud platform to the enterprise IdP, and then create an IdP entity and upload the metadata file of the enterprise IdP on the IAM console.

Establishing a Trust Relationship Between the Enterprise IdP and the Cloud Platform
-----------------------------------------------------------------------------------

Configure the metadata file of the cloud platform on the enterprise IdP to establish a trust.

#. Download the metadata file of the cloud platform.

   -  Web SSO: Visit https://auth.otc.t-systems.com/authui/saml/metadata.xml, right-click on the page, choose **Save As**, and set a file name, for example, **websso-metadata.xml**.

   -  SSO via API calling: Visit https://iam.eu-de.otc.t-systems.com/v3-ext/auth/OS-FEDERATION/SSO/metadata or https://iam.eu-nl.otc.t-systems.com/v3-ext/auth/OS-FEDERATION/SSO/metadata, right-click on the page, choose **Save As**, and set a file name, for example, **api-metadata-region.xml**.

      The cloud platform provides different API gateways for users in different regions to call APIs. To allow users to access resources in multiple regions, download metadata files of all these regions.

#. Upload the metadata file to the enterprise IdP server. For details, see the help documentation of the enterprise IdP.
#. Obtain the metadata file of the enterprise IdP. For details, see the help documentation of the enterprise IdP.

Creating an IdP Entity on the Cloud Platform
--------------------------------------------

To create an IdP entity on the IAM console, do as follows:

#. Log in to the IAM console, choose **Identity Providers** from the navigation pane, and click **Create Identity Provider** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001656300001.png
      :alt: **Figure 1** Creating an IdP entity

      **Figure 1** Creating an IdP entity

#. Specify the name, protocol, SSO type, status, and description of the IdP entity.


   .. figure:: /_static/images/en-us_image_0000001656340545.png
      :alt: **Figure 2** Setting IdP parameters

      **Figure 2** Setting IdP parameters

   .. table:: **Table 1** Basic parameters of an IdP

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | IdP name, which must be unique globally. You are advised to use the domain name.                                                                                                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | IdP protocol. The cloud platform supports SAML and OpenID Connect protocols. For details about OpenID Connect-based identity federation, see :ref:`Virtual User SSO via OpenID Connect <iam_08_0022>`.                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SSO Type                          | IdP type. An account can have only one type of IdP. The following describes the IAM user type.                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | IAM user SSO: After a federated user logs in to the cloud platform, the system automatically maps the :ref:`external identity ID <en-us_topic_0046661675__li13713193419317>` to an IAM user so that the federated user has the permissions of the mapped IAM user. An account can have only one IdP of the IAM user type. If you select the IAM user SSO, ensure that you have created an IAM user and set the external identity ID. For details, see :ref:`Creating a User <en-us_topic_0046611303>`. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | IdP status. The default value is **Enabled**.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Configuring the Metadata File of the Enterprise IdP on the Cloud Platform
-------------------------------------------------------------------------

You can upload the metadata file or manually edit metadata on the IAM console. For a metadata file larger than 500 KB, manually configure the metadata. If the metadata has been changed, upload the latest metadata file or edit the existing metadata to ensure that the federated users can log in to the cloud platform successfully.

.. note::

   For details about how to obtain the metadata file of an enterprise IdP, see the help documentation of the enterprise IdP.

-  **Upload a metadata file.**

   #. Click **Modify** in the row containing the IdP.


      .. figure:: /_static/images/en-us_image_0000001606781176.png
         :alt: **Figure 3** Modifying an IdP

         **Figure 3** Modifying an IdP

   #. Click **Select File** and select the metadata file of the enterprise IdP.


      .. figure:: /_static/images/en-us_image_0000001656580725.png
         :alt: **Figure 4** Uploading a metadata file

         **Figure 4** Uploading a metadata file

   #. Click **Upload**. The metadata extracted from the uploaded file is displayed. Click **OK**.

      -  If the uploaded metadata file contains multiple IdPs, select the IdP you want to use from the **Entity ID** drop-down list.
      -  If a message is displayed indicating that no entity ID is specified or the signing certificate has expired, check the metadata file and upload it again, or configure the metadata manually.

   #. Click **OK** to save the settings.

-  **Manually configure metadata.**

   #. Click **Manually configure**.


      .. figure:: /_static/images/en-us_image_0000001656341101.png
         :alt: **Figure 5** Manually configuring metadata

         **Figure 5** Manually configuring metadata

   #. In the **Configure Metadata** dialog box, set the metadata parameters, such as **Entity ID**, **Signing Certificate**, and **SingleSignOnService**.

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                                                                                                                                                                                                                                  |
      +=======================+=======================+==============================================================================================================================================================================================================================================================================+
      | Entity ID             | Yes                   | The unique identifier of an IdP. Enter the value of **entityID** displayed in the enterprise IdP's metadata file.                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | If the metadata file contains multiple IdPs, choose the one you want to use.                                                                                                                                                                                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol              | Yes                   | Protocol used for identity federation between an enterprise IdP and SP.                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | The protocol is selected by default.                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | NameIdFormat          | No                    | Enter the value of **NameIdFormat** displayed in the IdP metadata file.                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | It specifies the username identifier format supported by the IdP, which is used for communication between the IdP and federated user.                                                                                                                                        |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | If you configure multiple values, the cloud platform uses the first value by default.                                                                                                                                                                                        |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Signing Certificate   | Yes                   | Enter the value of **<X509Certificate>** displayed in the IdP metadata file.                                                                                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | A signing certificate is a public key certificate used for signature verification. For security purposes, enter a public key containing at least 2,048 bits. The signing certificate is used during identity federation to ensure that assertions are credible and complete. |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | If you configure multiple values, the cloud platform uses the first value by default.                                                                                                                                                                                        |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SingleSignOnService   | Yes                   | Enter the value of **SingleSignOnService** displayed in the IdP metadata file.                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | This parameter defines how SAML requests are sent during SSO. It must support HTTP Redirect or HTTP POST.                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | If you configure multiple values, the cloud platform uses the first value by default.                                                                                                                                                                                        |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SingleLogoutService   | No                    | Enter the value of **SingleLogoutService** displayed in the IdP metadata file.                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | This parameter indicates the address to which federated users will be redirected after logging out their sessions. It must support HTTP Redirect or HTTP POST.                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                              |
      |                       |                       | If you configure multiple values, the cloud platform uses the first value by default.                                                                                                                                                                                        |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      The following example shows the metadata file of an enterprise IdP and the manually configured metadata.


      .. figure:: /_static/images/en-us_image_0000001951269481.png
         :alt: **Figure 6** Metadata file of an enterprise IdP

         **Figure 6** Metadata file of an enterprise IdP

   #. Click **OK** to save the settings.
