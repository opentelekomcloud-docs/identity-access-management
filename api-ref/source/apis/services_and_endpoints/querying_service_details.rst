:original_name: en-us_topic_0067148045.html

.. _en-us_topic_0067148045:

Querying Service Details
========================

Function
--------

This API is used to query service details.

URI
---

-  URI format

   GET /v3/services/{service_id}

-  URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   service_id Yes       String Service ID.
   ========== ========= ====== ===========

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

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/services/5a4ed456d228428c800ed2b67b4363a7

Response Parameters
-------------------

Example response (successful response)

.. code-block::

   {
       "service": {
           "enabled": true,
           "type": "compute",
           "name": "nova",
           "links": {
               "self": "sample.domain.com/v3/services/5a4ed456d228428c800ed2b67b4363a7"
           },
           "id": "5a4ed456d228428c800ed2b67b4363a7"
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
