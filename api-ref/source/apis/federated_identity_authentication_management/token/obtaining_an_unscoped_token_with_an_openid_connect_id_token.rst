:original_name: iam_13_0606.html

.. _iam_13_0606:

Obtaining an Unscoped Token with an OpenID Connect ID Token
===========================================================

Function
--------

This API is used to obtain an unscoped token using an OpenID Connect ID token.

URI
---

POST /v3/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}/auth

.. table:: **Table 1** URI parameters

   =========== ========= ====== =====================
   Parameter   Mandatory Type   Description
   =========== ========= ====== =====================
   idp_id      Yes       String Identity provider ID.
   protocol_id Yes       String Protocol ID.
   =========== ========= ====== =====================

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +---------------+-----------+--------+---------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                               |
   +===============+===========+========+===========================================================================+
   | Authorization | Yes       | String | ID token of the identity provider. The format is **Bearer** *{ID Token}*. |
   +---------------+-----------+--------+---------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 3** Parameters in the response header

   =============== ====== =============
   Parameter       Type   Description
   =============== ====== =============
   X-Subject-Token String Signed token.
   =============== ====== =============

.. table:: **Table 4** Parameters in the response body

   +------------------------------------------------+--------+-----------------------------------+
   | Parameter                                      | Type   | Description                       |
   +================================================+========+===================================+
   | :ref:`token <iam_13_0606__table1026565014509>` | object | Details about the obtained token. |
   +------------------------------------------------+--------+-----------------------------------+

.. _iam_13_0606__table1026565014509:

.. table:: **Table 5** UnscopedTokenInfo

   +-----------------------------------------------+------------------+---------------------------------------------------------------------------------------+
   | Parameter                                     | Type             | Description                                                                           |
   +===============================================+==================+=======================================================================================+
   | expires_at                                    | String           | Time when the token will expire.                                                      |
   +-----------------------------------------------+------------------+---------------------------------------------------------------------------------------+
   | methods                                       | Array of strings | Token obtaining method. The default value for federated authentication is **mapped**. |
   +-----------------------------------------------+------------------+---------------------------------------------------------------------------------------+
   | issued_at                                     | String           | Time when the token was issued.                                                       |
   +-----------------------------------------------+------------------+---------------------------------------------------------------------------------------+
   | :ref:`user <iam_13_0606__table1727255020503>` | object           | User details.                                                                         |
   +-----------------------------------------------+------------------+---------------------------------------------------------------------------------------+

.. _iam_13_0606__table1727255020503:

.. table:: **Table 6** FederationUserBody

   +---------------------------------------------------------+--------+-------------------------+
   | Parameter                                               | Type   | Description             |
   +=========================================================+========+=========================+
   | :ref:`OS-FEDERATION <iam_13_0606__table10275125045010>` | object | Federated user details. |
   +---------------------------------------------------------+--------+-------------------------+

.. _iam_13_0606__table10275125045010:

.. table:: **Table 7** OSFederationInfo

   +-----------------------------------------------------------+--------+----------------------------+
   | Parameter                                                 | Type   | Description                |
   +===========================================================+========+============================+
   | :ref:`identify_provider <iam_13_0606__table328505075012>` | object | Identity provider details. |
   +-----------------------------------------------------------+--------+----------------------------+
   | :ref:`protocol <iam_13_0606__table52881350195012>`        | object | Protocol details.          |
   +-----------------------------------------------------------+--------+----------------------------+
   | groups                                                    | Array  | User group details.        |
   +-----------------------------------------------------------+--------+----------------------------+
   | :ref:`domain <iam_13_0606__table13291150195018>`          | object | Domain details.            |
   +-----------------------------------------------------------+--------+----------------------------+
   | id                                                        | String | User ID.                   |
   +-----------------------------------------------------------+--------+----------------------------+
   | name                                                      | String | Username.                  |
   +-----------------------------------------------------------+--------+----------------------------+

.. _iam_13_0606__table328505075012:

.. table:: **Table 8** IdpIdInfo

   ========= ====== =====================
   Parameter Type   Description
   ========= ====== =====================
   id        String Identity provider ID.
   ========= ====== =====================

.. _iam_13_0606__table52881350195012:

.. table:: **Table 9** ProtocolIdInfo

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   id        String Protocol ID.
   ========= ====== ============

.. _iam_13_0606__table13291150195018:

.. table:: **Table 10** DomainInfo

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   id        String Domain ID.
   name      String Domain name.
   ========= ====== ============

Example Request
---------------

.. code-block:: text

   POST https://sample.domain.com/v3/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}/auth

Example Response
----------------

**Status code: 201**

The request is successful.

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
     "error" : {
       "code" : 400,
       "message" : "Request parameter 'idp id' is invalid.",
       "title" : "Bad Request"
     }
   }

**Status code: 401**

Authentication failed.

.. code-block::

   {
     "error" : {
       "code" : 401,
       "message" : "The request you have made requires authentication.",
       "title" : "Unauthorized"
     }
   }

**Status code: 403**

Access denied.

.. code-block::

   {
     "error" : {
       "code" : 403,
       "message" : "You are not authorized to perform the requested action.",
       "title" : "Forbidden"
     }
   }

**Status code: 404**

The requested resource cannot be found.

.. code-block::

   {
     "error" : {
       "code" : 404,
       "message" : "Could not find %(target)s: %(target_id)s.",
       "title" : "Not Found"
     }
   }

**Status code: 500**

Internal system error.

.. code-block::

   {
     "error" : {
       "code" : 500,
       "message" : "An unexpected error prevented the server from fulfilling your request.",
       "title" : "Internal Server Error"
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
500         Internal system error.
=========== =========================================
