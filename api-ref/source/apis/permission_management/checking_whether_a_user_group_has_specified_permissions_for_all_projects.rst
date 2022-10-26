:original_name: iam_10_0012.html

.. _iam_10_0012:

Checking Whether a User Group Has Specified Permissions for All Projects
========================================================================

Function
--------

This API is provided for the administrator to check whether a user group has specified permissions for all projects.

URI
---

HEAD /v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/{role_id}/inherited_to_projects

.. table:: **Table 1** URI parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                               |
   +===========+===========+========+===========================================================================================================================================================================+
   | domain_id | Yes       | String | Domain ID. For details about how to obtain the ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`.              |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id  | Yes       | String | User group ID. For details about how to obtain a user group ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | role_id   | Yes       | String | Permission ID. For details about how to obtain a permission ID, see :ref:`Querying a Role List <en-us_topic_0057845591>`.                                                 |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   HEAD https://sample.domain.com/v3/OS-INHERIT/domains/{domain_id}/groups/{group_id}/roles/{role_id}/inherited_to_projects

Example Response
----------------

None

Status Codes
------------

=========== =============================================
Status Code Description
=========== =============================================
204         The request is successful.
401         Authentication failed.
403         Access denied.
404         The server could not find the requested page.
=========== =============================================

Error Codes
-----------

For details, see :ref:`Error Codes <iam_02_0006>`.
