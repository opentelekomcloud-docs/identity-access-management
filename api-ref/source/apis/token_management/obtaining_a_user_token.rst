:original_name: en-us_topic_0057845583.html

.. _en-us_topic_0057845583:

Obtaining a User Token
======================

Function
--------

This API is used to obtain a token through username/password authentication. A token is a system object encapsulating the identity and permissions of a user. When calling the APIs of IAM or other cloud services, you can use this API to obtain a token for authentication.

.. note::

   The validity period of a token is **24 hours**. Cache the token to prevent frequent API calling. Ensure that the token is valid while you use it. Using a token that will soon expire may cause API calling failures. Obtaining a new token does not affect the validity of the existing token. The following operations will invalidate the existing token. After these operations are performed, obtain a new token.

   -  Changing the password or access key of your account or an IAM user: The token of your account or the user is invalidated.
   -  Deleting or disabling an IAM user: The token of the user is invalidated.
   -  Changing the permissions of an IAM user: The token of the user is invalidated. For example, when the user is added to or removed from a user group, or when permissions of the group to which the user belongs are modified.

URI
---

POST /v3/auth/tokens

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Parameters in the request body

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================+
   | identity        | Yes             | JSON object     | Authentication parameters, including: **methods** and **password**.                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | .. code-block::                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |    "identity": {                                                                                                                                                                                                       |
   |                 |                 |                 |          "methods": ["password"],                                                                                                                                                                                      |
   |                 |                 |                 |          "password": {                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | methods         | Yes             | String Array    | Authentication method. The value of this field is **password**. If virtual MFA-based login authentication is enabled, the value of this field is **["password","totp"]**.                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password        | Yes             | JSON object     | Authentication information. Example:                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | .. code-block::                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |    "password": {                                                                                                                                                                                                       |
   |                 |                 |                 |            "user": {                                                                                                                                                                                                   |
   |                 |                 |                 |              "name": "user A",                                                                                                                                                                                         |
   |                 |                 |                 |              "password": "**********",                                                                                                                                                                                 |
   |                 |                 |                 |              "domain": {                                                                                                                                                                                               |
   |                 |                 |                 |                "name": "domain A"                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  **user.name**: Name of the user that wants to obtain the token. Obtain the username on the **My Credentials** page.                                                                                                 |
   |                 |                 |                 | -  **password**: Login password of the user.                                                                                                                                                                           |
   |                 |                 |                 | -  **domain.name**: Name of the domain that created the user. Obtain the domain name on the **My Credentials** page.                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | totp            | No              | JSON object     | Authentication information. This parameter is mandatory only when virtual MFA-based login authentication is enabled.                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | Example:                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | .. code-block::                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |    "totp": {                                                                                                                                                                                                           |
   |                 |                 |                 |            "user": {                                                                                                                                                                                                   |
   |                 |                 |                 |              "id": "b95b78b67fa045b38104c12fb...",                                                                                                                                                                     |
   |                 |                 |                 |              "passcode": "******"                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  **user.id**: User ID, which can be obtained on the **My Credentials** page.                                                                                                                                         |
   |                 |                 |                 | -  **passcode**: Virtual MFA device verification code, which can be obtained on the MFA app.                                                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scope           | No              | JSON object     | Usage scope of the token. The value can be **project** or **domain**.                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  Example 1: If this field is set to **project**, the token can be used to access only services in specific projects, such as ECS. You can specify either **id** or **name**.                                         |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |    .. code-block::                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |       "scope": {                                                                                                                                                                                                       |
   |                 |                 |                 |             "project": {                                                                                                                                                                                               |
   |                 |                 |                 |             "id": "0b95b78b67fa045b38104c12fb..."                                                                                                                                                                      |
   |                 |                 |                 |             }                                                                                                                                                                                                          |
   |                 |                 |                 |           }                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 | -  Example 2: If this field is set to **domain**, the token can be used to access global services, such as OBS. Global services are not subject to any projects or regions. You can specify either **id** or **name**. |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |    .. code-block::                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                        |
   |                 |                 |                 |       "scope": {                                                                                                                                                                                                       |
   |                 |                 |                 |             "domain": {                                                                                                                                                                                                |
   |                 |                 |                 |             "name": " domain A"                                                                                                                                                                                        |
   |                 |                 |                 |             }                                                                                                                                                                                                          |
   |                 |                 |                 |           }                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   The following is a sample request for obtaining a token for **user A**. The login password of the user is **``**********``** and the domain name is **domain A**. The scope of the token is **domain**.

   .. code-block::

      {
        "auth": {
          "identity": {
            "methods": ["password"],
            "password": {
              "user": {
                "name": "user A",
                "password": "**********",
                "domain": {
                  "name": "domain A"
                }
              }
            }
          },
          "scope": {
            "domain": {
              "name": "domain A"
            }
          }
        }
      }

   The following is a sample request for obtaining a token when virtual MFA-based login authentication is enabled.

   .. code-block::

      {
          "auth": {
              "identity": {
                  "methods": ["password", "totp"],
                  "password": {
                      "user": {
                          "name": "user A",
                          "password": "********",
                          "domain": {
                              "name": "domain A"
                          }
                      }
                  },
                  "totp" : {
                      "user": {
                          "id": "dfsafdfsaf....",
                          "passcode": "******"
                      }
                  }
              },
              "scope": {
                  "domain": {
                      "name": "domain A"
                  }
              }
          }
      }

Response Parameters
-------------------

-  Parameters in the response header

   =============== ========= ====== ===============
   Parameter       Mandatory Type   Description
   =============== ========= ====== ===============
   X-Subject-Token Yes       String Obtained token.
   =============== ========= ====== ===============

-  Token format description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | methods         | Yes             | Json Array      | Method for obtaining a token.                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | expires_at      | Yes             | String          | Expiration date of the token.                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | issued_at       | Yes             | String          | Time when the token was issued.                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | mfa_authn_at    | No              | String          | MFA authentication time. This field is displayed only when virtual MFA-based login authentication is enabled.                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | user            | Yes             | JSON object     | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "user": {                                                                                                                                      |
   |                 |                 |                 |          "name": "user A",                                                                                                                        |
   |                 |                 |                 |          "id": "b95b78b67fa045b38104...",                                                                                                         |
   |                 |                 |                 |          "password_expires_at":"2016-11-06T15:32:17.000000",                                                                                      |
   |                 |                 |                 |          "domain": {                                                                                                                              |
   |                 |                 |                 |             "name": "domain A",                                                                                                                   |
   |                 |                 |                 |             "id": "fdec73ffea524aa1b373e40..."                                                                                                    |
   |                 |                 |                 |           }                                                                                                                                       |
   |                 |                 |                 |        }                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **user.name**: Name of the user that wants to obtain the token.                                                                                |
   |                 |                 |                 | -  **user.id**: ID of the user.                                                                                                                   |
   |                 |                 |                 | -  **domain.name**: Name of the domain that created the user.                                                                                     |
   |                 |                 |                 | -  **domain.id**: ID of the domain.                                                                                                               |
   |                 |                 |                 | -  **password_expires_at**: Coordinated Universal Time (UTC) that the password will expire. **null** indicates that the password will not expire. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain          | No              | JSON object     | This parameter is returned only when the **scope** parameter in the request body has been set to **domain**.                                      |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "domain": {                                                                                                                                    |
   |                 |                 |                 |          "name" : "domain A"                                                                                                                      |
   |                 |                 |                 |          "id" : "fdec73ffea524aa1b373e40..."                                                                                                      |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **domain.name**: Name of the domain that created the user.                                                                                     |
   |                 |                 |                 | -  **domain.id**: ID of the domain.                                                                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | project         | No              | JSON object     | This parameter is returned only when the **scope** parameter in the request body has been set to **project**.                                     |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "project": {                                                                                                                                   |
   |                 |                 |                 |          "name": "project A",                                                                                                                     |
   |                 |                 |                 |          "id": "34c77f3eaf84c00aaf54...",                                                                                                         |
   |                 |                 |                 |          "domain": {                                                                                                                              |
   |                 |                 |                 |             "name": "domain A",                                                                                                                   |
   |                 |                 |                 |             "id": "fdec73ffea524aa1b373e40..."                                                                                                    |
   |                 |                 |                 |           }                                                                                                                                       |
   |                 |                 |                 |       }                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **project.name**: Name of a project.                                                                                                           |
   |                 |                 |                 | -  **project.id**: ID of the project.                                                                                                             |
   |                 |                 |                 | -  **domain.name**: Domain name of the project.                                                                                                   |
   |                 |                 |                 | -  **domain.id**: Domain ID of the project.                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | catalog         | Yes             | Json Array      | Endpoint information.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "catalog": [{                                                                                                                                  |
   |                 |                 |                 |        "type": "identity",                                                                                                                        |
   |                 |                 |                 |        "id": "1331e5cff2a74d76b03da1225910e...",                                                                                                  |
   |                 |                 |                 |        "name": "iam",                                                                                                                             |
   |                 |                 |                 |        "endpoints": [{                                                                                                                            |
   |                 |                 |                 |            "url": "https://sample.domain.com/v3",                                                                                                 |
   |                 |                 |                 |            "region": "*",                                                                                                                         |
   |                 |                 |                 |            "region_id": "*",                                                                                                                      |
   |                 |                 |                 |            "interface": "public",                                                                                                                 |
   |                 |                 |                 |            "id": "089d4a381d574308a703122d3ae73..."                                                                                               |
   |                 |                 |                 |        }]                                                                                                                                         |
   |                 |                 |                 |    }]                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **type**: Type of the service to which the API belongs.                                                                                        |
   |                 |                 |                 | -  **id**: ID of the service.                                                                                                                     |
   |                 |                 |                 | -  **name**: Name of the service.                                                                                                                 |
   |                 |                 |                 | -  **endpoints**: Endpoints that can be used to call the API.                                                                                     |
   |                 |                 |                 | -  **url**: URL used to call the API.                                                                                                             |
   |                 |                 |                 | -  **region**: Region in which the service can be accessed.                                                                                       |
   |                 |                 |                 | -  **region_id**: ID of the region.                                                                                                               |
   |                 |                 |                 | -  **interface**: Type of the API. The value **public** means that the API is open for access.                                                    |
   |                 |                 |                 | -  **id**: ID of the API.                                                                                                                         |
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

-  Example response

   The following is a sample request for obtaining a token for **user A**. The login password of the user is **``**********``** and the domain name is **domain A**. The scope of the token is **domain**.

   .. code-block::

      Token information stored in the response header:
      X-Subject-Token:MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...

      Token information stored in the response body:
      {
        "token" : {
          "methods" : ["password"],
          "expires_at" : "2015-11-09T01:42:57.527363Z",
          "issued_at" : "2015-11-09T00:42:57.527404Z",
          "user" : {
            "domain" : {
            "id" : "ded485def148s4e7d2se41d5se...",
            "name" : "domain A"
            },
            "id" : "ee4dfb6e5540447cb37419051...",
            "name" : "user A",
            "password_expires_at":"2016-11-06T15:32:17.000000",
          },
          "domain" : {
             "name" : "domain A",
             "id" : "dod4ed5e8d4e8d2e8e8d5d2d..."
          },
          "catalog": [{
              "type": "identity",
              "id": "1331e5cff2a74d76b03da12259...",
              "name": "iam",
              "endpoints": [{
                  "url": "https://sample.domain.com/v3",
                  "region": "*",
                  "region_id": "*",
                 "interface": "public",
                   "id": "089d4a381d574308a703122d3a..."
             }]
          }],
          "roles" : [{
             "name" : "role1",
             "id" : "roleid1"
             }, {
             "name" : "role2",
             "id" : "roleid2"
             }
        ]
        }
      }

   The following is a sample request for obtaining a token when virtual MFA-based login authentication is enabled.

   .. code-block::

      Token information stored in the response header:
      X-Subject-Token:MIIDkgYJKoZIhvcNAQcCoIIDgzCCA38CAQExDTALBglghkgBZQMEAgEwgXXXXX...

      Token information stored in the response body:
      {
        "token": {
          "expires_at": "2020-09-05T06:50:44.390000Z",
          "mfa_authn_at": "2020-09-04T06:50:44.390000Z",
          "issued_at": "2020-09-04T06:50:44.390000Z",
           "methods": [
            "password",
            "totp"
          ],
          "catalog": [
            {
              "endpoints": [
                {
                  "id": "33e1cbdd86d34e89a63cf8ad16a5f...",
                  "interface": "public",
                  "region": "*",
                  "region_id": "*",
                  "url": "https://sample.domain.com/v3.0"
                }
              ],
              "id": "100a6a3477f1495286579b819d399...",
              "name": "iam",
              "type": "iam"
            },
            ],
          "domain": {
            "id": "e6505630658e49649784759cdf251...",
            "name": "domain A"
          },
          "roles": [
           {
           "name" : "role1",
           "id" : "roleid1"
            },{
           "name" : "role1",
           "id" : "roleid1"

      }
          ],
             "user": {
            "domain": {
              "id": "e6505630658e49649784759cdf251...",
              "name": "domain A"
            },
            "id": "092ac6365a0025b11f76c01e90100...",
            "name": "user A",
            "password_expires_at": ""
          }
        }
      }

Status Codes
------------

=========== ===================================================
Status Code Description
=========== ===================================================
201         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error. The format may be incorrect.
503         Service unavailable.
=========== ===================================================
