:original_name: en-us_topic_0057845602.html

.. _en-us_topic_0057845602:

Listing User Groups
===================

Function
--------

This API is used to query user group information.

URI
---

-  URI format

   GET /v3/groups{?domain_id,name}

-  Query parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                              |
   +===========+===========+========+==========================================================================+
   | domain_id | No        | String | ID of the domain where a user group is located.                          |
   +-----------+-----------+--------+--------------------------------------------------------------------------+
   | name      | No        | String | Name of a user group. The length is less than or equal to 64 characters. |
   +-----------+-----------+--------+--------------------------------------------------------------------------+

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/groups?domain_id=ac7197fd67a24dc5850972854729a762&name=group123

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== =========================
   Parameter Mandatory Type        Description
   ========= ========= =========== =========================
   links     Yes       JSON object User group resource link.
   groups    Yes       JSONArray   List of a user group.
   ========= ========= =========== =========================

-  Group parameter description

   +-------------+-----------+-------------+-------------------------------------------------+
   | Parameter   | Mandatory | Type        | Description                                     |
   +=============+===========+=============+=================================================+
   | description | Yes       | String      | Description for a user group.                   |
   +-------------+-----------+-------------+-------------------------------------------------+
   | domain_id   | Yes       | String      | ID of the domain to which a user group belongs. |
   +-------------+-----------+-------------+-------------------------------------------------+
   | id          | Yes       | String      | ID of a user group.                             |
   +-------------+-----------+-------------+-------------------------------------------------+
   | links       | Yes       | JSON object | User group resource link.                       |
   +-------------+-----------+-------------+-------------------------------------------------+
   | name        | Yes       | String      | Name of a user group.                           |
   +-------------+-----------+-------------+-------------------------------------------------+
   | create_time | Yes       | Long        | Time when a user group is created.              |
   +-------------+-----------+-------------+-------------------------------------------------+

-  Example response

   .. code-block::

      {
          "links": {
              "self": "https://sample.domain.com/v3/groups?domain_id=ac7197fd67a24dc5850972854729a762&name=group123",
              "previous": null,
              "next": null
          },
          "groups": [{
              "description": "",
              "links": {
                  "self": "https://sample.domain.com/v3/groups/ff74abaeabe34c278a4b7693c7f0dff7"
              },
              "id": "ff74abaeabe34c278a4b7693c7f0dff7",
              "create_time": 1482566254983,
              "domain_id": "ac7197fd67a24dc5850972854729a762",
              "name": "group123"
          }]
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
=========== =========================================
