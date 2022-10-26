:original_name: en-us_topic_0057845599.html

.. _en-us_topic_0057845599:

Querying Whether a User Belongs to a User Group
===============================================

Function
--------

This API is used to query whether a user belongs to a user group.

URI
---

-  URI format

   HEAD /v3/groups/{group_id}/users/{user_id}

-  URI parameters

   ========= ========= ====== ===================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================
   group_id  Yes       String ID of a user group.
   user_id   Yes       String ID of a user.
   ========= ========= ====== ===================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.               |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X HEAD https://sample.domain.com/v3/groups/00007111583e457389b0d4252643181b/users/edb66d2b656c43d0b67fb143d670bb3a

Response Parameters
-------------------

None

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 204         | The user belongs to this user group.                                                          |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                                     |
+-------------+-----------------------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                                        |
+-------------+-----------------------------------------------------------------------------------------------+
| 403         | Access denied.                                                                                |
+-------------+-----------------------------------------------------------------------------------------------+
| 404         | The server could not find the requested page, or the user does not belong to this user group. |
+-------------+-----------------------------------------------------------------------------------------------+
