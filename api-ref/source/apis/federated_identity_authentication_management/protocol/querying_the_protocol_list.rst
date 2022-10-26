:original_name: en-us_topic_0057845644.html

.. _en-us_topic_0057845644:

Querying the Protocol List
==========================

Function
--------

This API is used to query the protocol list.

URI
---

-  URI format

   GET /v3/OS-FEDERATION/identity_providers/{idp_id}/protocols

-  URI parameters

   ========= ========= ====== ===========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========================
   idp_id    Yes       String ID of an identity provider.
   ========= ========= ====== ===========================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token.                                  |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/OS-FEDERATION/identity_providers/ACME/protocols/

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =============== =======================
   Parameter Mandatory Type            Description
   ========= ========= =============== =======================
   protocols Yes       List of objects List of protocols.
   links     Yes       Object          Protocol resource link.
   ========= ========= =============== =======================

-  protocols parameter description

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
          "links": {
              "next": null,
              "previous": null,
              "self": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME/protocols"
          },
          "protocols": [
              {
                  "id": "saml",
                  "links": {
                      "identity_provider": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME",
                      "self": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME/protocols/saml"
                  },
                  "mapping_id": "ACME"
              }
          ]
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 200         | The request is successful.                                                     |
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
