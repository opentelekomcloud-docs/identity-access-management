:original_name: en-us_topic_0057845597.html

.. _en-us_topic_0057845597:

Granting Permissions to a User Group Corresponding to a Project
===============================================================

Function
--------

This API is used to grant permissions to a user group corresponding to a project. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   PUT /v3/projects/{project_id}/groups/{group_id}/roles/{role_id}

-  URI parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`.                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Ensure that the project is the IAM project that IAM users in the group will be authorized to access and use.                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |    To assign a custom policy that contains OBS operations to a user group, use the API described in :ref:`Querying Project Information Based on the Specified Criteria <en-us_topic_0057845625>` to obtain the ID of the **MOS** project, and attach the custom policy to the user group in this project. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String          | ID of a user group. For details about how to obtain the group ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`.                                                                                                                               |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | role_id         | Yes             | String          | ID of a role. For details about how to obtain the role ID, see :ref:`Querying a Role List <en-us_topic_0057845591>`.                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X PUT https://sample.domain.com/v3/projects/073bbf60da374853841cf6624c94de4b/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles/e62d9ba0d6a544cd878d9e8a4663f6e2

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
409         A resource conflict occurs.
=========== =========================================
