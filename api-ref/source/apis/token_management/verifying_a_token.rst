:original_name: en-us_topic_0057845586.html

.. _en-us_topic_0057845586:

Verifying a Token
=================

Function
--------

This API can be used by the administrator to verify the token of a user or used by a user to verify their token. The administrator can only verify the token of a user created using the account. If the verified token is valid, **200** is displayed.

URI
---

HEAD /v3/auth/tokens

Request Parameters
------------------

.. table:: **Table 1** Parameters in the request header

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | -  To verify your own token, specify your token. There are no special requirements on the permissions that your token must have.         |
   |                 |                 |                 | -  To verify the token of another user under the same domain, use a token that has permissions of the **Security Administrator** policy. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Subject-Token | Yes             | String          | Token to be verified.                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block::

   curl -i -k -H "X-Auth-Token:$token" -H "X-Subject-Token:$token" -X HEAD https://sample.domain.com/v3/auth/tokens

Example Response
----------------

None

Status Codes
------------

=========== =======================================
Status Code Description
=========== =======================================
200         The request is successful.
401         Authentication failed.
404         The requested resource cannot be found.
500         The system is abnormal.
=========== =======================================
