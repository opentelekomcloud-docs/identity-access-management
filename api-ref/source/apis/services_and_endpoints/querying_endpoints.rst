:original_name: en-us_topic_0057845562.html

.. _en-us_topic_0057845562:

Querying Endpoints
==================

Function
--------

This API is used to query the list of terminal addresses and provides a service access entry.

URI
---

-  URI format

   GET /v3/endpoints{?interface, service_id}

-  URI parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                  |
   +=================+=================+=================+==============================================================================+
   | interface       | No              | String          | Plane to which an endpoint belongs.                                          |
   |                 |                 |                 |                                                                              |
   |                 |                 |                 | The value can be **public**, **internal**, or **admin**.                     |
   |                 |                 |                 |                                                                              |
   |                 |                 |                 | -  **public**: Users can view it on the public network interface.            |
   |                 |                 |                 | -  **internal**: Users can view it on the internal network interface.        |
   |                 |                 |                 | -  **admin**: The administrator can view it on the secure network interface. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | service_id      | No              | String          | Service ID.                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+

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

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/endpoints?interface=public&service_id=43cbe5e77aaf4665bbb962062dc1fc9d

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ==== =======================
   Parameter Mandatory Type Description
   ========= ========= ==== =======================
   links     Yes       dict Endpoint resource link.
   endpoints Yes       list List of endpoints.
   ========= ========= ==== =======================

-  Description for the endpoints format

   +------------+-----------+---------+-------------------------------------------------+
   | Parameter  | Mandatory | Type    | Description                                     |
   +============+===========+=========+=================================================+
   | id         | Yes       | String  | Endpoint ID.                                    |
   +------------+-----------+---------+-------------------------------------------------+
   | url        | Yes       | String  | Terminal endpoint URL.                          |
   +------------+-----------+---------+-------------------------------------------------+
   | region     | Yes       | String  | Region to which an endpoint belongs.            |
   +------------+-----------+---------+-------------------------------------------------+
   | region_id  | Yes       | String  | ID of the region to which an endpoint belongs.  |
   +------------+-----------+---------+-------------------------------------------------+
   | enabled    | Yes       | Boolean | Whether an endpoint is available.               |
   +------------+-----------+---------+-------------------------------------------------+
   | interface  | Yes       | String  | Plane to which an endpoint belongs.             |
   +------------+-----------+---------+-------------------------------------------------+
   | service_id | Yes       | String  | ID of the service to which an endpoint belongs. |
   +------------+-----------+---------+-------------------------------------------------+
   | links      | Yes       | dict    | Endpoint resource link.                         |
   +------------+-----------+---------+-------------------------------------------------+

-  Example response (successful request)

   .. code-block::

      {
          "endpoints": [
              {
                  "region_id": null,
                  "links": {
                      "self": "https://sample.domain.com/v3/endpoints/162277d696f54cf592f19b569f85d158"
                  },
                  "url": "https://sample.domain.com/v3",
                  "region": null,
                  "enabled": true,
                  "interface": "public",
                  "service_id": "053d21d488d1463c818132d9d08fb617",
                  "id": "162277d696f54cf592f19b569f85d158"
              }
          ],
          "links": {
              "self": "https://sample.domain.com/v3/endpoints?service_id=053d21d488d1463c818132d9d08fb617&interface=public",
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
