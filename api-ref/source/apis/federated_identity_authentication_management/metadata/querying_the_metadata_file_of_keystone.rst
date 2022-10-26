:original_name: en-us_topic_0057845577.html

.. _en-us_topic_0057845577:

Querying the Metadata File of Keystone
======================================

Function
--------

This API is used to query the metadata file of the keystone.

URI
---

GET /v3-ext/auth/OS-FEDERATION/SSO/metadata

Request Parameters
------------------

-  Parameters in the request header

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                      |
   +===========+===========+=========+==================================================================================================================+
   | unsigned  | No        | Boolean | Whether to sign metadata according to SAML 2.0 specifications. The default value of this parameter is **false**. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      GET /v3-ext/auth/OS-FEDERATION/SSO/metadata

Response Parameters
-------------------

Example response

.. code-block::

   <md:EntityDescriptor xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata" ID="43ebac773925f6849b196a3c803baba5" entityID="https://www.example.com">
   <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
   <ds:SignedInfo>
   <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
   <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
   <ds:Reference URI="#43ebac773925f6849b196a3c803baba5">
   <ds:Transforms>
   <ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
   <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
   </ds:Transforms>
   <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
   <ds:DigestValue>yuQJc6OI3xilt6X4cOEUBnVV2Vs=</ds:DigestValue>
   </ds:Reference>
   </ds:SignedInfo>
   <ds:SignatureValue>...</ds:SignatureValue>
   <ds:KeyInfo>
   <ds:X509Data>
   <ds:X509Certificate>...</ds:X509Certificate>
   </ds:X509Data>
   </ds:KeyInfo>
   </ds:Signature>
   <md:SPSSODescriptor AuthnRequestsSigned="true" WantAssertionsSigned="true" protocolSupportEnumeration="urn:oasis:names:tc:SAML:2.0:protocol">
   <md:KeyDescriptor use="signing">
   <ds:KeyInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
   <ds:X509Data>
   <ds:X509Certificate>...</ds:X509Certificate>
   </ds:X509Data>
   </ds:KeyInfo>
   </md:KeyDescriptor>
   <md:KeyDescriptor use="encryption">
   <ds:KeyInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
   <ds:X509Data>
   <ds:X509Certificate>...</ds:X509Certificate>
   </ds:X509Data>
   </ds:KeyInfo>
   </md:KeyDescriptor>
   <md:NameIDFormat xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata">
   urn:oasis:names:tc:SAML:2.0:nameid-format:transient
   </md:NameIDFormat>
   <md:AssertionConsumerService xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata" Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST" Location="https://www.example.com/v3-ext/auth/OS-FEDERATION/SSO/SAML2/POST" index="0" isDefault="true"/>
   <md:AssertionConsumerService xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata" Binding="urn:oasis:names:tc:SAML:2.0:bindings:PAOS" Location="https://www.example.com/v3-ext/auth/OS-FEDERATION/SSO/SAML2/ECP" index="1"/>
   </md:SPSSODescriptor>
   </md:EntityDescriptor>

Status Code
-----------

=========== ==========================
Status Code Description
=========== ==========================
200         The request is successful.
500         Internal server error.
503         Service unavailable.
=========== ==========================
