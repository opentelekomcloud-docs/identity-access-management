:original_name: iam_02_0519.html

.. _iam_02_0519:

Granting Permissions to a User Group for All Projects
=====================================================

Function
--------

This API is used to grant permissions to a user group for all projects.

URI
---

-  URI format

   PUT /v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/{role_id}/inherited_to_projects

-  URI parameters

   +-----------+-----------+--------+-------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                     |
   +===========+===========+========+=================================================+
   | domain_id | Yes       | String | ID of the domain to which a user group belongs. |
   +-----------+-----------+--------+-------------------------------------------------+
   | group_id  | Yes       | String | ID of a user group.                             |
   +-----------+-----------+--------+-------------------------------------------------+
   | role_id   | Yes       | String | User role ID.                                   |
   +-----------+-----------+--------+-------------------------------------------------+

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                      |
   +==============+===========+========+==================================================================================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.                                                                            |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | User token (of a specified domain ID) with **secu_admin** permissions or a token with **op_service** or **op_auth** permissions. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -X PUT https://sample.domain.com/v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/{role_id}/inherited_to_projects

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
=========== =========================================
