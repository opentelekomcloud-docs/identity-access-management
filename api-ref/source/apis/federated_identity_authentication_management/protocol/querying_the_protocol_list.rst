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

   +------------------------------------------------------------+-----------+-----------------+-------------------------+
   | Parameter                                                  | Mandatory | Type            | Description             |
   +============================================================+===========+=================+=========================+
   | :ref:`protocols <en-us_topic_0057845644__li1648144524410>` | Yes       | List of objects | List of protocols.      |
   +------------------------------------------------------------+-----------+-----------------+-------------------------+
   | :ref:`links <en-us_topic_0057845644__li19101175031314>`    | Yes       | Object          | Protocol resource link. |
   +------------------------------------------------------------+-----------+-----------------+-------------------------+

-  .. _en-us_topic_0057845644__li1648144524410:

   protocols

   +--------------------------------------------------------+--------+-------------------------+
   | Parameter                                              | Type   | Description             |
   +========================================================+========+=========================+
   | id                                                     | String | ID of a protocol.       |
   +--------------------------------------------------------+--------+-------------------------+
   | mapping_id                                             | String | Mapping ID.             |
   +--------------------------------------------------------+--------+-------------------------+
   | :ref:`links <en-us_topic_0057845644__li9443135117132>` | Object | Protocol resource link. |
   +--------------------------------------------------------+--------+-------------------------+

-  .. _en-us_topic_0057845644__li19101175031314:

   links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845644__li9443135117132:

   protocols.links

   ================= ====== ================================
   Parameter         Type   Description
   ================= ====== ================================
   identity_provider String Identity provider resource link.
   self              String Resource link.
   ================= ====== ================================

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
