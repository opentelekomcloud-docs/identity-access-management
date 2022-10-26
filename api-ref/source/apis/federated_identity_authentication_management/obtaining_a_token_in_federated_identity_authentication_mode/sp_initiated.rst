:original_name: iam_02_0001.html

.. _iam_02_0001:

SP Initiated
============

OpenStack and Shibboleth are widely used open-source federated identity authentication solutions. They provide powerful SSO capabilities and connect users to various applications both inside and outside enterprises. This section describes how to use OpenStackClient and Shibboleth ECP Client to obtain the federated authentication token.

Flowchart
---------

The following figure shows the SP-initiated federation authentication process.


.. figure:: /_static/images/en-us_image_0000001419956277.png
   :alt: **Figure 1** Flowchart (SP-initiated)

   **Figure 1** Flowchart (SP-initiated)

Description
-----------

#. The client calls the API (federated token obtained in the SP-initiated mode) provided by the public cloud system.
#. The public cloud system searches for the metadata file based on the user and IdP information in the URL and sends the SAML request to the client.
#. The client encapsulates the SAML request and forwards the SAML request to the IdP.
#. A user enters a username and password on the IdP server for identity authentication.
#. After the user passes the authentication, IdP constructs an assertion carrying the user identity information and sends the SAML response. The response passes through the client.
#. The client encapsulates the SAML response and forwards the SAML response to the public cloud.
#. The public cloud verifies and authenticates the assertion, and generates a temporary access credential according to the identity conversion rule configured by users in the identity provider.
#. Users can access public cloud resources according to their permissions.

OpenStackClient
---------------

You must have permissions of user **root** to install the unified command-line client. To perform the following operations, you only need to have the permissions of a common user.

.. important::

   The API calling operation must be performed in a secure network environment (in a VPN or a cloud server of a domain). Otherwise, this operation may be under the man-in-the-middle (MITM) attack.

#. Create an environment variable file under the installation directory of OpenStackClient. Modify the environment variable file in a text editor. Add parameters, such as the username, password, region, SAML protocol version, and the IP address and port number of IAM, to the file. :ref:`Table 1 <iam_02_0001__table2616118811159>` describes the parameters.

   For example:

   **export OS_IDENTITY_API_VERSION=3**

   **export OS_AUTH_TYPE=v3samlpassword**

   **export OS_AUTH_URL=https://iam.eu-de.otc.t-systems.com:443/v3**

   **export OS_IDENTITY_PROVIDER=idpid**

   **export OS_PROTOCOL=saml**

   **export OS_IDENTITY_PROVIDER_URL=https://idp.example.com/idp/profile/SAML2/SOAP/ECP**

   **export OS_USERNAME=username**

   **export OS_PASSWORD=userpassword**

   **export OS_DOMAIN_NAME=example-domain-name**

   .. _iam_02_0001__table2616118811159:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                            |
      +===================================+========================================================================================================================+
      | OS_IDENTITY_API_VERSION           | Indicates the authentication API version. The value is fixed at **3**.                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_AUTH_TYPE                      | Indicates the authentication type. The value is fixed at **v3samlpassword**.                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_AUTH_URL                       | Indicates the authentication URL. The value format is **https://**\ *IAM* *IP address*:*Port number*/*API version*.    |
      |                                   |                                                                                                                        |
      |                                   | -  *Port number* is fixed at **443**.                                                                                  |
      |                                   | -  *API version* is fixed at **v3**.                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_IDENTITY_PROVIDER              | Indicates the name of an identity provider created by a user in the cloud system. For example: Publiccloud-Shibboleth. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_DOMAIN_NAME                    | Indicates the domain name to be authenticated.                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_PROTOCOL                       | Indicates the SAML protocol version. The value is fixed at **saml**.                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_IDENTITY_PROVIDER_URL          | Indicates the URL of the identity provider used to handle the authentication request initialized by the ECP.           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_USERNAME                       | Indicates the name of a user who is authenticated in the identity provider.                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+
      | OS_PASSWORD                       | Indicates the password of a user who is authenticated in the identity provider.                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------+

#. Run the following command to set environment variables:

   **source keystonerc**

#. Run the following command to obtain a token:

   **openstack token issue**

   .. code-block::

      >>openstack token issue
      command: token issue -> openstackclient.identity.v3.token.IssueToken (auth=True)
      Using auth plugin: v3samlpassword
      +-----------------------------------------------------------------------------------------------------------
      | Field   | Value
      | expires | 2018-04-16T03:46:51+0000
      | id      | MIIDbQYJKoZIhvcNAQcCoIIDXjXXX...
      | user_id | 9B7CJy5ME14f0fQKhb6HJVQdpXXX...

   In the command output, **id** is the obtained federated authentication token.

Shibboleth ECP Client
---------------------

#. Configure the **metadata-providers.xml** file in Shibboleth IdP v3 and save the **metadata.xml** file in the corresponding path.

   .. code-block::

      <MetadataProvider id="LocalMetadata1"xsi:type="FilesystemMetadataProvider" metadataFile="C:\Program Files (x86)\Shibboleth\IdP\metadata\web_metadata.xml"/>
      <MetadataProvider id="LocalMetadata2"xsi:type="FilesystemMetadataProvider" metadataFile="C:\Program Files (x86)\Shibboleth\IdP\metadata\api_metadata.xml"/>

   .. note::

      -  **MetadataProvider id** indicates the name of the downloaded metadata file of the SP system.
      -  **metadataFile** indicates the path for storing the metadata file of the SP system in the enterprise IdP.

#. Configure the **attribute-filter.xml** file in Shibboleth IdP v3.

   .. code-block::

      <afp:AttributeFilterPolicy id="example1">
          <afp:PolicyRequirementRule xsi:type="basic:AttributeRequesterString" value="https://auth.example.com/" />
          <afp:AttributeRule attributeID="eduPersonPrincipalName">
              <afp:PermitValueRule xsi:type="basic:ANY" />
          </afp:AttributeRule>
          <afp:AttributeRule attributeID="uid">
              <afp:PermitValueRule xsi:type="basic:ANY" />
          </afp:AttributeRule>
          <afp:AttributeRule attributeID="mail">
              <afp:PermitValueRule xsi:type="basic:ANY" />
          </afp:AttributeRule>
      </afp:AttributeFilterPolicy>

      <afp:AttributeFilterPolicy id="example2">
          <afp:PolicyRequirementRule xsi:type="basic:AttributeRequesterString" value="https://iam.{region_id}.example.com" />
          <afp:AttributeRule attributeID="eduPersonPrincipalName">
              <afp:PermitValueRule xsi:type="basic:ANY" />
          </afp:AttributeRule>
          <afp:AttributeRule attributeID="uid">
              <afp:PermitValueRule xsi:type="basic:ANY" />
          </afp:AttributeRule>
          <afp:AttributeRule attributeID="mail">
              <afp:PermitValueRule xsi:type="basic:ANY" />
          </afp:AttributeRule>
      </afp:AttributeFilterPolicy>

   .. note::

      **AttributeFilterPolicy id** indicates the name of the downloaded metadata file of the SP system.

      **value** indicates the **EntityID** in the metadata file of the SP system.

#. Configure the endpoint address of the enterprise IdP in the `ecp.py <https://wiki.shibboleth.net/confluence/display/SHIB2/Contributions#Contributions-simplepython>`__ script.

   .. code-block::

      # mapping from user friendly names or tags to IdP ECP enpoints
      IDP_ENDPOINTS = {
          "idp1": "https://idp.example.com/idp/profile/SAML2/SOAP/ECP"
      }

#. Run the **ecp.py** script to obtain the federated authentication token.

   .. code-block::

      >>python ecp.py
      Usage: ecp.py [options] IdP_tag target_url login
      >>python ecp.py -d idp1 https://iam.{region_id}.example.com/v3/OS-FEDERATION/identity_providers/idp_example/protocols/saml/auth {username}
      X-Subject-Token: MIIDbQYJKoZIhvcNAQcCoIIDXXX...

   **X-Subject-Token** is the obtained federated authentication token.
