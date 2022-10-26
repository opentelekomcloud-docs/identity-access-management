:original_name: en-us_topic_0057845606.html

.. _en-us_topic_0057845606:

Creating a SAML Identity Provider
=================================

Function
--------

This API is used to create a SAML identity provider.

URI
---

-  URI format

   PUT /v3/OS-FEDERATION/identity_providers/{id}

-  URI parameters

   ========= ========= ====== ===========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========================
   id        Yes       String ID of an identity provider.
   ========= ========= ====== ===========================

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

   +-------------------+-----------------+-----------------+----------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                    |
   +===================+=================+=================+================================================================+
   | identity_provider | Yes             | JSON object     | Request body for registering an identity provider.             |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------+
   | description       | No              | String          | Identity provider description.                                 |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------+
   | enabled           | No              | Boolean         | Whether an identity provider is enabled.                       |
   |                   |                 |                 |                                                                |
   |                   |                 |                 | -  **true** indicates that the identity provider is enabled.   |
   |                   |                 |                 | -  **false** indicates that the identity provider is disabled. |
   |                   |                 |                 |                                                                |
   |                   |                 |                 | The default value is **false**.                                |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X PUT -d'{"identity_provider":{"description":"Stores ACME identities.","enabled":true}}' https://sample.domain.com/v3/OS-FEDERATION/identity_providers/ACME

Response Parameters
-------------------

-  Parameters in the response body

   +-------------+-----------+---------+------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                                            |
   +=============+===========+=========+========================================================================+
   | id          | Yes       | String  | ID of an identity provider.                                            |
   +-------------+-----------+---------+------------------------------------------------------------------------+
   | description | Yes       | String  | Identity provider description.                                         |
   +-------------+-----------+---------+------------------------------------------------------------------------+
   | enabled     | Yes       | Boolean | Whether an identity provider is enabled.                               |
   +-------------+-----------+---------+------------------------------------------------------------------------+
   | remote_ids  | Yes       | Array   | Federated user ID list of an identity provider.                        |
   +-------------+-----------+---------+------------------------------------------------------------------------+
   | links       | Yes       | Object  | Identity provider resource link, including **protocols** and **self**. |
   +-------------+-----------+---------+------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "identity_provider": {
              "description": "Stores ACME identities",
              "enabled": true,
              "id": "ACME",

              "remote_ids": [],
              "links": {
                  "protocols": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME/protocols",
                  "self": "https://example.com/v3/OS-FEDERATION/identity_providers/ACME"
              }
          }
      }

Status Codes
------------

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
| 409         | Duplicate identity provider ID.                                                |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
