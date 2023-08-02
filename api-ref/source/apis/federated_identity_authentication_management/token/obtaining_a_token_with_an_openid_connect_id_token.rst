:original_name: iam_13_0605.html

.. _iam_13_0605:

Obtaining a Token with an OpenID Connect ID Token
=================================================

Function
--------

This API is used to obtain a federated identity authentication token using an OpenID Connect ID token.

URI
---

POST /v3.0/OS-AUTH/id-token/tokens

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Idp-Id     | Yes       | String | Identity provider ID.                                 |
   +--------------+-----------+--------+-------------------------------------------------------+

.. table:: **Table 2** Parameters in the request body

   +-----------------------------------------------+-----------+--------+-----------------------------------------------+
   | Parameter                                     | Mandatory | Type   | Description                                   |
   +===============================================+===========+========+===============================================+
   | :ref:`auth <iam_13_0605__table2037015569431>` | Yes       | object | Details about the **auth** request parameter. |
   +-----------------------------------------------+-----------+--------+-----------------------------------------------+

.. _iam_13_0605__table2037015569431:

.. table:: **Table 3** GetIdTokenAuthParams

   +----------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                          | Mandatory | Type   | Description                                                                                                              |
   +====================================================+===========+========+==========================================================================================================================+
   | :ref:`id_token <iam_13_0605__table18374185617432>` | Yes       | object | Details about an ID token.                                                                                               |
   +----------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | :ref:`scope <iam_13_0605__table203761056124311>`   | No        | object | Permission scope of the token you want to obtain. An unscoped token will be obtained if this parameter is not specified. |
   +----------------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. _iam_13_0605__table18374185617432:

.. table:: **Table 4** GetIdTokenIdTokenBody

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                   |
   +===========+===========+========+===============================================================================================================================================================================================+
   | id        | Yes       | String | ID token, which is constructed by the enterprise IdP to carry the identity information of federated users. For details about how to obtain an ID token, see the enterprise IdP documentation. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _iam_13_0605__table203761056124311:

.. table:: **Table 5** GetIdTokenIdScopeBody

   +--------------------------------------------------+-----------+--------+-------------------------------------------------------+
   | Parameter                                        | Mandatory | Type   | Description                                           |
   +==================================================+===========+========+=======================================================+
   | :ref:`domain <iam_13_0605__table1379356134320>`  | No        | object | Domain scope details. Specify a domain or a project.  |
   +--------------------------------------------------+-----------+--------+-------------------------------------------------------+
   | :ref:`project <iam_13_0605__table1379356134320>` | No        | object | Project scope details. Specify a project or a domain. |
   +--------------------------------------------------+-----------+--------+-------------------------------------------------------+

.. _iam_13_0605__table1379356134320:

.. table:: **Table 6** GetIdTokenScopeDomainOrProjectBody

   +-----------+-----------+--------+-------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                         |
   +===========+===========+========+=====================================================================================+
   | id        | No        | String | Domain ID or project ID. Specify either this parameter or the **name** parameter.   |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------+
   | name      | No        | String | Domain name or project name. Specify either this parameter or the **id** parameter. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 7** Parameters in the response header

   =============== ====== =============
   Parameter       Type   Description
   =============== ====== =============
   X-Subject-Token String Signed token.
   =============== ====== =============

.. table:: **Table 8** Parameters in the response body

   +--------------------------------------------------+--------+-----------------------------------+
   | Parameter                                        | Type   | Description                       |
   +==================================================+========+===================================+
   | :ref:`token <iam_13_0605__table103881956114312>` | object | Details about the obtained token. |
   +--------------------------------------------------+--------+-----------------------------------+

.. _iam_13_0605__table103881956114312:

.. table:: **Table 9** ScopedTokenInfo

   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter                                         | Type             | Description                                                                                             |
   +===================================================+==================+=========================================================================================================+
   | expires_at                                        | String           | Time when the token will expire.                                                                        |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | methods                                           | Array of strings | Method for obtaining the token. For federated users, the default value of this parameter is **mapped**. |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | issued_at                                         | String           | Time when the token was issued.                                                                         |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | :ref:`user <iam_13_0605__table63957566436>`       | object           | User details.                                                                                           |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | :ref:`domain <iam_13_0605__table104051456104311>` | object           | Domain details.                                                                                         |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | :ref:`project <iam_13_0605__table18407115614438>` | object           | Project details.                                                                                        |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | role                                              | Array            | Policy details.                                                                                         |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+
   | :ref:`catalog <iam_13_0605__table14410115674311>` | object           | Catalog details.                                                                                        |
   +---------------------------------------------------+------------------+---------------------------------------------------------------------------------------------------------+

.. _iam_13_0605__table63957566436:

.. table:: **Table 10** FederationUserBody

   +--------------------------------------------------------+--------+-------------------------+
   | Parameter                                              | Type   | Description             |
   +========================================================+========+=========================+
   | :ref:`OS-FEDERATION <iam_13_0605__table1739620561434>` | object | Federated user details. |
   +--------------------------------------------------------+--------+-------------------------+

.. _iam_13_0605__table1739620561434:

.. table:: **Table 11** OSFederationInfo

   +------------------------------------------------------------+--------+----------------------------+
   | Parameter                                                  | Type   | Description                |
   +============================================================+========+============================+
   | :ref:`identify_provider <iam_13_0605__table1401155654314>` | object | Identity provider details. |
   +------------------------------------------------------------+--------+----------------------------+
   | :ref:`protocol <iam_13_0605__table1440310561432>`          | object | Protocol details.          |
   +------------------------------------------------------------+--------+----------------------------+
   | groups                                                     | Array  | User group details.        |
   +------------------------------------------------------------+--------+----------------------------+
   | :ref:`domain <iam_13_0605__table104051456104311>`          | object | Domain details.            |
   +------------------------------------------------------------+--------+----------------------------+
   | id                                                         | String | User ID.                   |
   +------------------------------------------------------------+--------+----------------------------+
   | name                                                       | String | Username.                  |
   +------------------------------------------------------------+--------+----------------------------+

.. _iam_13_0605__table1401155654314:

.. table:: **Table 12** IdpIdInfo

   ========= ====== =====================
   Parameter Type   Description
   ========= ====== =====================
   id        String Identity provider ID.
   ========= ====== =====================

.. _iam_13_0605__table1440310561432:

.. table:: **Table 13** ProtocolIdInfo

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   id        String Protocol ID.
   ========= ====== ============

.. _iam_13_0605__table104051456104311:

.. table:: **Table 14** DomainInfo

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   id        String Domain ID.
   name      String Domain name.
   ========= ====== ============

.. _iam_13_0605__table18407115614438:

.. table:: **Table 15** ProjectInfo

   ================================================= ====== ===============
   Parameter                                         Type   Description
   ================================================= ====== ===============
   :ref:`domain <iam_13_0605__table104051456104311>` object Domain details.
   id                                                String Project ID.
   name                                              String Project name.
   ================================================= ====== ===============

.. _iam_13_0605__table14410115674311:

.. table:: **Table 16** CatalogInfo

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

Example Request
---------------

-  Request for obtaining a scoped token for a specific project

   .. code-block:: text

      POST /v3.0/OS-AUTH/id-token/tokens

       {
         "auth" : {
           "id_token" : {
             "id" : "eyJhbGciOiJSU..."
           },
           "scope" : {
             "project" : {
               "id" : "46419baef4324...",
               "name" : "project name"
             }
           }
         }
       }

-  Request for obtaining a scoped token for a specific domain

   .. code-block:: text

      POST /v3.0/OS-AUTH/id-token/tokens

       {
         "auth" : {
           "id_token" : {
             "id" : "eyJhbGciOiJSU..."
           },
           "scope" : {
             "domain" : {
               "id" : "063bb260a480...",
               "name" : "IAMDomain"
             }
           }
         }
       }

-  Request for obtaining an unscoped token

   .. code-block:: text

      POST /v3.0/OS-AUTH/id-token/tokens

       {
         "auth" : {
           "id_token" : {
             "id" : "eyJhbGciOiJSU..."
           }
         }
       }

Example Response
----------------

**Status code: 201**

The token is obtained successfully.

.. code-block::

   {
     "token" : {
       "expires_at" : "2018-03-13T03:00:01.168000Z",
       "methods" : [ "mapped" ],
       "issued_at" : "2018-03-12T03:00:01.168000Z",
       "user" : {
         "OS-FEDERATION" : {
           "identity_provider" : {
             "id" : "idptest"
           },
           "protocol" : {
             "id" : "oidc"
           },
           "groups" : [ {
             "name" : "admin",
             "id" : "45a8c8f..."
           } ]
         },
         "domain" : {
           "id" : "063bb260a480...",
           "name" : "IAMDomain"
         },
         "name" : "FederationUser",
         "id" : "suvmgvUZc4PaCOEc..."
       }
     }
   }

**Status code: 400**

The server failed to process the request.

.. code-block::

   {
     "error_msg" : "Request body is invalid.",
     "error_code" : "IAM.0011"
   }

**Status code: 401**

Authentication failed.

.. code-block::

   {
     "error_msg" : "The request you have made requires authentication.",
     "error_code" : "IAM.0001"
   }

**Status code: 403**

Access denied.

.. code-block::

   {
     "error_msg" : "Policy doesn't allow %(actions)s to be performed.",
     "error_code" : "IAM.0003"
   }

**Status code: 404**

The requested resource cannot be found.

.. code-block::

   {
     "error_msg" : "Could not find %(target)s: %(target_id)s.",
     "error_code" : "IAM.0004"
   }

**Status code: 500**

Internal system error.

.. code-block::

   {
     "error_msg" : "An unexpected error prevented the server from fulfilling your request.",
     "error_code" : "IAM.0006"
   }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
201         The token is obtained successfully.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal system error.
=========== =========================================
