:original_name: en-us_topic_0067148043.html

.. _en-us_topic_0067148043:

Querying a Region List
======================

Function
--------

This API is used to query a region list.

URI
---

GET /v3/regions

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================================+
   | Accept       | Yes       | String | Fill **application/json** in this field.                                                                                                              |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token. If the token does not contain the private region information, the system does not return the private region in the query result. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/regions

Response Parameters
-------------------

-  Parameters in the response body

   +-------------------------------------------------------+-----------+------------------+-----------------------+
   | Parameter                                             | Mandatory | Type             | Description           |
   +=======================================================+===========+==================+=======================+
   | :ref:`links <en-us_topic_0067148043__li13463758160>`  | Yes       | Object           | Region resource link. |
   +-------------------------------------------------------+-----------+------------------+-----------------------+
   | :ref:`regions <en-us_topic_0067148043__li2129719204>` | Yes       | Array of objects | Region list.          |
   +-------------------------------------------------------+-----------+------------------+-----------------------+

-  .. _en-us_topic_0067148043__li2129719204:

   regions

   +-------------------------------------------------------+--------+-------------------------------+
   | Parameter                                             | Type   | Description                   |
   +=======================================================+========+===============================+
   | description                                           | String | Region description.           |
   +-------------------------------------------------------+--------+-------------------------------+
   | parent_region_id                                      | String | Parent region ID of a region. |
   +-------------------------------------------------------+--------+-------------------------------+
   | id                                                    | String | Region ID.                    |
   +-------------------------------------------------------+--------+-------------------------------+
   | :ref:`locales <en-us_topic_0067148043__li6783209973>` | Object | Region name.                  |
   +-------------------------------------------------------+--------+-------------------------------+
   | type                                                  | String | Region type.                  |
   +-------------------------------------------------------+--------+-------------------------------+
   | :ref:`links <en-us_topic_0067148043__li11493001976>`  | Object | Region resource link.         |
   +-------------------------------------------------------+--------+-------------------------------+

-  .. _en-us_topic_0067148043__li13463758160:

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

-  .. _en-us_topic_0067148043__li11493001976:

   regions.links

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   self      String Resource link.
   ========= ====== ==============

-  .. _en-us_topic_0067148043__li6783209973:

   regions.locales

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   en-us     String Region name in English.
   pt-br     String Region name in Portuguese.
   es-us     String Region name in Spanish (Latin American).
   es-es     String Region name in Spanish (Spain).
   ========= ====== ========================================

-  Example response (successful response)

   .. code-block::

      {
          "regions": [
              {
                  "parent_region_id": null,
                  "description": "",
                  "links": {
                      "self": "None/v3/regions/1500365963661574434"
                  },
                  "type": "private",
                  "id": "1500365963661574434",
                  "locales": {

                      "en-us": "region_name2"
                  }
              },
              {
                  "parent_region_id": null,
                  "description": "",
                  "links": {
                      "self": "https://sample.domain.com/v3/regions/500017826026667755"
                  },
                  "type": "private",
                  "id": "500017826026667755",
                  "locales": {

                      "en-us": "region_name2"
                  }
              },
              {
                  "parent_region_id": null,
                  "description": "",
                  "links": {
                      "self": "https://sample.domain.com/v3/regions/region_name"
                  },
                  "type": "public",
                  "id": "test2",
                  "locales": {

                      "en-us": "region_name2"
                  }
              },
              {
                  "parent_region_id": null,
                  "links": {
                      "self": "https://sample.domain.com/v3/regions/test1112244"
                  },
                  "id": "test1112244",
                  "locales": {

                      "en-us": "testregion1"
                  },
                  "description": ""
              }
          ],
          "links": {
              "self": "https://sample.domain.com/v3/regions",
              "previous": null,
              "next": null
          }
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
