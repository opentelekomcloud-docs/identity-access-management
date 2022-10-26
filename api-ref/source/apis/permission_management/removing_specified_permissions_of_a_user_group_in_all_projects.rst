:original_name: iam_10_0013.html

.. _iam_10_0013:

Removing Specified Permissions of a User Group in All Projects
==============================================================

Function
--------

This API is provided for the administrator to remove the specified permissions of a user group in all projects.

URI
---

DELETE /v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/{role_id}/inherited_to_projects

.. table:: **Table 1** URI parameters

   +-----------+-----------+--------+---------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                       |
   +===========+===========+========+===================================================+
   | domain_id | Yes       | String | ID of the domain to which the user group belongs. |
   +-----------+-----------+--------+---------------------------------------------------+
   | group_id  | Yes       | String | User group ID.                                    |
   +-----------+-----------+--------+---------------------------------------------------+
   | role_id   | Yes       | String | Permission ID.                                    |
   +-----------+-----------+--------+---------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                       |
   +==============+===========+========+===================================================================+
   | X-Auth-token | Yes       | String | Token with **Security Administrator** or **op_auth** permissions. |
   +--------------+-----------+--------+-------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://sample.domain.com/v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/{role_id}/inherited_to_projects

Example Response
----------------

None

Status Codes
------------

=========== ==================================================
Status Code Description
=========== ==================================================
204         The request is successful.
401         Authentication failed.
403         You do not have permission to perform this action.
404         The requested resource cannot be found.
500         Internal server error.
=========== ==================================================
