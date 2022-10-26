:original_name: en-us_topic_0057845600.html

.. _en-us_topic_0057845600:

Updating a User Group
=====================

Function
--------

This API is used to update user group information.

URI
---

-  URI format

   PATCH /v3/groups/{group_id}

-  URI parameters

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

-  Parameters in the request body

   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                       |
   +=============+===========+========+===================================================================================+
   | group       | Yes       | Object | Request body of a group.                                                          |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | description | No        | String | Description for a user group. The length is less than or equal to 255 characters. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | domain_id   | No        | String | ID of the domain to which a user group belongs.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | name        | No        | String | Name of a user group. The length is less than or equal to 64 characters.          |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X PATCH -d'{"group": {"description": "Contract developers 2016"}}' https://sample.domain.com/v3/groups/aaec2abd4eba430fbf61541ffde76650

Response Parameters
-------------------

-  Parameters in the response body

   +-------------+-----------+--------+-------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                     |
   +=============+===========+========+=================================================+
   | group       | Yes       | Dict   | Response body of a user group.                  |
   +-------------+-----------+--------+-------------------------------------------------+
   | description | Yes       | String | Description for a user group.                   |
   +-------------+-----------+--------+-------------------------------------------------+
   | domain_id   | Yes       | String | ID of the domain to which a user group belongs. |
   +-------------+-----------+--------+-------------------------------------------------+
   | id          | Yes       | String | ID of a user group.                             |
   +-------------+-----------+--------+-------------------------------------------------+
   | links       | Yes       | Dict   | User group resource link.                       |
   +-------------+-----------+--------+-------------------------------------------------+
   | name        | Yes       | String | Name of a user group.                           |
   +-------------+-----------+--------+-------------------------------------------------+

-  Example response

   .. code-block::

      {
        "group": {
          "domain_id": "d54061ebcb5145dd814f8eb3fe9b7ac0",
          "description": "Contract developers 2016",
          "id": "aaec2abd4eba430fbf61541ffde76650",
          "links": {
            "self": "https://sample.domain.com/v3/groups/aaec2abd4eba430fbf61541ffde76650"
          },
          "name": "jixiang1"
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
409         A resource conflict occurs.
501         The API is not implemented.
=========== =========================================
