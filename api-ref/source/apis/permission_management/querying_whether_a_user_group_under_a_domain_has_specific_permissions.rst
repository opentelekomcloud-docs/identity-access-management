:original_name: en-us_topic_0057845632.html

.. _en-us_topic_0057845632:

Querying Whether a User Group Under a Domain Has Specific Permissions
=====================================================================

Function
--------

This API is used to query whether a specified user group under a domain has specific permissions. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   HEAD /v3/domains/{domain_id}/groups/{group_id}/roles/{role_id}

-  URI parameters

   +-----------+-----------+--------+-------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                     |
   +===========+===========+========+=================================================+
   | domain_id | Yes       | String | ID of the domain to which a user group belongs. |
   +-----------+-----------+--------+-------------------------------------------------+
   | group_id  | Yes       | String | ID of a user group.                             |
   +-----------+-----------+--------+-------------------------------------------------+
   | role_id   | Yes       | String | ID of a role.                                   |
   +-----------+-----------+--------+-------------------------------------------------+

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X HEAD https://10.22.44.158:31943/v3/domains/d54061ebcb5145dd814f8eb3fe9b7ac0/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles/e62d9ba0d6a544cd878d9e8a4663f6e2

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
=========== =========================================
