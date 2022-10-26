:original_name: en-us_topic_0057845620.html

.. _en-us_topic_0057845620:

Querying Whether a User Group Corresponding to a Project Has Specific Permissions
=================================================================================

Function
--------

This API is used to query whether a user group corresponding to a project has specific permissions. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   HEAD /v3/projects/{project_id}/groups/{group_id}/roles/{role_id}

-  URI parameters

   ========== ========= ====== ===================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===================
   project_id Yes       String Project ID.
   group_id   Yes       String ID of a user group.
   role_id    Yes       String ID of a role.
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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X HEAD https://sample.domain.com/v3/projects/073bbf60da374853841cf6624c94de4b/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles/e62d9ba0d6a544cd878d9e8a4663f6e2

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
