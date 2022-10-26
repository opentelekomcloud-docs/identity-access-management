:original_name: en-us_topic_0079466135.html

.. _en-us_topic_0079466135:

Querying Information and Status of a Specified Project
======================================================

Function
--------

This API is used to query details about a specified project, including the project status.

URI
---

-  URI format

   GET /v3-ext/projects/{project_id}

-  URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -X "X-Auth-Token:$token" -X GET https://sample.domain.com/v3-ext/projects/5c9f5525d9d24c5bbf91e74d86772029

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ====== ====================
   Parameter Mandatory Type   Description
   ========= ========= ====== ====================
   project   Yes       Object Project information.
   ========= ========= ====== ====================

-  Description for the project format

   +----------------+-----------+---------+---------------------------------------------------------+
   | Parameter      | Mandatory | Type    | Description                                             |
   +================+===========+=========+=========================================================+
   | description    | Yes       | String  | Project description.                                    |
   +----------------+-----------+---------+---------------------------------------------------------+
   | id             | Yes       | String  | Project ID.                                             |
   +----------------+-----------+---------+---------------------------------------------------------+
   | domain_id      | Yes       | String  | ID of the domain that a project belongs to.             |
   +----------------+-----------+---------+---------------------------------------------------------+
   | name           | Yes       | String  | Project name.                                           |
   +----------------+-----------+---------+---------------------------------------------------------+
   | is_domain      | Yes       | Boolean | Indicates whether the user calling the API is a tenant. |
   +----------------+-----------+---------+---------------------------------------------------------+
   | enabled        | Yes       | Boolean | Whether a project is available.                         |
   +----------------+-----------+---------+---------------------------------------------------------+
   | parent_id      | Yes       | String  | Parent ID of a project.                                 |
   +----------------+-----------+---------+---------------------------------------------------------+
   | status         | Yes       | String  | Project status.                                         |
   +----------------+-----------+---------+---------------------------------------------------------+
   | suspended_time | No        | String  | Time when a project is suspended.                       |
   +----------------+-----------+---------+---------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "project": {
          "is_domain": false,
          "description": "",
          "enabled": true,
          "id": "ee65ca70d3cf43aaa1ea6492ce15f289",
          "parent_id": "9041929bcc6e4bfe85add4e7b96ffdd7",
          "domain_id": "398998b5392f4150ad48fe456d6de4f1",
          "name": "{region_id}_test1",
          "status": "suspended",
          "suspended_time": "2017-08-17T02:50:23.000000"
        }
      }

**Status Codes**
----------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
503         Service unavailable.
=========== =========================================
