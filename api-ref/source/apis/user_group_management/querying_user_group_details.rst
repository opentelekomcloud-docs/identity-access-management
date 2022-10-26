:original_name: en-us_topic_0057845618.html

.. _en-us_topic_0057845618:

Querying User Group Details
===========================

Function
--------

This API is used to query detailed information about a user group.

URI
---

-  URI format

   GET /v3/groups/{group_id}

-  Query parameters

   ========= ========= ====== ===================
   Parameter Mandatory Type   Description
   ========= ========= ====== ===================
   group_id  Yes       String ID of a user group.
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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/groups/ab9f261180d746ef8624beb5ae39b5aa

Response Parameters
-------------------

-  Parameters in the response body

   +-------------+-----------+-------------+-------------------------------------------------+
   | Parameter   | Mandatory | Type        | Description                                     |
   +=============+===========+=============+=================================================+
   | group       | Yes       | JSON object | Response body of a user group.                  |
   +-------------+-----------+-------------+-------------------------------------------------+
   | description | Yes       | String      | Description for a user group.                   |
   +-------------+-----------+-------------+-------------------------------------------------+
   | domain_id   | Yes       | String      | ID of the domain to which a user group belongs. |
   +-------------+-----------+-------------+-------------------------------------------------+
   | id          | Yes       | String      | ID of a user group.                             |
   +-------------+-----------+-------------+-------------------------------------------------+
   | links       | Yes       | JSON object | Links to a user group.                          |
   +-------------+-----------+-------------+-------------------------------------------------+
   | name        | Yes       | String      | Name of a user group.                           |
   +-------------+-----------+-------------+-------------------------------------------------+
   | create_time | Yes       | Long        | Time when a user group is created.              |
   +-------------+-----------+-------------+-------------------------------------------------+

-  Example response

   .. code-block::

      {
          "group":{
              "domain_id":"d54061ebcb5145dd814f8eb3fe9b7ac0",
              "description":"Contract developers",
              "id":"ab9f261180d746ef8624beb5ae39b5aa",
              "links":{
                  "self":"https://sample.domain.com/v3/groups/ab9f261180d746ef8624beb5ae39b5aa"
              },
              "name":"abcdef",
              "create_time": 1494943784468
          }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
=========== =========================================
