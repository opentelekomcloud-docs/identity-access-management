:original_name: iam_02_0004.html

.. _iam_02_0004:

Querying the Service Catalog
============================

Function
--------

This API is used to query the service catalog corresponding to **X-Auth-Token** contained in the request.

URI
---

GET /v3/auth/catalog

Request Parameters
------------------

-  Parameters in the request header

   ============ ========= ====== ========================================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ========================================
   X-Auth-Token Yes       String Authenticated scoped token of a project.
   ============ ========= ====== ========================================

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'X-Auth-Token:$token' -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3/auth/catalog

Response Parameters
-------------------

Example response (successful request)

.. code-block::

   {
     "catalog": [
       {
         "endpoints": [
           {
             "region_id": null,
             "url": "https://sample.domain.com/v2/c972a59e958e407e89b0c6d8e522df3b",
             "region": null,
             "interface": "public",
             "id": "04f0ee42038447f0a9c7b407028fd7b9"
           }
         ],
         "type": "compute",
         "id": "eb884e9f64b44dd0ac73cdc55d817286",
         "name": "nova"
       }
     ],
     "links": {
       "self": "https://sample.domain.com/v3/auth/catalog"
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
