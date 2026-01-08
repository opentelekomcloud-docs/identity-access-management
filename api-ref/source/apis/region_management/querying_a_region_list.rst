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

   ========= ========= ==== =====================
   Parameter Mandatory Type Description
   ========= ========= ==== =====================
   links     Yes       Dict Region resource link.
   regions   Yes       List Region list.
   ========= ========= ==== =====================

-  Description for the regions format

   ================ ========= ====== =============================
   Parameter        Mandatory Type   Description
   ================ ========= ====== =============================
   description      Yes       String Region description.
   parent_region_id Yes       String Parent region ID of a region.
   id               Yes       String Region ID.
   locales          Yes       Dict   Region name.
   type             No        String Region type.
   links            Yes       Dict   Region resource link.
   ================ ========= ====== =============================

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
