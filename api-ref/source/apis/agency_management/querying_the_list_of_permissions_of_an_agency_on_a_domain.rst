:original_name: en-us_topic_0079578166.html

.. _en-us_topic_0079578166:

Querying the List of Permissions of an Agency on a Domain
=========================================================

Function
--------

This API is used to query the list of permissions of an agency on a domain.

URI
---

-  URI format

   GET /v3.0/OS-AGENCY/domains/{domain_id}/agencies/{agency_id}/roles

-  URI parameters

   ========= ========= ====== =========================
   Parameter Mandatory Type   Description
   ========= ========= ====== =========================
   domain_id Yes       String ID of the current domain.
   agency_id Yes       String ID of an agency.
   ========= ========= ====== =========================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.               |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3.0/OS-AGENCY/domains/b32d99a7778d4fd9aa5bc616c3dc4e5f/agencies/37f90258b820472bbc8a0f4f0bfd720d/roles

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ===== ==============
   Parameter Mandatory Type  Description
   ========= ========= ===== ==============
   roles     Yes       Array List of roles.
   ========= ========= ===== ==============

-  Description for the role format

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | catalog         | No              | String          | Directory where a role locates.                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | display_name    | No              | String          | Displayed name of a role.                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | name            | Yes             | String          | Name of a role.                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | policy          | No              | Dict            | Policy of a role.                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | domain_id       | Yes             | String          | ID of the domain to which a role belongs.                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | type            | Yes             | String          | Display mode of a role.                                               |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  **AX**: A role is displayed at the domain layer.                   |
   |                 |                 |                 | -  **XA**: A role is displayed at the project layer.                  |
   |                 |                 |                 | -  **AA**: A role is displayed at both the domain and project layers. |
   |                 |                 |                 | -  **XX**: A role is not displayed at the domain or project layer.    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | id              | Yes             | String          | ID of a role.                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | description     | No              | String          | Description of a role.                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

-  Example response (successful request)

   .. code-block::

      {
        "roles": [
          {
            "catalog": "BASE",
            "display_name": "Tenant Guest",
            "name": "readonly",
            "policy": {
              "Version": "1.0",
              "Statement": [
                {
                  "Action": [
                    "::Get",
                    "::List"
                  ],
                  "Effect": "Allow"
                },
                {
                  "Action": [
                    "identity:*"
                  ],
                  "Effect": "Deny"
                }
              ]
            },
            "domain_id": null,
            "type": "AA",
            "id": "b32d99a7778d4fd9aa5bc616c3dc4e5f",
            "description": "Tenant Guest"
          }
        ]
      }

-  Example response (request failed)

   .. code-block::

      {
        "error": {
          "message": "You are not authorized to perform the requested action: identity:list_domain_grants",
          "code": 403,
          "title": "Forbidden"
        }
      }

Status Codes
------------

=========== =======================================
Status Code Description
=========== =======================================
200         The request is successful.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =======================================
