:original_name: en-us_topic_0057845615.html

.. _en-us_topic_0057845615:

Importing a Metadata File
=========================

Function
--------

Before using the federated identity authentication function, a metadata file must be imported to the IAM system. This API is used to import a metadata file of a domain.

URI
---

-  URI format

   POST /v3-ext/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}/metadata

-  URI parameters

   ============= ========= ====== =====================
   Parameter     Mandatory Type   Description
   ============= ========= ====== =====================
   idp_id        Yes       String Identity provider ID.
   protocol \_id Yes       String Protocol ID.
   ============= ========= ====== =====================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.               |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Parameters in the request body

   +---------------+-----------+--------+----------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                              |
   +===============+===========+========+==========================================================+
   | xaccount_type | Yes       | String | Source of a domain. This field is left blank by default. |
   +---------------+-----------+--------+----------------------------------------------------------+
   | metadata      | Yes       | String | Content of the metadata file on the IdP server.          |
   +---------------+-----------+--------+----------------------------------------------------------+
   | domain_id     | Yes       | String | ID of the domain that a user belongs to.                 |
   +---------------+-----------+--------+----------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X POST -d '{"xaccount_type":"","domain_id":"ed7a77d365304f458f7d0a7909c6d889","metadata":"$metadataContent"}' https://sample.domain.com/v3-ext/OS-FEDERATION/identity_providers/ACME/protocols/saml/metadata

Response Parameters
-------------------

Example response

.. code-block::

   { "message": "Import metadata successful"}

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
201         The import is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
500         Internal server error.
=========== =========================================
