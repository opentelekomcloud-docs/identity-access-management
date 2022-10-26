:original_name: en-us_topic_0057845553.html

.. _en-us_topic_0057845553:

Querying a Metadata File
========================

Function
--------

This API is used to query the content of the metadata file imported by an identity provider to the IAM system.

URI
---

-  URI format

   GET /v3-ext/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}/metadata

-  URI parameters

   ============= ========= ====== ===========================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ===========================
   idp_id        Yes       String ID of an identity provider.
   protocol \_id Yes       String ID of a protocol.
   ============= ========= ====== ===========================

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

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3-ext/OS-FEDERATION/identity_providers/ACME/protocols/saml/metadata

Response Parameters
-------------------

-  Parameters in the response body

   +---------------+-----------+--------+----------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                        |
   +===============+===========+========+====================================================+
   | id            | Yes       | String | ID of a metadata file.                             |
   +---------------+-----------+--------+----------------------------------------------------+
   | idp_id        | Yes       | String | ID of an identity provider.                        |
   +---------------+-----------+--------+----------------------------------------------------+
   | entity_id     | Yes       | String | **entityID** field in the metadata file.           |
   +---------------+-----------+--------+----------------------------------------------------+
   | protocol_id   | Yes       | String | ID of a protocol.                                  |
   +---------------+-----------+--------+----------------------------------------------------+
   | domain_id     | Yes       | String | ID of the domain that a user belongs to.           |
   +---------------+-----------+--------+----------------------------------------------------+
   | xaccount_type | Yes       | String | Domain source. The value is left empty by default. |
   +---------------+-----------+--------+----------------------------------------------------+
   | update_time   | Yes       | String | Time when a metadata file is imported or updated.  |
   +---------------+-----------+--------+----------------------------------------------------+
   | data          | Yes       | String | Content of a metadata file.                        |
   +---------------+-----------+--------+----------------------------------------------------+

-  Example response

   .. code-block::

      {
      "id": "40c174f35ff94e31b8257ad4991bce8b",
      "idp_id": "ACME",
      "entity_id": "https://idp.test.com/idp/shibboleth",
      "protocol_id": "saml",
      "domain_id": "ed7a77d365304f458f7d0a7909c6d889",
      "xaccount_type": "",
      "update_time": "2016-10-26T09:26:23.000000",
      "data": "$data"}

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
500         Internal server error.
=========== =========================================
