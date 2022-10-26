:original_name: en-us_topic_0067148046.html

.. _en-us_topic_0067148046:

Querying Endpoint Details
=========================

Function
--------

This API is used to query endpoint details.

URI
---

-  URI format

   GET /v3/endpoints/{endpoint_id}

-  URI parameters

   =========== ========= ====== ============
   Parameter   Mandatory Type   Description
   =========== ========= ====== ============
   endpoint_id Yes       String Endpoint ID.
   =========== ========= ====== ============

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token.                                  |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/endpoints/62ea3602f8ee42b1825956473f5295a8

Response Parameters
-------------------

Example response (successful request)

.. code-block::

   {
       "endpoint": {
           "region_id": "region_id",
           "links": {
               "self": "https://sample.domain.com/v3/endpoints/62ea3602f8ee42b1825956473f5295a8"
           },
           "url": "https://sample.domain.com/v2/",
           "region": "region_name",
           "enabled": true,
           "interface": "public",
           "service_id": "5a4ed456d228428c800ed2b67b4363a7",
           "id": "62ea3602f8ee42b1825956473f5295a8"
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
