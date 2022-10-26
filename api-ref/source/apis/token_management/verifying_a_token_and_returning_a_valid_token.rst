:original_name: en-us_topic_0057845585.html

.. _en-us_topic_0057845585:

Verifying a Token and Returning a Valid Token
=============================================

Function
--------

This API is used to check the validity of a specified token. If the token is valid, detailed information about the token will be returned.

URI
---

GET /v3/auth/tokens

Request Parameters
------------------

-  Parameters in the request header

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | -  To verify your own token, specify your token. There are no special requirements on the permissions that your token must have.         |
   |                 |                 |                 | -  To verify the token of another user under the same domain, use a token that has permissions of the **Security Administrator** policy. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Subject-Token | Yes             | String          | Token to be verified.                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

-  Query parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                         |
   +===========+===========+========+=====================================================================================+
   | nocatalog | No        | String | If this parameter is set, no catalog information will be displayed in the response. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H "X-Subject-Token:$token" -X GET https://sample.domain.com/v3/auth/tokens

Response Parameters
-------------------

-  Parameters in the response header

   =============== ========= ====== ===============
   Parameter       Mandatory Type   Description
   =============== ========= ====== ===============
   X-Subject-Token Yes       String Verified token.
   =============== ========= ====== ===============

-  Parameters in the response body

   ========= ========= ====== =======================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================
   token     Yes       Object Token information list.
   ========= ========= ====== =======================

-  Token format description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | methods         | Yes             | Array           | Method of obtaining the token, for example, **password**.                                                                                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | expires_at      | Yes             | String          | Expiration date of the token.                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | issued_at       | Yes             | String          | Time when the token was issued.                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | user            | Yes             | Object          | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "user": {                                                                                                                                      |
   |                 |                 |                 |          "name": "username",                                                                                                                      |
   |                 |                 |                 |          "id": "userid",                                                                                                                          |
   |                 |                 |                 |          "password_expires_at":"2016-11-06T15:32:17.000000",                                                                                      |
   |                 |                 |                 |          "domain": {                                                                                                                              |
   |                 |                 |                 |             "name": "domainname",                                                                                                                 |
   |                 |                 |                 |             "id": "domainid"                                                                                                                      |
   |                 |                 |                 |           }                                                                                                                                       |
   |                 |                 |                 |        }                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **user.name**: Name of the user that owns the token.                                                                                           |
   |                 |                 |                 | -  **user.id**: ID of the user.                                                                                                                   |
   |                 |                 |                 | -  **domain.name**: Name of the domain to which the user belongs.                                                                                 |
   |                 |                 |                 | -  **domain.id**: ID of the domain.                                                                                                               |
   |                 |                 |                 | -  **password_expires_at**: Time when the password will expire. **null** indicates that the password will not expire. This parameter is optional. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain          | No              | Object          | The system determines whether to return this field based on the scope contained in the request for obtaining the token.                           |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "domain": {                                                                                                                                    |
   |                 |                 |                 |          "name" : "domainame",                                                                                                                    |
   |                 |                 |                 |          "id" : "domainid"                                                                                                                        |
   |                 |                 |                 |    }                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **domain.name**: Domain name.                                                                                                                  |
   |                 |                 |                 | -  **domain.id**: Domain ID.                                                                                                                      |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | project         | No              | Object          | The system determines whether to return this field based on the scope contained in the request for obtaining the token.                           |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Example:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | .. code-block::                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 |    "project": {                                                                                                                                   |
   |                 |                 |                 |          "name": "projectname",                                                                                                                   |
   |                 |                 |                 |          "id": "projectid",                                                                                                                       |
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
   | roles           | Yes             | Array           | Permissions information of the token.                                                                                                             |
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

   .. code-block::

      {
        "token" : {
          "methods" : ["password"],
          "expires_at" : "2015-11-09T01:42:57.527363Z",
          "issued_at" : "2015-11-09T00:42:57.527404Z",
          "user" : {
            "domain" : {
            "id" : "default",
            "name" : "Default"
            },
            "id" : "ee4dfb6e5540447cb3741905149XXX...",
            "password_expires_at":"2016-11-06T15:32:17.000000",
            "name" : "admin"
          },
          "domain" : {
             "name" : "Default",
             "id" : "default"
          },
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

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
503         Service unavailable.
=========== =========================================
