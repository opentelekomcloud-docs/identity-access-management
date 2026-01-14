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

   =========== ========= ====== ===========================
   Parameter   Mandatory Type   Description
   =========== ========= ====== ===========================
   idp_id      Yes       String ID of an identity provider.
   protocol_id Yes       String ID of a protocol.
   =========== ========= ====== ===========================

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

   +-----------------------------------------------------------+-----------+--------+-----------------------+
   | Parameter                                                 | Mandatory | Type   | Description           |
   +===========================================================+===========+========+=======================+
   | :ref:`protocol <en-us_topic_0057845575__li3983238110289>` | Yes       | Object | Protocol information. |
   +-----------------------------------------------------------+-----------+--------+-----------------------+

-  .. _en-us_topic_0057845575__li3983238110289:

   protocol

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   mapping_id No        String Mapping ID.
   ========== ========= ====== ===========

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X PUT -d'{"protocol":{"mapping_id":"ACME"}}' https://sample.domain.com/v3/OS-FEDERATION/identity_providers/ACME/protocols/saml

Response Parameters
-------------------

-  Parameters in the response body

   +-------------------------------------------------------------+-----------+--------+-----------------------+
   | Parameter                                                   | Mandatory | Type   | Description           |
   +=============================================================+===========+========+=======================+
   | :ref:`protocol <en-us_topic_0057845575__li171961714172319>` | Yes       | Object | Protocol information. |
   +-------------------------------------------------------------+-----------+--------+-----------------------+

-  .. _en-us_topic_0057845575__li171961714172319:

   protocol

   +-------------------------------------------------------+--------+-------------------------------------+
   | Parameter                                             | Type   | Description                         |
   +=======================================================+========+=====================================+
   | id                                                    | String | Protocol ID.                        |
   +-------------------------------------------------------+--------+-------------------------------------+
   | mapping_id                                            | String | Mapping ID.                         |
   +-------------------------------------------------------+--------+-------------------------------------+
   | :ref:`links <en-us_topic_0057845575__li197002194250>` | Object | Protocol resource link information. |
   +-------------------------------------------------------+--------+-------------------------------------+

-  .. _en-us_topic_0057845575__li197002194250:

   protocol.links

   ================= ====== ================================
   Parameter         Type   Description
   ================= ====== ================================
   identity_provider String Identity provider resource link.
   self              String Resource link.
   ================= ====== ================================

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
