:original_name: iam_02_0042.html

.. _iam_02_0042:

Checking Whether an Agency Has Specified Permissions
====================================================

Function
--------

This API is provided for the administrator to check whether an agency has specified permissions.

URI
---

HEAD /v3.0/OS-INHERIT/domains/{domain_id}/agencies/{agency_id}/roles/{role_id}/inherited_to_projects

.. table:: **Table 1** URI parameters

   ========= ========= ====== ==================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==================================
   agency_id Yes       String Agency ID.
   domain_id Yes       String Domain ID of the delegating party.
   role_id   Yes       String Permission ID.
   ========= ========= ====== ==================================

Request Parameters
------------------

.. table:: **Table 2** Parameters in the request header

   +--------------+-----------+--------+----------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                        |
   +==============+===========+========+====================================================+
   | X-Auth-Token | Yes       | String | Token with **Security Administrator** permissions. |
   +--------------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block::

   HEAD https://sample.domain.com/v3.0/OS-INHERIT/domains/{domain_id}/agencies/{agency_id}/roles/{role_id}/inherited_to_projects

Example Response
----------------

None

Status Codes
------------

+-------------+------------------------------------------------------------------------+
| Status Code | Description                                                            |
+=============+========================================================================+
| 204         | The request is successful. (The agency has the specified permissions.) |
+-------------+------------------------------------------------------------------------+
| 401         | Authentication failed.                                                 |
+-------------+------------------------------------------------------------------------+
| 403         | Access denied.                                                         |
+-------------+------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                |
+-------------+------------------------------------------------------------------------+
| 500         | Internal server error.                                                 |
+-------------+------------------------------------------------------------------------+
