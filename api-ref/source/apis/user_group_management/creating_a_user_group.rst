:original_name: en-us_topic_0057845650.html

.. _en-us_topic_0057845650:

Creating a User Group
=====================

Function
--------

This API is used to create a user group.

URI
---

POST /v3/groups

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

   +---------------------------------------------------------+-----------+--------+-------------------------+
   | Parameter                                               | Mandatory | Type   | Description             |
   +=========================================================+===========+========+=========================+
   | :ref:`group <en-us_topic_0057845650__li61927459103839>` | Yes       | Object | User group information. |
   +---------------------------------------------------------+-----------+--------+-------------------------+

-  .. _en-us_topic_0057845650__li61927459103839:

   group

   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                       |
   +=============+===========+========+===================================================================================+
   | description | No        | String | Description for a user group. The length is less than or equal to 255 characters. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | domain_id   | No        | String | ID of the domain to which a user group belongs.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+
   | name        | Yes       | String | Name of a user group. The length is less than or equal to 64 characters.          |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X POST -d'{"group": {"description": "Contract developers","domain_id": "d54061ebcb5145dd814f8eb3fe9b7ac0","name": "jixiang2"}}' https://sample.domain.com/v3/groups

Response Parameters
-------------------

-  Parameters in the response body

   +-------------------------------------------------------+-----------+--------+-------------------------+
   | Parameter                                             | Mandatory | Type   | Description             |
   +=======================================================+===========+========+=========================+
   | :ref:`group <en-us_topic_0057845650__li159009373324>` | Yes       | Object | User group information. |
   +-------------------------------------------------------+-----------+--------+-------------------------+

-  .. _en-us_topic_0057845650__li159009373324:

   group

   +--------------------------------------------------------+--------+---------------------------------------------------+
   | Parameter                                              | Type   | Description                                       |
   +========================================================+========+===================================================+
   | description                                            | String | User group description.                           |
   +--------------------------------------------------------+--------+---------------------------------------------------+
   | id                                                     | String | User group ID.                                    |
   +--------------------------------------------------------+--------+---------------------------------------------------+
   | domain_id                                              | String | ID of the domain to which the user group belongs. |
   +--------------------------------------------------------+--------+---------------------------------------------------+
   | name                                                   | String | User group name.                                  |
   +--------------------------------------------------------+--------+---------------------------------------------------+
   | :ref:`links <en-us_topic_0057845650__li1255593313512>` | Object | User group resource link.                         |
   +--------------------------------------------------------+--------+---------------------------------------------------+
   | create_time                                            | Long   | Time when the user group was created.             |
   +--------------------------------------------------------+--------+---------------------------------------------------+

-  .. _en-us_topic_0057845650__li1255593313512:

   group.links

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   self      String Resource link.
   ========= ====== ==============

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
              "create_time" : "1763639302"
          }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
201         The user group is successfully created.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
409         A resource conflict occurs.
=========== =========================================
