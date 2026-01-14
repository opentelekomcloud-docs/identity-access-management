:original_name: iam_02_0003.html

.. _iam_02_0003:

Obtaining an Unscoped Token (IdP Initiated)
===========================================

Function
--------

This API is used to obtain an unscoped token in IdP-initiated federated identity authentication mode.

An unscoped token cannot be used for authentication. If a federated user needs to use a token for authentication, obtain the scoped token based on section :ref:`Obtaining a Scoped Token <iam_13_0604>`.

URI
---

POST /v3.0/OS-FEDERATION/tokens

Request Parameters
------------------

-  Parameters in the request header

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================+
   | X-Idp-Id        | Yes             | String          | ID of an identity provider.                                                                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | The client must transfer the SAMLResponse parameter to the server by using the form data submitted by the browser. Therefore, the value of this parameter must be: |
   |                 |                 |                 |                                                                                                                                                                    |
   |                 |                 |                 | application/x-www-form-urlencoded                                                                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameters in the request body

   +--------------+-----------+--------+---------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                   |
   +==============+===========+========+===============================================================+
   | SAMLResponse | Yes       | String | Response body returned when IdP authentication is successful. |
   +--------------+-----------+--------+---------------------------------------------------------------+

   .. note::

      This API can only be called on the CLI side. The client needs to obtain SAMLResponse in IdP-initiated federated identity authentication mode and obtain an unscoped token by using the form data submitted by the browser.

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'x-Idp-Id:test_local_idp' -H 'Content-Type:application/x-www-form-urlencoded' -X POST -d 'SAMLResponse=PD94bWwgdmVyc2lvbj0iMS4wIiBl4WXZ1OGNmYmRzWk1ZeWlLKy96anpEbm1rT2FrVVBrUmlSWEpLYUt5NzJtUmtoRFBCNjgwVQpzalU3R2hKNHE4ZG48L3hlbmM6Q2lwaGVyVmFsdWU%2BPC94ZW5jOkNpcGhlckRhdGE%2BPC94ZW5jOkVuY3J5cHRlZERhdGE%2BPC9zYW1sMjpFbmNyeXB0ZWRBc3NlcnRpb24%2BPC9zYW1sMnA6UmVzcG9uc2U%2B' https://sample.domain.com/v3.0/OS-FEDERATION/tokens

Response Parameters
-------------------

-  Parameters in the response header

   =============== ====== ======================
   Response Item   Type   Description
   =============== ====== ======================
   X-Subject-Token String Signed unscoped token.
   =============== ====== ======================

-  Parameters in the response body

   +----------------------------------------------+--------+-----------------------------------------------------------------------------------------------+
   | Parameter                                    | Type   | Description                                                                                   |
   +==============================================+========+===============================================================================================+
   | :ref:`token <iam_02_0003__li15757172383815>` | Object | Unscoped token for federated authentication, which contains the methods and user information. |
   +----------------------------------------------+--------+-----------------------------------------------------------------------------------------------+

-  .. _iam_02_0003__li15757172383815:

   token

   +---------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                   | Type                  | Description                                                                                                                                                                                                                                  |
   +=============================================+=======================+==============================================================================================================================================================================================================================================+
   | issued_at                                   | String                | Time when the token was issued.                                                                                                                                                                                                              |
   |                                             |                       |                                                                                                                                                                                                                                              |
   |                                             |                       | .. note::                                                                                                                                                                                                                                    |
   |                                             |                       |                                                                                                                                                                                                                                              |
   |                                             |                       |    The value is a UTC time in the YYYY-MM-DDTHH:mm:ss.ssssssZ format, for example, 2023-06-28T08:56:33.710000Z. For details about the date and timestamp formats, see `ISO-8601 <https://www.iso.org/iso-8601-date-and-time-format.html>`__. |
   +---------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expires_at                                  | String                | Expiration date of the token.                                                                                                                                                                                                                |
   |                                             |                       |                                                                                                                                                                                                                                              |
   |                                             |                       | .. note::                                                                                                                                                                                                                                    |
   |                                             |                       |                                                                                                                                                                                                                                              |
   |                                             |                       |    The value is a UTC time in the YYYY-MM-DDTHH:mm:ss.ssssssZ format, for example, 2023-06-28T08:56:33.710000Z. For details about the date and timestamp formats, see `ISO-8601 <https://www.iso.org/iso-8601-date-and-time-format.html>`__. |
   +---------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | methods                                     | Array of strings      | Method for obtaining the token.                                                                                                                                                                                                              |
   +---------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`user <iam_02_0003__li54901824143811>` | Object                | Information about the user who requests for the token.                                                                                                                                                                                       |
   +---------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _iam_02_0003__li54901824143811:

   token.user

   +----------------------------------------------------+--------+---------------------------------------------------------+
   | Parameter                                          | Type   | Description                                             |
   +====================================================+========+=========================================================+
   | :ref:`domain <iam_02_0003__li1494814115404>`       | Object | Information about the domain to which the user belongs. |
   +----------------------------------------------------+--------+---------------------------------------------------------+
   | id                                                 | String | User ID.                                                |
   +----------------------------------------------------+--------+---------------------------------------------------------+
   | name                                               | String | Username.                                               |
   +----------------------------------------------------+--------+---------------------------------------------------------+
   | :ref:`OS-FEDERATION <iam_02_0003__li094919112407>` | Object | Federated identity authentication information.          |
   +----------------------------------------------------+--------+---------------------------------------------------------+

-  .. _iam_02_0003__li1494814115404:

   token.user.domain

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   name      String Domain name.
   id        String Domain ID.
   ========= ====== ============

-  .. _iam_02_0003__li094919112407:

   token.user.OS-FEDERATION

   +---------------------------------------------------------+------------------+--------------------------------+
   | Parameter                                               | Type             | Description                    |
   +=========================================================+==================+================================+
   | :ref:`groups <iam_02_0003__li1314311674010>`            | Array of objects | User group information.        |
   +---------------------------------------------------------+------------------+--------------------------------+
   | :ref:`identity_provider <iam_02_0003__li1414416162403>` | Object           | Identity provider information. |
   +---------------------------------------------------------+------------------+--------------------------------+
   | :ref:`protocol <iam_02_0003__li1892131644013>`          | Object           | Protocol information.          |
   +---------------------------------------------------------+------------------+--------------------------------+

-  .. _iam_02_0003__li1314311674010:

   token.user.OS-FEDERATION.groups

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   id        String User group ID.
   name      String User group name.
   ========= ====== ================

-  .. _iam_02_0003__li1414416162403:

   token.user.OS-FEDERATION.identity_provider

   ========= ====== =====================
   Parameter Type   Description
   ========= ====== =====================
   id        String Identity provider ID.
   ========= ====== =====================

-  .. _iam_02_0003__li1892131644013:

   token.user.OS-FEDERATION.protocol

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   id        String Protocol ID.
   ========= ====== ============

-  Example response

   .. code-block::

      {
          "token": {
              "expires_at": "2018-03-13T03:00:01.168000Z",
              "methods": ["mapped"],
              "issued_at": "2018-03-12T03:00:01.168000Z",
              "user": {
                  "OS-FEDERATION": {
                      "identity_provider": {
                          "id": "test_local_idp"
                      },
                      "protocol": {
                          "id": "saml"
                      },
                      "groups": [{
                          "name": "admin",
                          "id": "45a8c8f1894444e9a016af065e152b91"
                      }]
                  },
                  "domain": {
                      "name": "hansheng",
                      "id": "c0e20cc993a24ad4aa3251661ef37c87"
                  },
                  "name": "FederationUser",
                  "id": "QNSzD0bycqUXE4hiRNfyFcWfoOs8z6gT"
              }
          }
      }

Status Code
-----------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 201         | The request is successful, and a token is returned.                            |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
