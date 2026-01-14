:original_name: en-us_topic_0057845625.html

.. _en-us_topic_0057845625:

Querying Project Information Based on the Specified Criteria
============================================================

Function
--------

This API is used to query project information based on the specified criteria.

URI
---

-  URI format

   GET /v3/projects

-  URI parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                             |
   +=================+=================+=================+=========================================================+
   | domain_id       | No              | String          | ID of an enterprise account to which a user belongs.    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | name            | No              | String          | Project name.                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | parent_id       | No              | String          | Parent project ID of a project.                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | enabled         | No              | Boolean         | Whether a project is available.                         |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | is_domain       | No              | Boolean         | Indicates whether the user calling the API is a tenant. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | page            | No              | Integer         | The page to be queried. The minimum value is **1**.     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+
   | per_page        | No              | Integer         | Number of data records on each page.                    |
   |                 |                 |                 |                                                         |
   |                 |                 |                 | Value range: 1-5000                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------+

   .. note::

      When querying required information by page, ensure that the query parameters **page** and **per_page** both exist.

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token of the target tenant.             |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -X "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/projects?domain_id=5c9f5525d9d24c5bbf91e74d86772029&name=region_name

Response Parameters
-------------------

-  Parameters in the response body

   +-----------------------------------------------------------------------------+-----------+--------+------------------------+
   | Parameter                                                                   | Mandatory | Type   | Description            |
   +=============================================================================+===========+========+========================+
   | :ref:`projects <en-us_topic_0057845625__l86920d09d4224a93a4379c10a51077f0>` | Yes       | List   | List of projects.      |
   +-----------------------------------------------------------------------------+-----------+--------+------------------------+
   | :ref:`links <en-us_topic_0057845625__li208411229192011>`                    | Yes       | Object | Project resource link. |
   +-----------------------------------------------------------------------------+-----------+--------+------------------------+

-  .. _en-us_topic_0057845625__l86920d09d4224a93a4379c10a51077f0:

   projects

   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | Parameter                                              | Mandatory | Type    | Description                                                                 |
   +========================================================+===========+=========+=============================================================================+
   | is_domain                                              | Yes       | Boolean | Indicates whether the user calling the API is a tenant.                     |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | description                                            | Yes       | String  | Project description.                                                        |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | :ref:`links <en-us_topic_0057845625__li1063810397233>` | Yes       | Object  | Project resource link.                                                      |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | enabled                                                | Yes       | Boolean | Whether a project is available.                                             |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | id                                                     | Yes       | String  | Project ID.                                                                 |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | parent_id                                              | Yes       | String  | Parent ID of the project.                                                   |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | domain_id                                              | Yes       | String  | ID of an enterprise account to which a project belongs.                     |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+
   | name                                                   | Yes       | String  | Project name. For example, eu-de and MOS. MOS is a built-in project of OBS. |
   +--------------------------------------------------------+-----------+---------+-----------------------------------------------------------------------------+

-  .. _en-us_topic_0057845625__li208411229192011:

   links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _en-us_topic_0057845625__li1063810397233:

   projects.links

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | self      | String | Resource link.                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | previous  | String | Previous resource link. If the previous resource link is unavailable, this parameter is set to **null**. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | next      | String | Next resource link. If the next resource link is unavailable, this parameter is set to **null**.         |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "links": {
          "self": "https://sample.domain.com/v3/projects?domain_id=c9f5525d9d24c5bbf91e74d86772029&name=region_name",
          "previous": null,
          "next": null
        },
        "projects": [
          {
            "is_domain": false,
            "description": "",
            "links": {
              "self": "https://sample.domain.com/v3/projects/e86737682ab64b2490c48f08bcc41914"
            },
            "enabled": true,
            "id": "e86737682ab64b2490c48f08bcc41914",
            "parent_id": "c9f5525d9d24c5bbf91e74d86772029",
            "domain_id": "c9f5525d9d24c5bbf91e74d86772029",
            "name": "region_name"
          }
        ]
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
500         Internal server error.
503         Service unavailable.
=========== =========================================
