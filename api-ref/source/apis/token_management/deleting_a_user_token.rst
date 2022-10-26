:original_name: iam_02_0063.html

.. _iam_02_0063:

Deleting a User Token
=====================

Function
--------

This API is used to delete a token no matter whether the token has expired or not.

URI
---

DELETE /v3/auth/tokens

Request Parameters
------------------

-  Parameters in the request header

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | Obtained token.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  To delete your own token, specify your token. There are no special requirements on the permissions that your token must have.         |
   |                 |                 |                 | -  To delete the token of another user under the same domain, use a token that has permissions of the **Security Administrator** policy. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Subject-Token | Yes             | String          | Token to be deleted.                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H "X-Subject-Token:$token" -X DELETE https://sample.domain.com/v3/auth/tokens

Response Parameters
-------------------

None

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
204         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
503         Service unavailable.
=========== =========================================
