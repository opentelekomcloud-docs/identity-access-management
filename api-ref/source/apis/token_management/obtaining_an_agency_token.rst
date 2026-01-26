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

   +-------------------------------------------------------+-----------+--------+-----------------------------+
   | Parameter                                             | Mandatory | Type   | Description                 |
   +=======================================================+===========+========+=============================+
   | :ref:`auth <en-us_topic_0064274720__li1562212117563>` | Yes       | Object | Authentication information. |
   +-------------------------------------------------------+-----------+--------+-----------------------------+

-  .. _en-us_topic_0064274720__li1562212117563:

   auth

   +---------------------------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                               | Mandatory       | Type            | Description                                                                                                                      |
   +=========================================================+=================+=================+==================================================================================================================================+
   | :ref:`identity <en-us_topic_0064274720__li74381167583>` | Yes             | Object          | Authentication parameters, including: **methods** and **assume_role**.                                                           |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 | .. code-block::                                                                                                                  |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 |    "identity": {                                                                                                                 |
   |                                                         |                 |                 |          "methods": ["assume_role"],                                                                                             |
   |                                                         |                 |                 |          "assume_role": {                                                                                                        |
   +---------------------------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`scope <en-us_topic_0064274720__li1834119420019>`  | Yes             | Object          | Application scope of the token. The value can be **project** or **domain**.                                                      |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 | -  If this field is set to **project**, the token can only be used to access resources in the project of a specified ID or name. |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 |    .. code-block::                                                                                                               |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 |       "scope": {                                                                                                                 |
   |                                                         |                 |                 |             "project": {                                                                                                         |
   |                                                         |                 |                 |             "id": "0b95b78b67fa045b38104c12fb..."                                                                                |
   |                                                         |                 |                 |             }                                                                                                                    |
   |                                                         |                 |                 |           }                                                                                                                      |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 | -  If this field is set to **domain**, the token can be used to access all resources under the domain of a specified ID or name. |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 |    .. code-block::                                                                                                               |
   |                                                         |                 |                 |                                                                                                                                  |
   |                                                         |                 |                 |       "scope": {                                                                                                                 |
   |                                                         |                 |                 |             "domain": {                                                                                                          |
   |                                                         |                 |                 |             "id": "6b8eb224c76842e3ac2..."                                                                                       |
   |                                                         |                 |                 |             }                                                                                                                    |
   |                                                         |                 |                 |           }                                                                                                                      |
   +---------------------------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0064274720__li74381167583:

   auth.identity

   +------------------------------------------------------------+-----------+------------------+--------------------------------------------------------------------+
   | Parameter                                                  | Mandatory | Type             | Description                                                        |
   +============================================================+===========+==================+====================================================================+
   | methods                                                    | Yes       | Array of strings | Method for obtaining the token. Set this field to **assume_role**. |
   +------------------------------------------------------------+-----------+------------------+--------------------------------------------------------------------+
   | :ref:`assume_role <en-us_topic_0064274720__li45262021599>` | Yes       | Object           | Details about the agency and delegating party.                     |
   +------------------------------------------------------------+-----------+------------------+--------------------------------------------------------------------+

-  .. _en-us_topic_0064274720__li45262021599:

   auth.identity.assume_role

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                       |
   +=============+===========+========+===================================================================================================+
   | domain_id   | No        | String | Domain ID of the delegating party A. Either **domain_id** or **domain_name** must be specified.   |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | domain_name | No        | String | Domain name of the delegating party A. Either **domain_id** or **domain_name** must be specified. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | agency_name | Yes       | String | Name of the agency created by the delegating party A.                                             |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0064274720__li1834119420019:

   auth.scope

   +----------------------------------------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                | Mandatory | Type   | Description                                                                                                                       |
   +==========================================================+===========+========+===================================================================================================================================+
   | :ref:`domain <en-us_topic_0064274720__li13594535911>`    | No        | Object | If this parameter is set to **project**, the token can only be used to access resources in the project of a specified ID or name. |
   +----------------------------------------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`project <en-us_topic_0064274720__li1055112561412>` | No        | Object | If this parameter is set to **domain**, the token can be used to access all resources under the domain of a specified ID or name. |
   +----------------------------------------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0064274720__li13594535911:

   auth.scope.domain

   +-----------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                         |
   +===========+===========+========+=====================================================================================+
   | id        | No        | String | Domain ID of the delegating party A. Either **id** or **name** must be specified.   |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------+
   | name      | No        | String | Domain name of the delegating party A. Either **id** or **name** must be specified. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------+

-  .. _en-us_topic_0064274720__li1055112561412:

   auth.scope.project

   +-----------+-----------+--------+--------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                          |
   +===========+===========+========+======================================================================================+
   | id        | No        | String | Project ID of the delegating party A. Either **id** or **name** must be specified.   |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------+
   | name      | No        | String | Project name of the delegating party A. Either **id** or **name** must be specified. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------+

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

-  Parameters in the response body

   +------------------------------------------------------+--------+-------------------------+
   | Parameter                                            | Type   | Description             |
   +======================================================+========+=========================+
   | :ref:`token <en-us_topic_0064274720__li13315129356>` | Object | Token information list. |
   +------------------------------------------------------+--------+-------------------------+

-  .. _en-us_topic_0064274720__li13315129356:

   token

   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                     | Type                  | Description                                                                                                                          |
   +===============================================================+=======================+======================================================================================================================================+
   | methods                                                       | Array of strings      | Method for obtaining the token.                                                                                                      |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | expires_at                                                    | String                | Time when the token will expire.                                                                                                     |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | issued_at                                                     | String                | Time when the token was issued.                                                                                                      |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`assumed_by <en-us_topic_0064274720__table168378447517>` | Object                | Detailed information about the delegated party.                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | Example:                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | .. code-block::                                                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       |    "assumed_by": {                                                                                                                   |
   |                                                               |                       |          "user": {                                                                                                                   |
   |                                                               |                       |            "domain": {                                                                                                               |
   |                                                               |                       |              "name": "domain B",                                                                                                     |
   |                                                               |                       |              "id": "bfdd55e02a014894b5a2693f31..."                                                                                   |
   |                                                               |                       |            },                                                                                                                        |
   |                                                               |                       |            "name": "user B",                                                                                                         |
   |                                                               |                       |            "id": "ff5ea657f1dd45c4b8f398cab..."                                                                                      |
   |                                                               |                       |          }                                                                                                                           |
   |                                                               |                       |        }                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | -  **domain.name**: Name of the domain to which the delegated party belongs.                                                         |
   |                                                               |                       | -  **user.name**: Username of the delegated party.                                                                                   |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`catalog <en-us_topic_0064274720__table8840164418519>`   | Array of objects      | Endpoint information.                                                                                                                |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | Example:                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | .. code-block::                                                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       |    "catalog": [{                                                                                                                     |
   |                                                               |                       |        "type": "identity",                                                                                                           |
   |                                                               |                       |        "id": "1331e5cff2a74d76b03da1225910e31d",                                                                                     |
   |                                                               |                       |        "name": "iam",                                                                                                                |
   |                                                               |                       |        "endpoints": [{                                                                                                               |
   |                                                               |                       |            "url": "https://sample.domain.com/v3",                                                                                    |
   |                                                               |                       |            "region": "*",                                                                                                            |
   |                                                               |                       |            "region_id": "*",                                                                                                         |
   |                                                               |                       |            "interface": "public",                                                                                                    |
   |                                                               |                       |            "id": "089d4a381d574308a703122d3ae738e9"                                                                                  |
   |                                                               |                       |        }]                                                                                                                            |
   |                                                               |                       |    }]                                                                                                                                |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`domain <en-us_topic_0064274720__table884219440518>`     | Object                | This parameter is returned only when the **scope** parameter in the request body has been set to **domain**.                         |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | Example:                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | .. code-block::                                                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       |    "domain": {                                                                                                                       |
   |                                                               |                       |          "name" : "domain A",                                                                                                        |
   |                                                               |                       |          "id" : "domainid"                                                                                                           |
   |                                                               |                       |    }                                                                                                                                 |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | -  **domain.name**: Name of the domain to which the delegating party belongs.                                                        |
   |                                                               |                       | -  **domain.id**: ID of the domain to which the delegating party belongs.                                                            |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`project <en-us_topic_0064274720__table08421144254>`     | Object                | This parameter is returned only when the **scope** parameter in the request body has been set to **project**.                        |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | Example:                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | .. code-block::                                                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       |    "project": {                                                                                                                      |
   |                                                               |                       |          "name": "projectname",                                                                                                      |
   |                                                               |                       |          "id": "projectid"                                                                                                           |
   |                                                               |                       |    }                                                                                                                                 |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | -  **project.name**: project name.                                                                                                   |
   |                                                               |                       | -  **project.id**: project ID.                                                                                                       |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`roles <en-us_topic_0064274720__table16843544651>`       | Array of objects      | Permissions information of the token.                                                                                                |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | Example:                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | .. code-block::                                                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       |    "roles" : [{                                                                                                                      |
   |                                                               |                       |         "name" : "role1",                                                                                                            |
   |                                                               |                       |         "id" : "roleid1"                                                                                                             |
   |                                                               |                       |         }, {                                                                                                                         |
   |                                                               |                       |         "name" : "role2",                                                                                                            |
   |                                                               |                       |         "id" : "roleid2"                                                                                                             |
   |                                                               |                       |         }                                                                                                                            |
   |                                                               |                       |       ]                                                                                                                              |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`user <en-us_topic_0064274720__table1484415441657>`      | Object                | Detailed information about the delegating party.                                                                                     |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | .. code-block::                                                                                                                      |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       |    "user": {                                                                                                                         |
   |                                                               |                       |          "name": "user A",                                                                                                           |
   |                                                               |                       |          "id": "userid",                                                                                                             |
   |                                                               |                       |          "password_expires_at":"2016-11-06T15:32:17.000000",                                                                         |
   |                                                               |                       |          "domain": {                                                                                                                 |
   |                                                               |                       |             "name": "domain A",                                                                                                      |
   |                                                               |                       |             "id": "domainid"                                                                                                         |
   |                                                               |                       |           }                                                                                                                          |
   |                                                               |                       |        }                                                                                                                             |
   |                                                               |                       |                                                                                                                                      |
   |                                                               |                       | -  **user.name**: Username of the delegating party.                                                                                  |
   |                                                               |                       | -  **user.id**: User ID of the delegating party.                                                                                     |
   |                                                               |                       | -  **domain.name**: Name of the domain to which the delegating party belongs.                                                        |
   |                                                               |                       | -  **domain.id**: ID of the domain to which the delegating party belongs.                                                            |
   |                                                               |                       | -  (Optional) **password_expires_at**: UTC time when the password will expire. **null** indicates that the password will not expire. |
   +---------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0064274720__table168378447517:

   .. table:: **Table 1** token.assumed_by

      +----------------------------------------------------------+--------+-----------------------------------------------------+
      | Parameter                                                | Type   | Description                                         |
      +==========================================================+========+=====================================================+
      | :ref:`user <en-us_topic_0064274720__table1083884415518>` | Object | Information about an IAM user of delegated party B. |
      +----------------------------------------------------------+--------+-----------------------------------------------------+

   .. _en-us_topic_0064274720__table1083884415518:

   .. table:: **Table 2** token.assumed_by.user

      +------------------------------------------------------------+--------+------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                                  | Type   | Description                                                                                                            |
      +============================================================+========+========================================================================================================================+
      | name                                                       | String | IAM username.                                                                                                          |
      +------------------------------------------------------------+--------+------------------------------------------------------------------------------------------------------------------------+
      | id                                                         | String | IAM user ID.                                                                                                           |
      +------------------------------------------------------------+--------+------------------------------------------------------------------------------------------------------------------------+
      | :ref:`domain <en-us_topic_0064274720__table1983984416516>` | Object | Domain information about delegated party B.                                                                            |
      +------------------------------------------------------------+--------+------------------------------------------------------------------------------------------------------------------------+
      | password_expires_at                                        | String | UTC time when the password of the IAM user will expire. If this parameter is **null**, the password will never expire. |
      +------------------------------------------------------------+--------+------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0064274720__table1983984416516:

   .. table:: **Table 3** token.assumed_by.user.domain

      ========= ====== =================================
      Parameter Type   Description
      ========= ====== =================================
      name      String Domain name of delegated party B.
      id        String Domain ID of delegated party B.
      ========= ====== =================================

   .. _en-us_topic_0064274720__table8840164418519:

   .. table:: **Table 4** token.catalog

      +--------------------------------------------------------------+------------------+-----------------------------------------------+
      | Parameter                                                    | Type             | Description                                   |
      +==============================================================+==================+===============================================+
      | :ref:`endpoints <en-us_topic_0064274720__table168411441052>` | Array of objects | Endpoint information.                         |
      +--------------------------------------------------------------+------------------+-----------------------------------------------+
      | id                                                           | String           | Service ID.                                   |
      +--------------------------------------------------------------+------------------+-----------------------------------------------+
      | name                                                         | String           | Service name.                                 |
      +--------------------------------------------------------------+------------------+-----------------------------------------------+
      | type                                                         | String           | Type of the service to which the API belongs. |
      +--------------------------------------------------------------+------------------+-----------------------------------------------+

   .. _en-us_topic_0064274720__table168411441052:

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

   .. _en-us_topic_0064274720__table884219440518:

   .. table:: **Table 6** token.domain

      ========= ====== ======================================
      Parameter Type   Description
      ========= ====== ======================================
      name      String Domain name of the delegating party A.
      id        String Domain ID of the delegating party A.
      ========= ====== ======================================

   .. _en-us_topic_0064274720__table08421144254:

   .. table:: **Table 7** token.project

      +-----------------------------------------------------------+--------+----------------------------------------------+
      | Parameter                                                 | Type   | Description                                  |
      +===========================================================+========+==============================================+
      | name                                                      | String | Project name of delegating party A.          |
      +-----------------------------------------------------------+--------+----------------------------------------------+
      | id                                                        | String | Project ID of delegating party A.            |
      +-----------------------------------------------------------+--------+----------------------------------------------+
      | :ref:`domain <en-us_topic_0064274720__table138436441651>` | Object | Domain information about delegating party A. |
      +-----------------------------------------------------------+--------+----------------------------------------------+

   .. _en-us_topic_0064274720__table138436441651:

   .. table:: **Table 8** token.project.domain

      ========= ====== ======================================
      Parameter Type   Description
      ========= ====== ======================================
      name      String Domain name of the delegating party A.
      id        String Domain ID of the delegating party A.
      ========= ====== ======================================

   .. _en-us_topic_0064274720__table16843544651:

   .. table:: **Table 9** token.roles

      +-----------+--------+-----------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                             |
      +===========+========+=========================================================================================+
      | name      | String | Permission name.                                                                        |
      +-----------+--------+-----------------------------------------------------------------------------------------+
      | id        | String | Permission ID. The default value is **0**, which does not correspond to any permission. |
      +-----------+--------+-----------------------------------------------------------------------------------------+

   .. _en-us_topic_0064274720__table1484415441657:

   .. table:: **Table 10** token.user

      +------------------------------------------------------------+--------+---------------------------------------------------+
      | Parameter                                                  | Type   | Description                                       |
      +============================================================+========+===================================================+
      | name                                                       | String | Domain name or agency name of delegating party A. |
      +------------------------------------------------------------+--------+---------------------------------------------------+
      | id                                                         | String | Agency ID.                                        |
      +------------------------------------------------------------+--------+---------------------------------------------------+
      | :ref:`domain <en-us_topic_0064274720__table6845164417519>` | Object | Domain information about delegating party A.      |
      +------------------------------------------------------------+--------+---------------------------------------------------+

   .. _en-us_topic_0064274720__table6845164417519:

   .. table:: **Table 11** token.user.domain

      ========= ====== ======================================
      Parameter Type   Description
      ========= ====== ======================================
      id        String Domain ID of the delegating party A.
      name      String Domain name of the delegating party A.
      ========= ====== ======================================

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
