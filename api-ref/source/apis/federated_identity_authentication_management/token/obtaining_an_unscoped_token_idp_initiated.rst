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
