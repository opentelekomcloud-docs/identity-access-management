:original_name: iam_08_0252.html

.. _iam_08_0252:

Configuring an Enterprise IdP
=============================

You can configure parameters in the enterprise IdP to determine what information will be sent to the cloud platform. The cloud platform authenticates the federated identity and assigns permissions based on the received information and identity conversion rules.

Common Parameters in an Enterprise IdP
--------------------------------------

.. table:: **Table 1** Common parameters in an enterprise IdP

   +----------------------------------+--------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
   | Parameter                        | Description                                                              | Scenario                                                                                 |
   +==================================+==========================================================================+==========================================================================================+
   | IAM_SAML_Attributes_redirect_url | Target URL which the federated user will be redirected to                | During SSO login, the federated user will be redirected to a page on the cloud platform. |
   +----------------------------------+--------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
   | IAM_SAML_Attributes_domain_id    | Account ID of the cloud platform to be federated with the enterprise IdP | This parameter is mandatory in the enterprise IdP-initiated federation.                  |
   +----------------------------------+--------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
   | IAM_SAML_Attributes_idp_id       | Name of the IdP entity created on the cloud platform                     | This parameter is mandatory in the enterprise IdP-initiated federation.                  |
   +----------------------------------+--------------------------------------------------------------------------+------------------------------------------------------------------------------------------+
