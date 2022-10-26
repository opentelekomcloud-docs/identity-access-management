:original_name: en-us_topic_0057845571.html

.. _en-us_topic_0057845571:

Querying Permissions of a User Group Under a Domain
===================================================

Function
--------

This API is used to query the permissions of a user group under a domain. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   GET /v3/domains/{domain_id}/groups/{group_id}/roles

-  URI parameters

   ========= ========= ====== ==============
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============
   domain_id Yes       String Domain ID.
   group_id  Yes       String User group ID.
   ========= ========= ====== ==============

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/domains/d54061ebcb5145dd814f8eb3fe9b7ac0/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles

Response Parameters
-------------------

-  Parameters in the response body

   +-----------+-----------+-------+--------------------------------------------------------------+
   | Parameter | Mandatory | Type  | Description                                                  |
   +===========+===========+=======+==============================================================+
   | links     | Yes       | Dict  | Role resource link of a specified user group under a domain. |
   +-----------+-----------+-------+--------------------------------------------------------------+
   | roles     | Yes       | Array | Role of a specified user group under a domain.               |
   +-----------+-----------+-------+--------------------------------------------------------------+

-  Role parameter description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | id              | Yes             | String          | ID of a role of a specified user group under a domain.                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | links           | Yes             | Dict            | Role resource link.                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | name            | Yes             | String          | Name of a role.                                                       |
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
        "links": {
          "self": "https://sample.domain.com/v3/domains/d54061ebcb5145dd814f8eb3fe9b7ac0/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles",
          "previous": null,
          "next": null
        },
        "roles": [
          {
            "display_name": "Security Administrator",
            "description": "Security Administrator",
            "links": {
              "self": "https://sample.domain.com/v3/roles/005cf92cfd364105afaa5df2eec25012"
            },
            "domain_id": null,
            "name": "secu_admin",
            "type": "AX",
            "catalog": "BASE",
            "policy": {
              "Version": "1.0",
              "Statement": [
                {
                  "Action": [
                    "identity:*"
                  ],
                  "Effect": "Allow"
                }
              ]
            },
            "id": "005cf92cfd364105afaa5df2eec25012"
          },
          {
            "display_name": "Agent Operator",
            "description": "Agent Operator",
            "links": {
              "self": "https://sample.domain.com/v3/roles/d160d30477c642a486ad10e3b4d9820f"
            },
            "domain_id": null,
            "name": "te_agency",
            "type": "AX",
            "catalog": "IAM",
            "policy": {
              "Version": "1.0",
              "Statement": [
                {
                  "Action": [
                    "identity:assume role"
                  ],
                  "Effect": "Allow"
                }
              ]
            },
            "id": "d160d30477c642a486ad10e3b4d9820f"
          }
        ]
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
