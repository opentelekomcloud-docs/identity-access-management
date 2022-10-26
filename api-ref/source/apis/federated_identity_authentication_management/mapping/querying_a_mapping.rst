:original_name: en-us_topic_0057845645.html

.. _en-us_topic_0057845645:

Querying a Mapping
==================

Function
--------

This API is used to query the information about a mapping.

URI
---

-  URI format

   GET /v3/OS-FEDERATION/mappings/{id}

-  URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   id        Yes       String Mapping ID.
   ========= ========= ====== ===========

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

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/OS-FEDERATION/mappings/ACME

Response Parameters
-------------------

-  Parameters in the response body

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================================================================================+
   | id              | Yes             | String          | Mapping ID.                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | rules           | Yes             | Object          | Rule used to map federated users to local users                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | Example rule for SAML:                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | .. code-block::                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 |     "rules": [                                                                                                                                                                                                 |
   |                 |                 |                 |                {                                                                                                                                                                                               |
   |                 |                 |                 |                    "local": [                                                                                                                                                                                  |
   |                 |                 |                 |                        {                                                                                                                                                                                       |
   |                 |                 |                 |                            "user": {                                                                                                                                                                           |
   |                 |                 |                 |                                "name": "{0}"                                                                                                                                                                   |
   |                 |                 |                 |                            }                                                                                                                                                                                   |
   |                 |                 |                 |                        },                                                                                                                                                                                      |
   |                 |                 |                 |                        {                                                                                                                                                                                       |
   |                 |                 |                 |                            "group": {                                                                                                                                                                          |
   |                 |                 |                 |                                "name": "0cd5e9"                                                                                                                                                                |
   |                 |                 |                 |                            }                                                                                                                                                                                   |
   |                 |                 |                 |                        }                                                                                                                                                                                       |
   |                 |                 |                 |                    ],                                                                                                                                                                                          |
   |                 |                 |                 |                    "remote": [                                                                                                                                                                                 |
   |                 |                 |                 |                        {                                                                                                                                                                                       |
   |                 |                 |                 |                            "type": "UserName"                                                                                                                                                                  |
   |                 |                 |                 |                        },                                                                                                                                                                                      |
   |                 |                 |                 |                        {                                                                                                                                                                                       |
   |                 |                 |                 |                            "type": "orgPersonType",                                                                                                                                                            |
   |                 |                 |                 |                            "not_any_of": [                                                                                                                                                                     |
   |                 |                 |                 |                                "Contractor",                                                                                                                                                                   |
   |                 |                 |                 |                                "Guest"                                                                                                                                                                         |
   |                 |                 |                 |                            ]                                                                                                                                                                                   |
   |                 |                 |                 |                        }                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 |                    ]                                                                                                                                                                                           |
   |                 |                 |                 |                }                                                                                                                                                                                               |
   |                 |                 |                 |            ]                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **local**: indicates the information about a federated user in the cloud system.                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | -  **user**: indicates the name of a federated user in the cloud system. **{0}** indicates the first attribute of the user information in **remote**.                                                          |
   |                 |                 |                 | -  **group**: indicates the user group to which a federated user belongs in the cloud system.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | **remote**: indicates the information about a federated user in the IdP. This expression is a combination of assertion attributes and operators. The value of **remote** is determined based on the assertion. |
   |                 |                 |                 |                                                                                                                                                                                                                |
   |                 |                 |                 | -  **"type": "UserName"** indicates an attribute in an IdP assertion.                                                                                                                                          |
   |                 |                 |                 | -  **"type": "orgPersonType"** indicates an attribute in an IdP assertion.                                                                                                                                     |
   |                 |                 |                 | -  **not_any_of**: The rule is not matched if any of the specified strings appear in the attribute type. The condition result is Boolean, not the argument that is passed as input.                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links           | Yes             | Object          | Mapping resource link.                                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "mapping": {
              "id": "ACME",
              "links": {
                  "self": "https://example.com/v3/OS-FEDERATION/mappings/ACME"
              },
              "rules": [
                  {
                      "local": [
                          {
                              "user": {
                                  "name": "{0}"
                              }
                          },
                          {
                              "group": {
                                  "name": "0cd5e9"
                              }
                          }
                      ],
                      "remote": [
                          {
                              "type": "UserName"
                          },
                          {
                              "type": "orgPersonType",
                              "not_any_of": [
                                  "Contractor",
                                  "Guest"
                              ]
                          }
                      ]
                  }
              ]
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
