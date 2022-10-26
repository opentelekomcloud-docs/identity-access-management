:original_name: en-us_topic_0057845640.html

.. _en-us_topic_0057845640:

Querying Permissions of a User Group Corresponding to a Project
===============================================================

Function
--------

This API is used to query the permissions of a specified user group corresponding to a project. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   GET /v3/projects/{project_id}/groups/{group_id}/roles

-  URI parameters

   ========== ========= ====== ===================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================
   project_id Yes       String Project ID.
   group_id   Yes       String ID of a user group.
   ========== ========= ====== ===================

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/projects/073bbf60da374853841cf6624c94de4b/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ===== ===================
   Parameter Mandatory Type  Description
   ========= ========= ===== ===================
   links     Yes       Dict  Role resource link.
   roles     Yes       Array List of roles.
   ========= ========= ===== ===================

-  Role parameter description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | id              | Yes             | String          | ID of a role.                                                         |
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
              "self": " https://sample.domain.com/v3/projects/3a4cd4d559d8492bbe7bd355643f9763/groups/728da352c017480f80b5a96beb15f0e6/roles",
              "previous": null,
              "next": null
          },
          "roles": [
              {
                  "catalog": "BASE",
                  "display_name": "Guest",
                  "name": "readonly",
                  "links": {
                      "self": " https://sample.domain.com/v3/roles/13d132b7856945788f6df7eb3ed5c35e"
                  },
                  "policy": {
                      "Version": "1.0",
                      "Statement": [
                          {
                              "Action": [
                                  "*:*:Get*",
                                  "*:*:List*"
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
                  "id": "13d132b7856945788f6df7eb3ed5c35e",
                  "description": "Guest"
              },
              {
                  "catalog": "BASE",
                  "display_name": "Tenant Administrator",
                  "name": "te_admin",
                  "links": {
                      "self": " https://sample.domain.com/v3/roles/1def304b73f14e8eb8d1eb9bf8337ae6"
                  },
                  "policy": {
                      "Version": "1.0",
                      "Statement": [
                          {
                              "Action": [
                                  "*"
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
                  "id": "1def304b73f14e8eb8d1eb9bf8337ae6",
                  "description": "Tenant Administrator"
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
