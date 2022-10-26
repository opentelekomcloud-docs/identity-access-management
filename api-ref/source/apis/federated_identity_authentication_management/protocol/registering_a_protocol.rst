:original_name: en-us_topic_0057845575.html

.. _en-us_topic_0057845575:

Registering a Protocol
======================

Function
--------

This API is used to register a protocol, that is, associate a rule with an identity provider.

URI
---

-  URI format

   PUT /v3/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}

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

-  Parameters in the request body

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   mapping_id Yes       String Mapping ID.
   ========== ========= ====== ===========

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X PUT -d'{"protocol":{"mapping_id":"ACME"}}' https://sample.domain.com/v3/OS-FEDERATION/identity_providers/ACME/protocols/saml

Response Parameters
-------------------

-  Parameters in the response body

   ========== ========= ====== =======================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =======================
   id         Yes       String ID of a protocol.
   mapping_id Yes       String Mapping ID.
   links      Yes       Object Protocol resource link.
   ========== ========= ====== =======================

-  Example response

   .. code-block::

      {
          "protocol": {
              "id": "saml",
              "links": {
                  "identity_provider": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME",
                  "self": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME/protocols/saml"
              },
              "mapping_id": "ACME"
          }
      }

**Status Codes**
----------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 201         | The request is successful.                                                     |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                        |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
