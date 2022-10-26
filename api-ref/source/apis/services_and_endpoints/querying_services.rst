:original_name: en-us_topic_0057845587.html

.. _en-us_topic_0057845587:

Querying Services
=================

Function
--------

This API is used to query the service list.

URI
---

-  URI format

   GET /v3/services{?type}

-  URI parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                 |
   +=================+=================+=================+=============================================================================================+
   | type            | No              | String          | Service type.                                                                               |
   |                 |                 |                 |                                                                                             |
   |                 |                 |                 | The value can be **compute**, **ec2**, **identity**, **image**, **network**, or **volume**. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+

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

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/services?type=compute

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ==== ======================
   Parameter Mandatory Type Description
   ========= ========= ==== ======================
   links     Yes       Dict Service resource link.
   services  Yes       List A list of services.
   ========= ========= ==== ======================

-  Description for the services format

   =========== ========= ======= ===============================
   Parameter   Mandatory Type    Description
   =========== ========= ======= ===============================
   description No        String  Service description.
   enabled     Yes       Boolean Whether a service is available.
   id          Yes       String  Service ID.
   name        No        String  Service name.
   type        Yes       String  Service type.
   links       Yes       Dict    Service resource link.
   =========== ========= ======= ===============================

-  Example response (successful response)

   .. code-block::

      {
          "services": [
              {
                  "name": "compute5",
                  "links": {
                      "self": "https://sample.domain.com/v3/services/053d21d488d1463c818132d9d08fb617"
                  },
                  "enabled": true,
                  "type": "compute",
                  "id": "053d21d488d1463c818132d9d08fb617",
                  "description": "Compute service 5"
              },
              {
                  "name": "compute3",
                  "links": {
                      "self": "https://sample.domain.com/v3/services/c2474183dca7453bbd73123a0b78feae"
                  },
                  "enabled": true,
                  "type": "compute",
                  "id": "c2474183dca7453bbd73123a0b78feae",
                  "description": "Compute service 3"
              },
              {
                  "name": "compute2",
                  "links": {
                      "self": "https://sample.domain.com/v3/services/c7166694ebdd4616bd927737f7b12ca2"
                  },
                  "enabled": true,
                  "type": "compute",
                  "id": "c7166694ebdd4616bd927737f7b12ca2",
                  "description": "Compute service 2"
              }
          ],
          "links": {
              "self": "https://sample.domain.com/v3/services?type=compute",
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
