:original_name: en-us_topic_0057845596.html

.. _en-us_topic_0057845596:

Querying the List of Domains Accessible to Federated Users
==========================================================

Function
--------

This API is used to query the list of domains accessible to federated users.

URI
---

GET /v3/OS-FEDERATION/domains

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                  |
   +==============+===========+========+==============================================================================================================+
   | X-Auth-Token | Yes       | String | Unscoped token. For details, see :ref:`Obtaining an Unscoped Token (SP Initiated) <en-us_topic_0057845629>`. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+

   .. note::

      The API described in :ref:`Querying the List of Domains Accessible to Users <en-us_topic_0057845574>` is recommended. This API returns the same response format as the API described in this section.

-  Example request

   .. code-block:: text

      GET /v3/OS-FEDERATION/domains

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ====== =====================
   Parameter Mandatory Type   Description
   ========= ========= ====== =====================
   domains   Yes       array  List of domains.
   links     Yes       Object Domain resource link.
   ========= ========= ====== =====================

-  Example response

   .. code-block::

      {
        "domains": [
          {
            "links": {
              "self": "https://sample.domain.com/v3/domains/e31ac82d778b4d128cb6fed37fd72cdb"
            },
            "description": null,
            "name": "exampledomain",
            "enabled": true,
            "id": "e31ac82d778b4d128cb6fed37fd72cdb"
          }
        ],
        "links": {
          "self": "https://sample.domain.com/v3/OS-FEDERATION/domains",
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
| 405         | The method specified in the request is not allowed for the requested resource. |
+-------------+--------------------------------------------------------------------------------+
| 413         | The request entity is too large.                                               |
+-------------+--------------------------------------------------------------------------------+
| 500         | Internal server error.                                                         |
+-------------+--------------------------------------------------------------------------------+
| 503         | Service unavailable.                                                           |
+-------------+--------------------------------------------------------------------------------+
