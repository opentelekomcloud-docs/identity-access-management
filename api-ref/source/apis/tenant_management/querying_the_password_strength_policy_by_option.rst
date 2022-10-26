:original_name: iam_02_0113.html

.. _iam_02_0113:

Querying the Password Strength Policy by Option
===============================================

Function
--------

This API is used to query the password strength policy by **option**. The option can be the regular expression and description of the password strength policy.

URI
---

-  URI format

   GET /v3/domains/{domain_id}/config/security_compliance/{option}

-  URI parameters

   +-----------+-----------+--------+----------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                      |
   +===========+===========+========+==================================================================================+
   | domain_id | Yes       | String | ID of the domain whose password strength policy is to be queried.                |
   +-----------+-----------+--------+----------------------------------------------------------------------------------+
   | option    | Yes       | String | Query option, which can be **password_regex** or **password_regex_description**. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------+

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated user token.                             |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/domains/{domain_id}/config/security_compliance/password_regex

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ==== =====================================
   Parameter Mandatory Type Description
   ========= ========= ==== =====================================
   config    Yes       JSON Password strength policy of a domain.
   ========= ========= ==== =====================================

-  Description for the config format

   +----------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory | Type   | Description                                                                                             |
   +============================+===========+========+=========================================================================================================+
   | password_regex             | No        | String | Regular expression of the password strength policy (When **option** is set to **password_regex**).      |
   +----------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | password_regex_description | No        | String | Description of the password strength policy (When **option** is set to **password_regex_description**). |
   +----------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      When option is set to password_regex:
      {
        "config": {
          "password_regex": "^(?=.*\\d)(?=.*[a-zA-Z]).{7,}$"
        }
      }
      When option is set to password_regex_description:
      {
        "config": {
          "password_regex_description": "Passwords must contain at least 1 letter, 1 digit, and be a minimum length of 7 characters."
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
