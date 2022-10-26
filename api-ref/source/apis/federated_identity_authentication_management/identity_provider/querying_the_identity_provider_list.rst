:original_name: en-us_topic_0057845581.html

.. _en-us_topic_0057845581:

Querying the Identity Provider List
===================================

Function
--------

This API is used to query the identity provider list.

URI
---

GET /v3/OS-FEDERATION/identity_providers

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

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/OS-FEDERATION/identity_providers

Response Parameters
-------------------

-  Parameters in the response body

   ================== ========= ====== ================================
   Parameter          Mandatory Type   Description
   ================== ========= ====== ================================
   identity_providers Yes       Array  List of identity providers.
   links              Yes       Object Identity provider resource link.
   ================== ========= ====== ================================

-  Description for the identity_providers format

   +-------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                                                                                                                                                                    |
   +=============+===========+=========+================================================================================================================================================================================================+
   | id          | Yes       | String  | ID of an identity provider.                                                                                                                                                                    |
   +-------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | Yes       | String  | Identity provider description.                                                                                                                                                                 |
   +-------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enabled     | Yes       | Boolean | Whether an identity provider is enabled. **true** indicates that the identity provider is enabled. **false** indicates that the identity provider is disabled. The default value is **false**. |
   +-------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remote_ids  | Yes       | Array   | Federated user ID list of an identity provider.                                                                                                                                                |
   +-------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links       | Yes       | Object  | Identity provider resource link.                                                                                                                                                               |
   +-------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "identity_providers": [
              {
                  "description": "Stores ACME identities",
                  "enabled": true,
                  "id": "ACME",
                  "remote_ids": [],
                  "links": {
                      "protocols": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME/protocols",
                      "self": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME"
                  }
              },
              {
                  "description": "Stores contractor identities",
                  "enabled": false,
                  "remote_ids": [],
                  "id": "ACME-contractors",

                  "links": {
                      "protocols": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME-contractors/protocols",
                      "self": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME-contractors"
                  }
              }
          ],
          "links": {
              "next": null,
              "previous": null,
              "self": "https://sample.domain.com/v3/OS-FEDERATION/identity_providers"
          }
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
