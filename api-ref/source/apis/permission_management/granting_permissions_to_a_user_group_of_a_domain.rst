:original_name: en-us_topic_0057845623.html

.. _en-us_topic_0057845623:

Granting Permissions to a User Group of a Domain
================================================

Function
--------

This API is used to grant permissions to a user group of a domain. A role is a set of permissions and represents a group of actions.

URI
---

-  URI format

   PUT /v3/domains/{domain_id}/groups/{group_id}/roles/{role_id}

-  URI parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================================================================================================================================================================+
   | domain_id       | Yes             | String          | ID of the domain to which a user group belongs. For details about how to obtain the domain ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`.                                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String          | ID of a user group. For details about how to obtain the group ID, see :ref:`Obtaining User, Account, User Group, Project, and Agency Information <en-us_topic_0057845624>`.                                                                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | role_id         | Yes             | String          | ID of a role. For details about how to obtain the role ID, see :ref:`Querying a Role List <en-us_topic_0057845591>`.                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |    To assign a custom policy that contains OBS operations to a user group, create two custom policies with the scope being set to global services and region-specific projects respectively and other parameters being the same, and then attach the two policies to the user group. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X PUT https://sample.domain.com/v3/domains/d54061ebcb5145dd814f8eb3fe9b7ac0/groups/47d79cabc2cf4c35b13493d919a5bb3d/roles/e62d9ba0d6a544cd878d9e8a4663f6e2

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
