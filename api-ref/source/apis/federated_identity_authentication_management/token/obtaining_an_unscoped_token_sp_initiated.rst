:original_name: en-us_topic_0057845629.html

.. _en-us_topic_0057845629:

Obtaining an Unscoped Token (SP Initiated)
==========================================

Function
--------

This API is used to obtain an unscoped token in SP-initiated federated identity authentication mode.

An unscoped token cannot be used for authentication. If a federated user needs to use a token for authentication, obtain the scoped token based on section :ref:`Obtaining a Scoped Token <iam_13_0604>`.

URI
---

-  URI format

   GET /v3/OS-FEDERATION/identity_providers/{idp_id}/protocols/{protocol_id}/auth

-  URI parameters

   ============= ========= ====== ===========================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ===========================
   idp_id        Yes       String ID of an identity provider.
   protocol \_id Yes       String ID of a protocol.
   ============= ========= ====== ===========================

Request Parameters
------------------

-  Parameters in the request header

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | Accept          | No              | String          | -  This parameter is not required when a token is obtained in the WebSSO mode.                               |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  When you obtain a token using the Enhanced Client Proxy (ECP), the value of this parameter is as follows: |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 |    application/vnd.paos+xml                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | PAOS            | No              | String          | -  This parameter is not required when a token is obtained in the WebSSO mode.                               |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | -  When you obtain a token using the ECP, the value of this parameter is as follows:                         |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 |    urn:oasis:names:tc:SAML:2.0:profiles:SSO:ecp                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

   .. note::

      #. This API can be used to obtain tokens through WebSSO and ECP. Different request headers are used to determine the method of obtaining a token. For details, see the parameter description of Request Header.
      #. You are not advised to obtain a token by directly calling this API. You are advised to obtain a token using OpenStackClient.

-  Example request

   .. code-block:: text

      GET /v3/OS-FEDERATION/identity_providers/idptest/protocols/saml/auth

Response Parameters
-------------------

-  Parameters in the response body

   +-----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Response Item   | Parameter | Type   | Description                                                                                                                   |
   +=================+===========+========+===============================================================================================================================+
   | X-Subject-Token | header    | String | Signed unscoped token.                                                                                                        |
   +-----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | token           | body      | Object | Information of the unscoped token obtained in federated identity authentication mode, including methods and user information. |
   +-----------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "token": {
              "issued_at": "2017-05-23T06:54:51.763000Z",
              "expires_at": "2017-05-24T06:54:51.763000Z",
              "methods": [
                  "mapped"
              ],
              "user": {
                  "domain": {
                      "id": "e31ac82d778b4d128cb6fed37fd72cdb",
                      "name": "exampledomain"
                  },
                  "id": "RMQTgtjjSNGDcKy7oUmI3AZg7GgsWG0Z",
                  "name": "exampleuser",
                  "OS-FEDERATION": {
                      "identity_provider": {
                          "id": "exampleuser"
                      },
                      "protocol": {
                          "id": "saml"
                      },
                      "groups": [
                          {
                              "id": "b40189e26ea44f959877621b4b298db5"
                          }
                      ]
                  }
              }
          }
      }

Status Code
-----------

+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                               |
+=============+===========================================================================================================================================+
| 200         | The request is successful. You need to further obtain user information.                                                                   |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 201         | The request is successful, and a token is returned.                                                                                       |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 302         | The system switches to the identity provider authentication page if the request does not carry user information of the identity provider. |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                                                                                 |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                                                                                    |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 403         | Access denied.                                                                                                                            |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource.                                                            |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                                                                                          |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 500         | Internal server error.                                                                                                                    |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                                                                                      |
+-------------+-------------------------------------------------------------------------------------------------------------------------------------------+
