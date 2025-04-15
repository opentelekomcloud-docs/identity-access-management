:original_name: en-us_topic_0064274720.html

.. _en-us_topic_0064274720:

Obtaining an Agency Token
=========================

Function
--------

This API is used to obtain an agency token. For example, after a trust relationship is established between account A (delegating party) and account B (delegated party), the delegated party B can use this API to obtain an agency token to manage A's resources that B is delegated to manage. However, B cannot use this agency token to manage its own resources. To do so, B needs to obtain a token by referring to :ref:`Obtaining a User Token <en-us_topic_0057845583>`.

.. note::

   The validity period of a token is **24 hours**. Cache the token to prevent frequent API calling. Ensure that the token is valid while you use it. Using a token that will soon expire may cause API calling failures. Obtaining a new token does not affect the validity of the existing token.

URI
---

POST /v3/auth/tokens

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+--------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                    |
   +==============+===========+========+================================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.                          |
   +--------------+-----------+--------+--------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Token that assigns the permissions of the **Agent Operator** policy to user B. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------+

-  Parameters in the request body

   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory       | Type            | Description                                                                                                                      |
   +==========================+=================+=================+==================================================================================================================================+
   | identity                 | Yes             | JSON object     | Authentication parameters, including: **methods** and **assume_role**.                                                           |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 | .. code-block::                                                                                                                  |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 |    "identity": {                                                                                                                 |
   |                          |                 |                 |          "methods": ["assume_role"],                                                                                             |
   |                          |                 |                 |          "assume_role": {                                                                                                        |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | methods                  | Yes             | String Array    | Method for obtaining the token. Set this field to **assume_role**.                                                               |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | domain_name or domain_id | Yes             | String          | Domain name or domain ID of the delegating party A. Specify either **domain_name** or **domain_id**.                             |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | xrole_name               | Yes             | String          | Name of the agency created by A.                                                                                                 |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | scope                    | No              | JSON object     | Usage scope of the token. The value can be **project** or **domain**.                                                            |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 | -  If this field is set to **project**, the token can only be used to access resources in the project of a specified ID or name. |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 |    .. code-block::                                                                                                               |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 |       "scope": {                                                                                                                 |
   |                          |                 |                 |             "project": {                                                                                                         |
   |                          |                 |                 |             "id": "0b95b78b67fa045b38104c12fb..."                                                                                |
   |                          |                 |                 |             }                                                                                                                    |
   |                          |                 |                 |           }                                                                                                                      |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 | -  If this field is set to **domain**, the token can be used to access all resources under the domain of a specified ID or name. |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 |    .. code-block::                                                                                                               |
   |                          |                 |                 |                                                                                                                                  |
   |                          |                 |                 |       "scope": {                                                                                                                 |
   |                          |                 |                 |             "domain": {                                                                                                          |
   |                          |                 |                 |             "id": "6b8eb224c76842e3ac2..."                                                                                       |
   |                          |                 |                 |             }                                                                                                                    |
   |                          |                 |                 |           }                                                                                                                      |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   The following is a sample request for obtaining an agency token for **domain A**. The name of the agency is **agencytest**.

   .. code-block::

      {
          "auth":{
              "identity":{
                  "methods":[
                      "assume_role"
                  ],
                  "assume_role":{
                      "domain_name":"domain A",
                      "xrole_name":"agencytest"
                      }
              },
              "scope":{
                  "domain":{
                      "name":"domain A"
                  }
              }
           }
      }

Response Parameters
-------------------

-  Parameters in the response header

   =============== ========= ====== ==============================
   Parameter       Mandatory Type   Description
   =============== ========= ====== ==============================
   X-Subject-Token Yes       String Agency token that is obtained.
   =============== ========= ====== ==============================

-  Token format description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | methods         | Yes             | Json Array      | Method for obtaining the token.                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | expires_at      | Yes             | String          | Expiration date of the token.                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | issued_at       | Yes             | String          | Time when the token was issued.                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | user            | Yes             | JSON object     | Detailed information about the delegating party. Example:                                                                                         |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "user": {                                                                                                                                      |
   |                 |                 |                 |          "name": "user A",                                                                                                                        |
   |                 |                 |                 |          "id": "userid",                                                                                                                          |
   |                 |                 |                 |          "password_expires_at":"2016-11-06T15:32:17.000000",                                                                                      |
   |                 |                 |                 |          "domain": {                                                                                                                              |
   |                 |                 |                 |             "name": "domain A",                                                                                                                   |
   |                 |                 |                 |             "id": "domainid"                                                                                                                      |
   |                 |                 |                 |           }                                                                                                                                       |
   |                 |                 |                 |        }                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **user.name**: Username of the delegating party.                                                                                               |
   |                 |                 |                 | -  **user.id**: User ID of the delegating party.                                                                                                  |
   |                 |                 |                 | -  **domain.name**: Name of the domain which the delegating party belongs to.                                                                     |
   |                 |                 |                 | -  **domain.id**: ID of the domain which the delegating party belongs to.                                                                         |
   |                 |                 |                 | -  **password_expires_at**: Time when the password will expire. **null** indicates that the password will not expire. This parameter is optional. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain          | No              | JSON object     | This parameter is returned only when the **scope** parameter in the request body has been set to **domain**.                                      |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "domain": {                                                                                                                                    |
   |                 |                 |                 |          "name" : "domain A",                                                                                                                     |
   |                 |                 |                 |          "id" : "domainid"                                                                                                                        |
   |                 |                 |                 |    }                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **domain.name**: Name of the domain which the delegating party belongs to.                                                                     |
   |                 |                 |                 | -  **domain.id**: ID of the domain which the delegating party belongs to.                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | project         | No              | JSON object     | This parameter is returned only when the **scope** parameter in the request body has been set to **project**.                                     |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "project": {                                                                                                                                   |
   |                 |                 |                 |          "name": "projectname",                                                                                                                   |
   |                 |                 |                 |          "id": "projectid"                                                                                                                        |
   |                 |                 |                 |    }                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **project.name**: Name of a project.                                                                                                           |
   |                 |                 |                 | -  **project.id**: ID of the project.                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | catalog         | No              | Json Array      | Endpoint information.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "catalog": [{                                                                                                                                  |
   |                 |                 |                 |        "type": "identity",                                                                                                                        |
   |                 |                 |                 |        "id": "1331e5cff2a74d76b03da1225910e31d",                                                                                                  |
   |                 |                 |                 |        "name": "iam",                                                                                                                             |
   |                 |                 |                 |        "endpoints": [{                                                                                                                            |
   |                 |                 |                 |            "url": "https://sample.domain.com/v3",                                                                                                 |
   |                 |                 |                 |            "region": "*",                                                                                                                         |
   |                 |                 |                 |            "region_id": "*",                                                                                                                      |
   |                 |                 |                 |            "interface": "public",                                                                                                                 |
   |                 |                 |                 |            "id": "089d4a381d574308a703122d3ae738e9"                                                                                               |
   |                 |                 |                 |        }]                                                                                                                                         |
   |                 |                 |                 |    }]                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | roles           | Yes             | JSON object     | Permissions information of the token.                                                                                                             |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "roles" : [{                                                                                                                                   |
   |                 |                 |                 |         "name" : "role1",                                                                                                                         |
   |                 |                 |                 |         "id" : "roleid1"                                                                                                                          |
   |                 |                 |                 |         }, {                                                                                                                                      |
   |                 |                 |                 |         "name" : "role2",                                                                                                                         |
   |                 |                 |                 |         "id" : "roleid2"                                                                                                                          |
   |                 |                 |                 |         }                                                                                                                                         |
   |                 |                 |                 |       ]                                                                                                                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | assumed_by      | Yes             | JSON object     | Detailed information about the delegated party. Example:                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "assumed_by": {                                                                                                                                |
   |                 |                 |                 |          "user": {                                                                                                                                |
   |                 |                 |                 |            "domain": {                                                                                                                            |
   |                 |                 |                 |              "name": "domain B",                                                                                                                  |
   |                 |                 |                 |              "id": "bfdd55e02a014894b5a2693f31..."                                                                                                |
   |                 |                 |                 |            },                                                                                                                                     |
   |                 |                 |                 |            "name": "user B",                                                                                                                      |
   |                 |                 |                 |            "id": "ff5ea657f1dd45c4b8f398cab..."                                                                                                   |
   |                 |                 |                 |          }                                                                                                                                        |
   |                 |                 |                 |        }                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **domain.name**: Name of the domain which the delegated party belongs to.                                                                      |
   |                 |                 |                 | -  **user.name**: Username of the delegated party.                                                                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      Token information stored in the response header:
      X-Subject-Token:MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...

      X-Frame-Options: SAMEORIGIN

      Information included in the response body:
      {
        "token": {
          "methods": [
            "assume_role"
          ],
          "issued_at": "2017-05-18T11:44:05.232000Z",
          "expires_at": "2017-05-19T11:44:05.232000Z",
          "user": {
            "id": "93e12ecdad6f4abd84968741da...",
            "name": "user A/agencytest",
            "password_expires_at":"2016-11-06T15:32:17.000000",
            "domain": {
              "id": "ce925c42c25943bebba10ea64a...",
              "name": "domain A"
            }
          },
          "domain": {
            "id": "ce925c42c25943bebba10ea64a...",
            "name": "domain A"
          },
          "roles": [
            {
              "id": "c11c61319f08404eaf94f8030b9...",
              "name": "role1"
            },
            {
              "id": "d52dde35ijg62fex2ijhdc785sc3...",
              "name": "role2"
            },
            {
              "id": "d862dwd32dwhu854rdcs447ed1d7..."
              "name": "op_gated_tasssg6"
            }
          ],
          "assumed_by": {
            "user": {
              "domain": {
                "name": "domain B",
                "id": "c1a78a82d81c4a19b03bfe82d3ad..."
              },
              "id": "cdeb158dda854cc3bab77d8926ff...",
              "name": "User B"
            }
          }
        }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
201         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
503         Service unavailable.
=========== =========================================
