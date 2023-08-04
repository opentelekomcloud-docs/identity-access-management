:original_name: iam_13_0209.html

.. _iam_13_0209:

Querying an OpenID Connect Identity Provider
============================================

Function
--------

This API is provided for the administrator to query an OpenID Connect identity provider.

URI
---

GET /v3.0/OS-FEDERATION/identity-providers/{idp_id}/openid-connect-config

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+----------------------------+
   | Parameter       | Mandatory       | Type            | Description                |
   +=================+=================+=================+============================+
   | idp_id          | Yes             | String          | Identity provider ID.      |
   |                 |                 |                 |                            |
   |                 |                 |                 | Length: 1 to 64 characters |
   +-----------------+-----------------+-----------------+----------------------------+

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions.    |
   +--------------+-----------+--------+-------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Parameters in the response body

   +------------------------------------------------------------------+--------+--------------------------------+
   | Parameter                                                        | Type   | Description                    |
   +==================================================================+========+================================+
   | :ref:`openid_connect_config <iam_13_0209__table106271415184212>` | object | OpenID Connect configurations. |
   +------------------------------------------------------------------+--------+--------------------------------+

.. _iam_13_0209__table106271415184212:

.. table:: **Table 4** OpenIDConnectConfig

   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                               |
   +========================+=======================+===========================================================================================================+
   | access_mode            | String                | Access type. Options:                                                                                     |
   |                        |                       |                                                                                                           |
   |                        |                       | -  **program_console**: programmatic access and management console access.                                |
   |                        |                       | -  **program**: programmatic access only.                                                                 |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | idp_url                | String                | URL of the OpenID Connect identity provider. This field corresponds to the **iss** field in the ID token. |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | client_id              | String                | ID of a client registered with the OpenID Connect identity provider.                                      |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | authorization_endpoint | String                | Authorization endpoint of the OpenID Connect identity provider.                                           |
   |                        |                       |                                                                                                           |
   |                        |                       | This field is required only if **access_mode** is set to **program_console**.                             |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | scope                  | String                | Scope of authorization requests.                                                                          |
   |                        |                       |                                                                                                           |
   |                        |                       | This field is required only if **access_mode** is set to **program_console**.                             |
   |                        |                       |                                                                                                           |
   |                        |                       | Enumerated values:                                                                                        |
   |                        |                       |                                                                                                           |
   |                        |                       | -  openid                                                                                                 |
   |                        |                       | -  email                                                                                                  |
   |                        |                       | -  profile                                                                                                |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | response_type          | String                | Response type.                                                                                            |
   |                        |                       |                                                                                                           |
   |                        |                       | This field is required only if **access_mode** is set to **program_console**.                             |
   |                        |                       |                                                                                                           |
   |                        |                       | Enumerated value:                                                                                         |
   |                        |                       |                                                                                                           |
   |                        |                       | -  id_token                                                                                               |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | response_mode          | String                | Response mode.                                                                                            |
   |                        |                       |                                                                                                           |
   |                        |                       | This field is required only if **access_mode** is set to **program_console**.                             |
   |                        |                       |                                                                                                           |
   |                        |                       | Enumerated values:                                                                                        |
   |                        |                       |                                                                                                           |
   |                        |                       | -  fragment                                                                                               |
   |                        |                       | -  form_post                                                                                              |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
   | signing_key            | String                | Public key used to sign the ID token of the OpenID Connect identity provider.                             |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{address}/v3.0/OS-FEDERATION/identity-providers/{idp_id}/openid-connect-config

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "openid_connect_config" : {
       "access_mode" : "program_console",
       "idp_url" : "https://accounts.example.com",
       "client_id" : "client_id_example",
       "authorization_endpoint" : "https://accounts.example.com/o/oauth2/v2/auth",
       "scope" : "openid",
       "response_type" : "id_token",
       "response_mode" : "form_post",
       "signing_key" : "{\"keys\":[{\"kty\":\"RSA\",\"e\":\"AQAB\",\"use\":\"sig\",\"n\":\"example\",\"kid\":\"kid_example\",\"alg\":\"RS256\"}]}"
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
     "error_msg" : "Request parameter %(key)s is invalid.",
     "error_code" : "IAM.0007"
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
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal system error.
=========== =========================================
