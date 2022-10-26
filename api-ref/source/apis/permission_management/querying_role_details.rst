:original_name: en-us_topic_0057845603.html

.. _en-us_topic_0057845603:

Querying Role Details
=====================

Function
--------

This API is used to query role details, including the permissions policies of a role. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   GET /v3/roles/{role_id}

-  URI parameters

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   role_id   Yes       String ID of a role.
   ========= ========= ====== =============

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/roles/19bb93eec4ca4f08aefdc02da76d8f3c

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ==== ====================
   Parameter Mandatory Type Description
   ========= ========= ==== ====================
   role      Yes       Dict Details of the role.
   ========= ========= ==== ====================

-  Description for the role format

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | domain_id       | Yes             | String          | ID of the domain to which a role belongs.                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | id              | Yes             | String          | ID of a role.                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | links           | Yes             | Dict            | Role resource link.                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | name            | Yes             | String          | Name of a role.                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | type            | Yes             | String          | Display mode of a role.                                               |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | -  **AX**: A role is displayed at the domain layer.                   |
   |                 |                 |                 | -  **XA**: A role is displayed at the project layer.                  |
   |                 |                 |                 | -  **AA**: A role is displayed at both the domain and project layers. |
   |                 |                 |                 | -  **XX**: A role is not displayed at the domain or project layer.    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | display_name    | No              | String          | Displayed name of a role.                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | catalog         | No              | String          | Directory where a role locates.                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | policy          | No              | Dict            | Policy of a role.                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | description     | No              | String          | Description of a role.                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "role": {
          "display_name": "Tanent Guest",
          "description": "Tanent Guest",
          "links": {
            "self": "https://sample.domain.com/v3/roles/19bb93eec4ca4f08aefdc02da76d8f3c"
          },
          "domain_id": null,
          "catalog": "BASE",
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
          "id": "19bb93eec4ca4f08aefdc02da76d8f3c",
          "type": "AA",
          "name": "readonly"
        }
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
=========== =========================================
