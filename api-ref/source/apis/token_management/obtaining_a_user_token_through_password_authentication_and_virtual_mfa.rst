:original_name: iam_03_0006.html

.. _iam_03_0006:

Obtaining a User Token Through Password Authentication and Virtual MFA
======================================================================

Function
--------

This API is used to obtain an IAM user token using the username, password, and virtual MFA device. To use this API, ensure that virtual MFA-based login protection has been enabled for the IAM user. A token is an access credential issued to a user to bear its identity and permissions. The token obtained using this API can be used to authenticate API calls to IAM and other cloud services.

URI
---

POST /v3/auth/tokens

.. table:: **Table 1** Query parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                              |
   +===========+===========+========+==========================================================================================================================================================================================================================+
   | nocatalog | No        | String | If this parameter is set, no catalog information will be displayed in the response. Any non-empty string for this parameter will be interpreted as **true** and indicates that no catalog information will be displayed. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                          |
   +==============+===========+========+======================================================+
   | Content-Type | Yes       | String | Set this field to **application/json;charset=utf8**. |
   +--------------+-----------+--------+------------------------------------------------------+

.. table:: **Table 3** Parameters in the request body

   +----------------------------------------------------------------------+-----------+--------+-----------------------------+
   | Parameter                                                            | Mandatory | Type   | Description                 |
   +======================================================================+===========+========+=============================+
   | :ref:`auth <iam_03_0006__en-us_topic_0221482385_request_rq3100auth>` | Yes       | Object | Authentication information. |
   +----------------------------------------------------------------------+-----------+--------+-----------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq3100auth:

.. table:: **Table 4** auth

   +----------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                        | Mandatory       | Type            | Description                                                                                                                                                 |
   +==================================================================================+=================+=================+=============================================================================================================================================================+
   | :ref:`identity <iam_03_0006__en-us_topic_0221482385_request_rq3100authidentity>` | Yes             | Object          | Authentication parameters.                                                                                                                                  |
   +----------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`scope <iam_03_0006__en-us_topic_0221482385_request_rq31authscope>`         | Yes             | Object          | Application scope of the token. Value options: **project** and **domain**.                                                                                  |
   |                                                                                  |                 |                 |                                                                                                                                                             |
   |                                                                                  |                 |                 | .. note::                                                                                                                                                   |
   |                                                                                  |                 |                 |                                                                                                                                                             |
   |                                                                                  |                 |                 |    -  **If the scope is set to domain, the token applies to global services. If the scope is set to project, the token applies to project-level services.** |
   |                                                                                  |                 |                 |    -  **If the scope is set to both project and domain, the project is used and you get a token for project-level services.**                               |
   |                                                                                  |                 |                 |    -  **If the scope is left blank, you get a token for global services. You are advised to specify this parameter.**                                       |
   +----------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq3100authidentity:

.. table:: **Table 5** auth.identity

   +-----------------------------------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                         | Mandatory       | Type             | Description                                                                                                               |
   +===================================================================================+=================+==================+===========================================================================================================================+
   | methods                                                                           | Yes             | Array of strings | Authentication method.                                                                                                    |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | The options are as follows:                                                                                               |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | -  password                                                                                                               |
   |                                                                                   |                 |                  | -  totp                                                                                                                   |
   +-----------------------------------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | :ref:`password <iam_03_0006__en-us_topic_0221482385_request_rq31authidentitypwd>` | Yes             | Object           | IAM user password authentication information.                                                                             |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | .. note::                                                                                                                 |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |    Authentication information. Example:                                                                                   |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |    .. code-block::                                                                                                        |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |       "password": {                                                                                                       |
   |                                                                                   |                 |                  |               "user": {                                                                                                   |
   |                                                                                   |                 |                  |                 "name": "user A",                                                                                         |
   |                                                                                   |                 |                  |                 "password": "**********",                                                                                 |
   |                                                                                   |                 |                  |                 "domain": {                                                                                               |
   |                                                                                   |                 |                  |                   "name": "domain A"                                                                                      |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |    -  **user.name**: Name of the user that wants to obtain the token. Obtain the username on the **My Credentials** page. |
   |                                                                                   |                 |                  |    -  **password**: Login password of the user.                                                                           |
   |                                                                                   |                 |                  |    -  **domain.name**: Name of the domain that created the user. Obtain the domain name on the **My Credentials** page.   |
   +-----------------------------------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+
   | :ref:`totp <iam_03_0006__en-us_topic_0221482385_request_rq3100authidentitytotp>`  | Yes             | Object           | Authentication information. This parameter is mandatory only if you have enabled virtual MFA-based login protection.      |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | You can specify either **user.id** or **user.name**.                                                                      |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | .. caution::                                                                                                              |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |    CAUTION:                                                                                                               |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | Example 1:                                                                                                                |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | .. code-block::                                                                                                           |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |    "totp": {                                                                                                              |
   |                                                                                   |                 |                  |            "user": {                                                                                                      |
   |                                                                                   |                 |                  |              "id": "b95b78b67fa045b38104c12fb...",                                                                        |
   |                                                                                   |                 |                  |              "passcode": "******"                                                                                         |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | -  **user.id**: User ID, which can be obtained on the **My Credentials** page.                                            |
   |                                                                                   |                 |                  | -  **passcode**: MFA verification code, which can be obtained on the MFA App.                                             |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | Example 2:                                                                                                                |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | .. code-block::                                                                                                           |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  |    "totp": {                                                                                                              |
   |                                                                                   |                 |                  |            "user": {                                                                                                      |
   |                                                                                   |                 |                  |              "name": "user A",                                                                                            |
   |                                                                                   |                 |                  |              "passcode": "******"                                                                                         |
   |                                                                                   |                 |                  |                                                                                                                           |
   |                                                                                   |                 |                  | -  **user.name**: Name of the user that wants to obtain the token.                                                        |
   |                                                                                   |                 |                  | -  **passcode**: MFA verification code, which can be obtained on the MFA App.                                             |
   +-----------------------------------------------------------------------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq31authidentitypwd:

.. table:: **Table 6** auth.identity.password

   +-----------------------------------------------------------------------------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter                                                                         | Mandatory | Type   | Description                                                         |
   +===================================================================================+===========+========+=====================================================================+
   | :ref:`user <iam_03_0006__en-us_topic_0221482385_request_rq31authidentitypwduser>` | Yes       | Object | Information about the IAM user who is requesting to obtain a token. |
   +-----------------------------------------------------------------------------------+-----------+--------+---------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq31authidentitypwduser:

.. table:: **Table 7** auth.identity.password.user

   +-------------------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                 | Mandatory       | Type            | Description                                                                                                                                                                                                             |
   +===========================================================================================+=================+=================+=========================================================================================================================================================================================================================+
   | :ref:`domain <iam_03_0006__en-us_topic_0221482385_request_rq31authidentitypwduserdomain>` | Yes             | Object          | Information about the account used to create the IAM user.                                                                                                                                                              |
   +-------------------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                                                                      | Yes             | String          | IAM username.                                                                                                                                                                                                           |
   +-------------------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | password                                                                                  | Yes             | String          | Password of the IAM user.                                                                                                                                                                                               |
   |                                                                                           |                 |                 |                                                                                                                                                                                                                         |
   |                                                                                           |                 |                 | .. note::                                                                                                                                                                                                               |
   |                                                                                           |                 |                 |                                                                                                                                                                                                                         |
   |                                                                                           |                 |                 |    -  To obtain a token successfully, ensure that the password you provide is correct.                                                                                                                                  |
   |                                                                                           |                 |                 |    -  A third-party system user cannot directly obtain a token by using the username and password used for identity federation. Go to the cloud platform login page, click **Forgot Password**, and reset the password. |
   +-------------------------------------------------------------------------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq31authidentitypwduserdomain:

.. table:: **Table 8** auth.identity.password.user.domain

   +-----------+-----------+--------+--------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                      |
   +===========+===========+========+==================================================+
   | name      | Yes       | String | Name of the account used to create the IAM user. |
   +-----------+-----------+--------+--------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq3100authidentitytotp:

.. table:: **Table 9** auth.identity.totp

   +--------------------------------------------------------------------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                            | Mandatory | Type   | Description                                                                                                                             |
   +======================================================================================+===========+========+=========================================================================================================================================+
   | :ref:`user <iam_03_0006__en-us_topic_0221482385_request_rq3100authidentitytotpuser>` | Yes       | Object | IAM user information. Login protection has been enabled for the IAM user, and a virtual MFA device is used for identity authentication. |
   +--------------------------------------------------------------------------------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq3100authidentitytotpuser:

.. table:: **Table 10** auth.identity.totp.user

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                  |
   +=================+=================+=================+==============================================================================================+
   | id              | Yes             | String          | ID of the IAM user for whom virtual MFA-based login protection has been enabled.             |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | passcode        | Yes             | String          | MFA verification code, which can be obtained on the MFA App.                                 |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | .. note::                                                                                    |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 |    To obtain a token successfully, ensure that the verification code you provide is correct. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq31authscope:

.. table:: **Table 11** auth.scope

   +-----------------------------------------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                         | Mandatory | Type   | Description                                                                                                                                                                                                                                |
   +===================================================================================+===========+========+============================================================================================================================================================================================================================================+
   | :ref:`domain <iam_03_0006__en-us_topic_0221482385_request_rq31authscopedomain>`   | No        | Object | If this parameter is set to **domain**, the token can be used to access global services, such as OBS. Global services are not subject to any projects or regions. You can specify either **id** or **name**. **domain.id** is recommended. |
   +-----------------------------------------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`project <iam_03_0006__en-us_topic_0221482385_request_rq31authscopeproject>` | No        | Object | If this parameter is set to **project**, the token can be used to access only services (such as ECS) in specific projects. You can specify either **id** or **name**.                                                                      |
   +-----------------------------------------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq31authscopedomain:

.. table:: **Table 12** auth.scope.domain

   +-----------+-----------+--------+--------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                      |
   +===========+===========+========+==================================================+
   | id        | No        | String | ID of the account used to create the IAM user.   |
   +-----------+-----------+--------+--------------------------------------------------+
   | name      | No        | String | Name of the account used to create the IAM user. |
   +-----------+-----------+--------+--------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_request_rq31authscopeproject:

.. table:: **Table 13** auth.scope.project

   +-----------+-----------+--------+----------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                              |
   +===========+===========+========+==========================================================+
   | id        | No        | String | ID of the project to which the IAM user belongs.         |
   +-----------+-----------+--------+----------------------------------------------------------+
   | name      | No        | String | Project name of the account used to create the IAM user. |
   +-----------+-----------+--------+----------------------------------------------------------+

Example Request
---------------

-  Sample request

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
                          "name": "user A",
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

Response
--------

.. table:: **Table 14** Parameters in the response header

   =============== ====== =============
   Parameter       Type   Description
   =============== ====== =============
   X-Subject-Token String Signed token.
   =============== ====== =============

.. table:: **Table 15** Parameters in the response body

   +-----------------------------------------------------------------------+--------+--------------------+
   | Parameter                                                             | Type   | Description        |
   +=======================================================================+========+====================+
   | :ref:`token <iam_03_0006__en-us_topic_0221482385_response_rs31token>` | Object | Token information. |
   +-----------------------------------------------------------------------+--------+--------------------+

.. _iam_03_0006__en-us_topic_0221482385_response_rs31token:

.. table:: **Table 16** token

   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                             | Type             | Description                                                                                                                                                                      |
   +=======================================================================================+==================+==================================================================================================================================================================================+
   | :ref:`catalog <iam_03_0006__en-us_topic_0221482385_response_rs31tokencatalogarritem>` | Array of objects | Endpoint information.                                                                                                                                                            |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`domain <iam_03_0006__en-us_topic_0221482385_response_rs31tokendomain>`          | Object           | Account information about the IAM user who requests for the token. This parameter is returned only when the **scope** parameter in the request body has been set to **domain**.  |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expires_at                                                                            | String           | Expiration date of the token.                                                                                                                                                    |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | issued_at                                                                             | String           | Time when the token was issued.                                                                                                                                                  |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mfa_authn_at                                                                          | String           | MFA authentication time. This field is displayed only when virtual MFA-based login authentication is enabled.                                                                    |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | methods                                                                               | Array of strings | Method for obtaining the token.                                                                                                                                                  |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`project <iam_03_0006__en-us_topic_0221482385_response_rs31tokenproject>`        | Object           | Project information about the IAM user who requests for the token. This parameter is returned only when the **scope** parameter in the request body has been set to **project**. |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`roles <iam_03_0006__en-us_topic_0221482385_response_rs31tokenrolesarritem>`     | Array of objects | Permissions information of the token.                                                                                                                                            |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`user <iam_03_0006__en-us_topic_0221482385_response_rs31tokenuser>`              | Object           | Information about the IAM user who requests for the token.                                                                                                                       |
   +---------------------------------------------------------------------------------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokencatalogarritem:

.. table:: **Table 17** token.catalog

   +---------------------------------------------------------------------------------------------------------+------------------+-----------------------------------------------+
   | Parameter                                                                                               | Type             | Description                                   |
   +=========================================================================================================+==================+===============================================+
   | :ref:`endpoints <iam_03_0006__en-us_topic_0221482385_response_rs31tokencatalogarritemendpointsarritem>` | Array of objects | Endpoint information.                         |
   +---------------------------------------------------------------------------------------------------------+------------------+-----------------------------------------------+
   | id                                                                                                      | String           | Service ID.                                   |
   +---------------------------------------------------------------------------------------------------------+------------------+-----------------------------------------------+
   | name                                                                                                    | String           | Service name.                                 |
   +---------------------------------------------------------------------------------------------------------+------------------+-----------------------------------------------+
   | type                                                                                                    | String           | Type of the service to which the API belongs. |
   +---------------------------------------------------------------------------------------------------------+------------------+-----------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokencatalogarritemendpointsarritem:

.. table:: **Table 18** token.catalog.endpoints

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

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokendomain:

.. table:: **Table 19** token.domain

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   name      String Domain name.
   id        String Domain ID.
   ========= ====== ============

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokenproject:

.. table:: **Table 20** token.project

   +-------------------------------------------------------------------------------------+--------+------------------------------------+
   | Parameter                                                                           | Type   | Description                        |
   +=====================================================================================+========+====================================+
   | :ref:`domain <iam_03_0006__en-us_topic_0221482385_response_rs31tokenprojectdomain>` | Object | Domain information of the project. |
   +-------------------------------------------------------------------------------------+--------+------------------------------------+
   | id                                                                                  | String | Project ID.                        |
   +-------------------------------------------------------------------------------------+--------+------------------------------------+
   | name                                                                                | String | Project name.                      |
   +-------------------------------------------------------------------------------------+--------+------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokenprojectdomain:

.. table:: **Table 21** token.project.domain

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   id        String Domain ID.
   name      String Domain name.
   ========= ====== ============

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokenrolesarritem:

.. table:: **Table 22** token.roles

   +-----------+--------+-----------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                             |
   +===========+========+=========================================================================================+
   | name      | String | Permission name.                                                                        |
   +-----------+--------+-----------------------------------------------------------------------------------------+
   | id        | String | Permission ID. The default value is **0**, which does not correspond to any permission. |
   +-----------+--------+-----------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokenuser:

.. table:: **Table 23** token.user

   +----------------------------------------------------------------------------------+--------+-----------------------------------------------------------------------------------------------+
   | Parameter                                                                        | Type   | Description                                                                                   |
   +==================================================================================+========+===============================================================================================+
   | name                                                                             | String | IAM username.                                                                                 |
   +----------------------------------------------------------------------------------+--------+-----------------------------------------------------------------------------------------------+
   | id                                                                               | String | IAM user ID.                                                                                  |
   +----------------------------------------------------------------------------------+--------+-----------------------------------------------------------------------------------------------+
   | password_expires_at                                                              | String | Password expiration time. If this parameter is not specified, the password will never expire. |
   +----------------------------------------------------------------------------------+--------+-----------------------------------------------------------------------------------------------+
   | :ref:`domain <iam_03_0006__en-us_topic_0221482385_response_rs31tokenuserdomain>` | Object | Information about the account used to create the IAM user.                                    |
   +----------------------------------------------------------------------------------+--------+-----------------------------------------------------------------------------------------------+

.. _iam_03_0006__en-us_topic_0221482385_response_rs31tokenuserdomain:

.. table:: **Table 24** token.user.domain

   ========= ====== ================================================
   Parameter Type   Description
   ========= ====== ================================================
   name      String Name of the account used to create the IAM user.
   id        String ID of the account used to create the IAM user.
   ========= ====== ================================================

Example Response
----------------

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

=========== ================================
Status Code Description
=========== ================================
201         Creation succeeded.
400         Invalid parameters.
401         Authentication failed.
403         Access denied.
404         Requested resource cannot found.
500         Internal server error.
503         Service unavailable.
=========== ================================
