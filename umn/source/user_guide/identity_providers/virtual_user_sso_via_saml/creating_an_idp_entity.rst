:original_name: iam_08_0003.html

.. _iam_08_0003:

Creating an IdP Entity
======================

To establish a trust relationship between an enterprise IdP and the cloud platform, upload the metadata file of the cloud platform to the enterprise IdP, and then create an IdP entity and upload the metadata file of the enterprise IdP on the IAM console.

Prerequisites
-------------

The enterprise administrator has read the help documentation of the enterprise IdP or has understood how to use the enterprise IdP. Configurations of different enterprise IdPs differ greatly, so they are not described in this document. For details about how to obtain the enterprise IdP's metadata file and how to upload the metadata file of the cloud platform to the enterprise IdP, see the IdP help documentation.

Establishing a Trust Relationship Between the Enterprise IdP and the Cloud Platform
-----------------------------------------------------------------------------------

The metadata file of the cloud platform needs to be configured in the enterprise IdP to establish a trust relationship between the two systems.

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


   .. figure:: /_static/images/en-us_image_0000001607217960.png
      :alt: **Figure 1** Creating an IdP entity

      **Figure 1** Creating an IdP entity

#. Specify the name, protocol, SSO type, status, and description of the IdP entity.


   .. figure:: /_static/images/en-us_image_0000001656578205.png
      :alt: **Figure 2** Setting IdP parameters

      **Figure 2** Setting IdP parameters

   .. table:: **Table 1** Basic parameters of an IdP

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================+
      | Name                              | IdP name, which must be unique globally. You are advised to use the domain name.                                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | IdP protocol. The cloud platform supports SAML and OpenID Connect protocols. For details about OpenID Connect-based identity federation, see :ref:`Virtual User SSO via OpenID Connect <iam_08_0022>`.      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | SSO Type                          | IdP type. An account can have only one type of IdP. The following describes the virtual user type.                                                                                                          |
      |                                   |                                                                                                                                                                                                             |
      |                                   | Virtual user SSO: After a federated user logs in to the cloud platform, the system automatically creates a virtual user for the federated user. An account can have multiple IdPs of the virtual user type. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | IdP status. The default value is **Enabled**.                                                                                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Configuring the Metadata File of the Enterprise IdP on the Cloud Platform
-------------------------------------------------------------------------

To configure the metadata file of the enterprise IdP in the cloud platform, you can upload the metadata file or manually edit metadata on the IAM console. For a metadata file larger than 500 KB, manually configure the metadata. If the metadata has been changed, upload the latest metadata file or edit the existing metadata to ensure that the federated users can log in to the cloud platform successfully.

.. note::

   For details about how to obtain the metadata file of an enterprise IdP, see the help documentation of the enterprise IdP.

-  **Upload a metadata file.**

   #. Click **Modify** in the row containing the IdP.


      .. figure:: /_static/images/en-us_image_0000001656458721.png
         :alt: **Figure 3** Modifying an IdP

         **Figure 3** Modifying an IdP

   #. Click **Select File** and select the metadata file of the enterprise IdP.


      .. figure:: /_static/images/en-us_image_0000001606779168.png
         :alt: **Figure 4** Uploading a metadata file

         **Figure 4** Uploading a metadata file

   #. Click **Upload**. The metadata extracted from the uploaded file is displayed. Click **OK**.

      -  If the uploaded metadata file contains multiple IdPs, select the IdP you want to use from the **Entity ID** drop-down list.
      -  If a message is displayed indicating that no entity ID is specified or the signing certificate has expired, check the metadata file and upload it again, or configure the metadata manually.

   #. Click **OK**.

-  **Manually configure metadata.**

   #. Click **Manually configure**.


      .. figure:: /_static/images/en-us_image_0000001606939052.png
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


      .. figure:: /_static/images/en-us_image_0272447834.png
         :alt: **Figure 6** Metadata file of an enterprise IdP

         **Figure 6** Metadata file of an enterprise IdP

   #. Click **OK**.

Related Operations
------------------

-  Viewing IdP information: In the IdP list, click **View** in the row containing the IdP, and view its basic information, metadata, and identity conversion rules.

   .. note::

      To modify the configuration of an IdP, click **Modify** at the bottom of the details page.

-  Modifying an IdP: In the IdP list, click **Modify** in the row containing the IdP, and then change its status or modify the description, metadata, or identity conversion rules.
-  Deleting an IdP: In the IdP list, click **Delete** in the row containing the IdP, and click **OK** in the displayed dialog box.

Follow-Up Procedure
-------------------

-  Configure the enterprise IdP: Configure enterprise IdP parameters to determine what information can be sent to the cloud platform.
-  Configure identity conversion rules: In the **Identity Conversion Rules** area, configure identity conversion rules to establish a mapping between enterprise users and IAM user groups. In this way, enterprise users can obtain the corresponding permissions in the cloud platform. For details, see :ref:`Configuring Identity Conversion Rules <iam_08_0004>`.
-  Verify the federated login: Check whether the enterprise user can log in to the cloud platform through SSO. For details, see :ref:`Verifying the Login <iam_08_0025>`.
