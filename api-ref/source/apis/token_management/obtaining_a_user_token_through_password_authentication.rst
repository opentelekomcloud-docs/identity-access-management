:original_name: en-us_topic_0057845583.html

.. _en-us_topic_0057845583:

Obtaining a User Token Through Password Authentication
======================================================

Function
--------

This API is used to obtain a token through username/password authentication. A token is a system object encapsulating the identity and permissions of a user. When calling the APIs of IAM or other cloud services, you can use this API to obtain a token for authentication.

.. note::

   -  The validity period of a token is **24 hours**. Cache your token to prevent frequent API calling. Ensure that the token is valid while you use it. Using a token that will soon expire may cause API calling failures. Obtaining a new token does not affect the validity of the existing token.
   -  **The token or the tokens of the account will become invalid within 30 minutes** if any of the following occurs:

      -  An IAM user is deleted or disabled.
      -  An IAM user's password or access key is changed.
      -  An IAM user's permissions are changed (due to outstanding payments, OBT application approval, or permission modification). Your account is in arrears, you apply for or exit the OBT, or the permissions of any user group under your account are changed.

   -  If "The token must be updated" is returned when a token is used to call a cloud service API, the token has expired or is invalid. You need to obtain a new token.
   -  A token will fail to pass the signature verification if it has been tampered with.

URI
---

POST /v3/auth/tokens

.. table:: **Table 1** Query parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                               |
   +===========+===========+========+===========================================================================================================================================================================================================+
   | nocatalog | No        | String | If this parameter is set, no catalog information will be displayed in the response. Any non-empty string for this parameter will be interpreted as **true** and no catalog information will be displayed. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Parameters in the request body

   +-------------------------------------------------------+-----------+--------+-----------------------------+
   | Parameter                                             | Mandatory | Type   | Description                 |
   +=======================================================+===========+========+=============================+
   | :ref:`auth <en-us_topic_0057845583__li9161113917599>` | Yes       | Object | Authentication information. |
   +-------------------------------------------------------+-----------+--------+-----------------------------+

-  .. _en-us_topic_0057845583__li9161113917599:

   auth

   +----------------------------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                | Mandatory       | Type            | Description                                                                                                                                                     |
   +==========================================================+=================+=================+=================================================================================================================================================================+
   | :ref:`identity <en-us_topic_0057845583__li521911596593>` | Yes             | Object          | Authentication parameters.                                                                                                                                      |
   +----------------------------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`scope <en-us_topic_0057845583__li152529541647>`    | Yes             | Object          | Application scope of the token. Value options: **project** and **domain**.                                                                                      |
   |                                                          |                 |                 |                                                                                                                                                                 |
   |                                                          |                 |                 | .. note::                                                                                                                                                       |
   |                                                          |                 |                 |                                                                                                                                                                 |
   |                                                          |                 |                 |    -  If the scope is set to **domain**, the token applies to global services. If the scope is set to **project**, the token applies to project-level services. |
   |                                                          |                 |                 |    -  If you set the scope to both **project** and **domain**, the **project** is used and you get a token for project-level services.                          |
   |                                                          |                 |                 |    -  If you leave **scope** empty, the token applies to global services. You are advised to specify an appropriate scope as required.                          |
   +----------------------------------------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845583__li521911596593:

   auth.identity

   +-----------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                 | Mandatory       | Type             | Description                                                                                                               |
   +===========================================================+=================+==================+===========================================================================================================================+
   | methods                                                   | Yes             | Array of strings | Authentication method. Set this parameter to **"password"**.                                                              |
   +-----------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | :ref:`password <en-us_topic_0057845583__li2030154913010>` | Yes             | Object           | IAM user password authentication information.                                                                             |
   |                                                           |                 |                  |                                                                                                                           |
   |                                                           |                 |                  | .. note::                                                                                                                 |
   |                                                           |                 |                  |                                                                                                                           |
   |                                                           |                 |                  |    Authentication information. Example:                                                                                   |
   |                                                           |                 |                  |                                                                                                                           |
   |                                                           |                 |                  |    .. code-block::                                                                                                        |
   |                                                           |                 |                  |                                                                                                                           |
   |                                                           |                 |                  |       "password": {                                                                                                       |
   |                                                           |                 |                  |               "user": {                                                                                                   |
   |                                                           |                 |                  |                 "name": "user A",                                                                                         |
   |                                                           |                 |                  |                 "password": "**********",                                                                                 |
   |                                                           |                 |                  |                 "domain": {                                                                                               |
   |                                                           |                 |                  |                   "name": "domain A"                                                                                      |
   |                                                           |                 |                  |                                                                                                                           |
   |                                                           |                 |                  |    -  **user.name**: Name of the user that wants to obtain the token. Obtain the username on the **My Credentials** page. |
   |                                                           |                 |                  |    -  **password**: Login password of the user.                                                                           |
   |                                                           |                 |                  |    -  **domain.name**: Name of the domain that created the user. Obtain the domain name on the **My Credentials** page.   |
   +-----------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845583__li2030154913010:

   auth.identity.password

   +-----------------------------------------------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter                                           | Mandatory | Type   | Description                                                         |
   +=====================================================+===========+========+=====================================================================+
   | :ref:`user <en-us_topic_0057845583__li93251722349>` | Yes       | Object | Information about the IAM user who is requesting to obtain a token. |
   +-----------------------------------------------------+-----------+--------+---------------------------------------------------------------------+

-  .. _en-us_topic_0057845583__li93251722349:

   auth.identity.password.user

   +-------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                             | Mandatory       | Type            | Description                                                                                                                                                                                                             |
   +=======================================================+=================+=================+=========================================================================================================================================================================================================================+
   | :ref:`domain <en-us_topic_0057845583__li19469631442>` | Yes             | Object          | Information about the account used to create the IAM user.                                                                                                                                                              |
   +-------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                  | Yes             | String          | IAM username                                                                                                                                                                                                            |
   +-------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password                                              | Yes             | String          | Password of the IAM user.                                                                                                                                                                                               |
   |                                                       |                 |                 |                                                                                                                                                                                                                         |
   |                                                       |                 |                 | .. note::                                                                                                                                                                                                               |
   |                                                       |                 |                 |                                                                                                                                                                                                                         |
   |                                                       |                 |                 |    -  To obtain a token successfully, ensure that the password you provide is correct.                                                                                                                                  |
   |                                                       |                 |                 |    -  A third-party system user cannot directly obtain a token by using the username and password used for identity federation. Go to the cloud platform login page, click **Forgot Password**, and reset the password. |
   +-------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845583__li19469631442:

   auth.identity.password.user.domain

   +-----------+-----------+--------+--------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                      |
   +===========+===========+========+==================================================+
   | name      | Yes       | String | Name of the account used to create the IAM user. |
   +-----------+-----------+--------+--------------------------------------------------+

-  .. _en-us_topic_0057845583__li152529541647:

   auth.scope

   +----------------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                | Mandatory | Type   | Description                                                                                                                                                                                                                                |
   +==========================================================+===========+========+============================================================================================================================================================================================================================================+
   | :ref:`domain <en-us_topic_0057845583__li31351934511>`    | No        | Object | If this parameter is set to **domain**, the token can be used to access global services, such as OBS. Global services are not subject to any projects or regions. You can specify either **id** or **name**. **domain.id** is recommended. |
   +----------------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`project <en-us_topic_0057845583__li1026951216511>` | No        | Object | If this parameter is set to **project**, the token can be used to access only services (such as ECS) in specific projects. You can specify either **id** or **name**.                                                                      |
   +----------------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845583__li31351934511:

   auth.scope.domain

   +-----------+-----------+--------+--------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                      |
   +===========+===========+========+==================================================+
   | id        | No        | String | ID of the account used to create the IAM user.   |
   +-----------+-----------+--------+--------------------------------------------------+
   | name      | No        | String | Name of the account used to create the IAM user. |
   +-----------+-----------+--------+--------------------------------------------------+

-  .. _en-us_topic_0057845583__li1026951216511:

   auth.scope.project

   +-----------+-----------+--------+----------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                              |
   +===========+===========+========+==========================================================+
   | id        | No        | String | ID of the project to which the IAM user belongs.         |
   +-----------+-----------+--------+----------------------------------------------------------+
   | name      | No        | String | Project name of the account used to create the IAM user. |
   +-----------+-----------+--------+----------------------------------------------------------+

-  Example request

   The following is a sample request for obtaining a token for **user A**. The login password of the user is **\*********\*** and the domain name is **domain A**. The scope of the token is **domain**.

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

Response Parameters
-------------------

-  Parameters in the response header

   =============== ========= ====== ===============
   Parameter       Mandatory Type   Description
   =============== ========= ====== ===============
   X-Subject-Token Yes       String Obtained token.
   =============== ========= ====== ===============

   .. table:: **Table 2** Parameters in the response body

      +------------------------------------------------------------+--------+--------------------+
      | Parameter                                                  | Type   | Description        |
      +============================================================+========+====================+
      | :ref:`token <en-us_topic_0057845583__table14259024204717>` | Object | Token information. |
      +------------------------------------------------------------+--------+--------------------+

   .. _en-us_topic_0057845583__table14259024204717:

   .. table:: **Table 3** token

      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                                    | Type                  | Description                                                                                                                                                                      |
      +==============================================================+=======================+==================================================================================================================================================================================+
      | :ref:`catalog <en-us_topic_0057845583__table18263824174719>` | Array of objects      | Catalog information.                                                                                                                                                             |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | Example:                                                                                                                                                                         |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | .. code-block::                                                                                                                                                                  |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       |    "catalog": [{                                                                                                                                                                 |
      |                                                              |                       |        "type": "identity",                                                                                                                                                       |
      |                                                              |                       |        "id": "1331e5cff2a74d76b03da1225910e...",                                                                                                                                 |
      |                                                              |                       |        "name": "iam",                                                                                                                                                            |
      |                                                              |                       |        "endpoints": [{                                                                                                                                                           |
      |                                                              |                       |            "url": "https://sample.domain.com/v3",                                                                                                                                |
      |                                                              |                       |            "region": "*",                                                                                                                                                        |
      |                                                              |                       |            "region_id": "*",                                                                                                                                                     |
      |                                                              |                       |            "interface": "public",                                                                                                                                                |
      |                                                              |                       |            "id": "089d4a381d574308a703122d3ae73..."                                                                                                                              |
      |                                                              |                       |        }]                                                                                                                                                                        |
      |                                                              |                       |    }]                                                                                                                                                                            |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | :ref:`domain <en-us_topic_0057845583__table52641724184711>`  | Object                | Account information about the IAM user who requests for the token. This parameter is returned only when the **scope** parameter in the request body has been set to **domain**.  |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | Example:                                                                                                                                                                         |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | .. code-block::                                                                                                                                                                  |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       |    "domain": {                                                                                                                                                                   |
      |                                                              |                       |          "name" : "domain A"                                                                                                                                                     |
      |                                                              |                       |          "id" : "fdec73ffea524aa1b373e40..."                                                                                                                                     |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | expires_at                                                   | String                | Time when the token will expire.                                                                                                                                                 |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | mfa_authn_at                                                 | String                | MFA authentication time. This field is displayed only when virtual MFA-based login authentication is enabled.                                                                    |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | issued_at                                                    | String                | Time when the token was issued.                                                                                                                                                  |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | methods                                                      | Array of strings      | Method for obtaining the token.                                                                                                                                                  |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | :ref:`project <en-us_topic_0057845583__table4265182419474>`  | Object                | Project information about the IAM user who requests for the token. This parameter is returned only when the **scope** parameter in the request body has been set to **project**. |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | Example:                                                                                                                                                                         |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | .. code-block::                                                                                                                                                                  |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       |    "project": {                                                                                                                                                                  |
      |                                                              |                       |          "name": "project A",                                                                                                                                                    |
      |                                                              |                       |          "id": "34c77f3eaf84c00aaf54...",                                                                                                                                        |
      |                                                              |                       |          "domain": {                                                                                                                                                             |
      |                                                              |                       |             "name": "domain A",                                                                                                                                                  |
      |                                                              |                       |             "id": "fdec73ffea524aa1b373e40..."                                                                                                                                   |
      |                                                              |                       |           }                                                                                                                                                                      |
      |                                                              |                       |       }                                                                                                                                                                          |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | :ref:`roles <en-us_topic_0057845583__table1526632404711>`    | Array of objects      | Permissions information of the token.                                                                                                                                            |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | Example:                                                                                                                                                                         |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | .. code-block::                                                                                                                                                                  |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       |    "roles" : [{                                                                                                                                                                  |
      |                                                              |                       |         "name" : "role1",                                                                                                                                                        |
      |                                                              |                       |         "id" : "roleid1"                                                                                                                                                         |
      |                                                              |                       |         }, {                                                                                                                                                                     |
      |                                                              |                       |         "name" : "role2",                                                                                                                                                        |
      |                                                              |                       |         "id" : "roleid2"                                                                                                                                                         |
      |                                                              |                       |         }                                                                                                                                                                        |
      |                                                              |                       |       ]                                                                                                                                                                          |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | :ref:`user <en-us_topic_0057845583__table926722417478>`      | Object                | Information about the IAM user who requests for the token.                                                                                                                       |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | Example:                                                                                                                                                                         |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       | .. code-block::                                                                                                                                                                  |
      |                                                              |                       |                                                                                                                                                                                  |
      |                                                              |                       |    "user": {                                                                                                                                                                     |
      |                                                              |                       |          "name": "user A",                                                                                                                                                       |
      |                                                              |                       |          "id": "b95b78b67fa045b38104...",                                                                                                                                        |
      |                                                              |                       |          "password_expires_at":"2016-11-06T15:32:17.000000",                                                                                                                     |
      |                                                              |                       |          "domain": {                                                                                                                                                             |
      |                                                              |                       |             "name": "domain A",                                                                                                                                                  |
      |                                                              |                       |             "id": "fdec73ffea524aa1b373e40..."                                                                                                                                   |
      |                                                              |                       |           }                                                                                                                                                                      |
      |                                                              |                       |        }                                                                                                                                                                         |
      +--------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0057845583__table18263824174719:

   .. table:: **Table 4** token.catalog

      +----------------------------------------------------------------+------------------+-----------------------------------------------+
      | Parameter                                                      | Type             | Description                                   |
      +================================================================+==================+===============================================+
      | :ref:`endpoints <en-us_topic_0057845583__table13263152454713>` | Array of objects | Endpoint information.                         |
      +----------------------------------------------------------------+------------------+-----------------------------------------------+
      | id                                                             | String           | Service ID.                                   |
      +----------------------------------------------------------------+------------------+-----------------------------------------------+
      | name                                                           | String           | Service name.                                 |
      +----------------------------------------------------------------+------------------+-----------------------------------------------+
      | type                                                           | String           | Type of the service to which the API belongs. |
      +----------------------------------------------------------------+------------------+-----------------------------------------------+

   .. _en-us_topic_0057845583__table13263152454713:

   .. table:: **Table 5** token.catalog.endpoints

      +-----------+--------+------------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                              |
      +===========+========+==========================================================================================+
      | id        | String | Endpoint ID.                                                                             |
      +-----------+--------+------------------------------------------------------------------------------------------+
      | interface | String | Visibility of the API. **public** indicates that the API is available for public access. |
      +-----------+--------+------------------------------------------------------------------------------------------+
      | region    | String | Region to which the endpoint belongs.                                                    |
      +-----------+--------+------------------------------------------------------------------------------------------+
      | region_id | String | Region ID.                                                                               |
      +-----------+--------+------------------------------------------------------------------------------------------+
      | url       | String | Endpoint URL.                                                                            |
      +-----------+--------+------------------------------------------------------------------------------------------+

   .. _en-us_topic_0057845583__table52641724184711:

   .. table:: **Table 6** token.domain

      ========= ====== ============
      Parameter Type   Description
      ========= ====== ============
      name      String Domain name.
      id        String Domain ID.
      ========= ====== ============

   .. _en-us_topic_0057845583__table4265182419474:

   .. table:: **Table 7** token.project

      ========= ====== ==================================
      Parameter Type   Description
      ========= ====== ==================================
      domain    Object Domain information of the project.
      id        String Project ID.
      name      String Project name.
      ========= ====== ==================================

   .. table:: **Table 8** token.project.domain

      ========= ====== ============
      Parameter Type   Description
      ========= ====== ============
      id        String Domain ID.
      name      String Domain name.
      ========= ====== ============

   .. _en-us_topic_0057845583__table1526632404711:

   .. table:: **Table 9** token.roles

      +-----------+--------+-----------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                             |
      +===========+========+=========================================================================================+
      | name      | String | Permission name.                                                                        |
      +-----------+--------+-----------------------------------------------------------------------------------------+
      | id        | String | Permission ID. The default value is **0**, which does not correspond to any permission. |
      +-----------+--------+-----------------------------------------------------------------------------------------+

   .. _en-us_topic_0057845583__table926722417478:

   .. table:: **Table 10** token.user

      +--------------------------------------------------------------+--------+-------------------------------------------------------------------------------------------------+
      | Parameter                                                    | Type   | Description                                                                                     |
      +==============================================================+========+=================================================================================================+
      | name                                                         | String | IAM username.                                                                                   |
      +--------------------------------------------------------------+--------+-------------------------------------------------------------------------------------------------+
      | id                                                           | String | IAM user ID.                                                                                    |
      +--------------------------------------------------------------+--------+-------------------------------------------------------------------------------------------------+
      | password_expires_at                                          | String | Password expiration time. If this parameter is set to **null**, the password will never expire. |
      +--------------------------------------------------------------+--------+-------------------------------------------------------------------------------------------------+
      | :ref:`domain <en-us_topic_0057845583__table202681724204710>` | Object | Information about the account used to create the IAM user.                                      |
      +--------------------------------------------------------------+--------+-------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0057845583__table202681724204710:

   .. table:: **Table 11** token.user.domain

      ========= ====== ================================================
      Parameter Type   Description
      ========= ====== ================================================
      name      String Name of the account used to create the IAM user.
      id        String ID of the account used to create the IAM user.
      ========= ====== ================================================

-  Example response

   The following is a sample request for obtaining a token for **user A**. The login password of the user is **\*********\*** and the domain name is **domain A**. The scope of the token is **domain**.

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
