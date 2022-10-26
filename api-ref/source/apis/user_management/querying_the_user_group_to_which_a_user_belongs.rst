:original_name: en-us_topic_0057845554.html

.. _en-us_topic_0057845554:

Querying the User Group to Which a User Belongs
===============================================

Function
--------

This API is used to query the information about the user group to which a specified user belongs.

URI
---

-  URI format

   GET /v3/users/{user_id}/groups

-  URI parameters

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   user_id   Yes       String User ID.
   ========= ========= ====== ===========

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                            |
   +==============+===========+========+========================================================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.                                                  |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission or authenticated token of the user. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/users/43cbe5e77aaf4665bbb962062dc1fc9d/groups

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== =========================
   Parameter Mandatory Type        Description
   ========= ========= =========== =========================
   groups    Yes       JSONArray   List of a user group.
   links     Yes       JSON object User group resource link.
   ========= ========= =========== =========================

-  Description for the group format

   +-------------+-----------+-------------+-------------------------------------------------+
   | Parameter   | Mandatory | Type        | Description                                     |
   +=============+===========+=============+=================================================+
   | description | Yes       | String      | Description for a user group.                   |
   +-------------+-----------+-------------+-------------------------------------------------+
   | id          | Yes       | String      | User group ID.                                  |
   +-------------+-----------+-------------+-------------------------------------------------+
   | domain_id   | Yes       | String      | ID of the domain where a user group is located. |
   +-------------+-----------+-------------+-------------------------------------------------+
   | name        | Yes       | String      | User group name.                                |
   +-------------+-----------+-------------+-------------------------------------------------+
   | links       | Yes       | JSON object | User group resource link.                       |
   +-------------+-----------+-------------+-------------------------------------------------+
   | create_time | Yes       | Long        | Time when a user group is created.              |
   +-------------+-----------+-------------+-------------------------------------------------+

-  Example response

   .. code-block::

      {
          "links": {
              "self": "https://sample.domain.com/v3/users/f7cb4876e5174c0885433e280e831c43/groups",
              "previous": null,
              "next": null
          },
          "groups": [{
              "description": "User group that has the permission for all system operations",
              "links": {
                  "self": "https://sample.domain.com/v3/groups/e21c7a1e415c4604927948dc24750716"
              },
              "id": "e21c7a1e415c4604927948dc24750716",
              "create_time": 1472888495993,
              "domain_id": "88b16b6440684467b8825d7d96e154d8",
              "name": "admin"
          }]
      }

Status Codes
------------

+-------------+--------------------------------------------------------------------------------+
| Status Code | Description                                                                    |
+=============+================================================================================+
| 200         | The request is successful.                                                     |
+-------------+--------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                      |
+-------------+--------------------------------------------------------------------------------+
| 401         | Authentication failed.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 403         | Access denied.                                                                 |
+-------------+--------------------------------------------------------------------------------+
| 404         | The requested resource cannot be found.                                        |
+-------------+--------------------------------------------------------------------------------+
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
