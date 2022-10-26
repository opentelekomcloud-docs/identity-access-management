:original_name: iam_02_0007.html

.. _iam_02_0007:

Querying the Password Strength Policy
=====================================

Function
--------

This API is used to query the password strength policy, including its regular expression and description.

URI
---

-  URI format

   GET /v3/domains/{domain_id}/config/security_compliance

-  URI parameters

   ========= ========= ====== ========================
   Parameter Mandatory Type   Description
   ========= ========= ====== ========================
   domain_id Yes       String Domain ID to be queried.
   ========= ========= ====== ========================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token of a user.                        |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/domains/{domain_id}/config/security_compliance

Response Parameters
-------------------

-  Parameters in the response body

   +----------------------------+-----------+--------+-----------------------------------------------------+
   | Parameter                  | Mandatory | Type   | Description                                         |
   +============================+===========+========+=====================================================+
   | security_compliance        | Yes       | JSON   | Password strength policy.                           |
   +----------------------------+-----------+--------+-----------------------------------------------------+
   | password_regex             | Yes       | String | Regular expression of the password strength policy. |
   +----------------------------+-----------+--------+-----------------------------------------------------+
   | password_regex_description | Yes       | String | Description of the password strength policy.        |
   +----------------------------+-----------+--------+-----------------------------------------------------+

-  Example response

   .. code-block::

      {
        "config": {
          "security_compliance": {
            "password_regex": "^(?=.*\\d)(?=.*[a-zA-Z]).{7,}$",
            "password_regex_description": "Passwords must contain at least 1 letter, 1 digit, and be a minimum length of 7 characters."
          }
        }
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 200         | The request is successful.                                                     |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                        |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
