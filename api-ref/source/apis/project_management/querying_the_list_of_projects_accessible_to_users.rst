:original_name: en-us_topic_0057845558.html

.. _en-us_topic_0057845558:

Querying the List of Projects Accessible to Users
=================================================

Function
--------

This API is used to query the list of projects accessible to users.

URI
---

GET /v3/auth/projects

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token of the user.                      |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET /v3/auth/projects

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ========= ======================
   Parameter Mandatory Type      Description
   ========= ========= ========= ======================
   projects  Yes       JSONArray List of projects.
   links     Yes       Object    Project resource link.
   ========= ========= ========= ======================

-  Description for the project format

   +-------------+-----------+---------+---------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                             |
   +=============+===========+=========+=========================================================+
   | description | Yes       | String  | Project description.                                    |
   +-------------+-----------+---------+---------------------------------------------------------+
   | id          | Yes       | String  | ID of a project.                                        |
   +-------------+-----------+---------+---------------------------------------------------------+
   | domain_id   | Yes       | String  | ID of the domain where a project is located.            |
   +-------------+-----------+---------+---------------------------------------------------------+
   | name        | Yes       | String  | Project name.                                           |
   +-------------+-----------+---------+---------------------------------------------------------+
   | links       | Yes       | Object  | Project resource link.                                  |
   +-------------+-----------+---------+---------------------------------------------------------+
   | is_domain   | Yes       | Boolean | Indicates whether the user calling the API is a tenant. |
   +-------------+-----------+---------+---------------------------------------------------------+
   | enabled     | Yes       | Boolean | Whether a project is available.                         |
   +-------------+-----------+---------+---------------------------------------------------------+
   | parent_id   | Yes       | String  | Parent ID of the project.                               |
   +-------------+-----------+---------+---------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "links": {
          "self": "https://sample.domain.com/v3/auth/projects",
          "previous": null,
          "next": null
        },
        "projects": [
          {
            "is_domain": false,
            "description": "",
            "links": {
              "self": "https://sample.domain.com/v3/projects/9041929bcc6e4bfe85add4e7b96ffdd7"
            },
            "enabled": true,
            "id": "9041929bcc6e4bfe85add4e7b96ffdd7",
            "parent_id": "398998b5392f4150ad48fe456d6de4f1",
            "domain_id": "398998b5392f4150ad48fe456d6de4f1",
            "name": "region"
          },
          {
            "is_domain": false,
            "description": "",
            "links": {
              "self": "https://sample.domain.com/v3/projects/ee65ca70d3cf43aaa1ea6492ce15f289"
            },
            "enabled": true,
            "id": "ee65ca70d3cf43aaa1ea6492ce15f289",
            "parent_id": "398998b5392f4150ad48fe456d6de4f1",
            "domain_id": "398998b5392f4150ad48fe456d6de4f1",
            "name": "{project_name}"
          }
        ]
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
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
