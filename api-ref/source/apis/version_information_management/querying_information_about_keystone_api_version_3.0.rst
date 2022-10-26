:original_name: en-us_topic_0057845613.html

.. _en-us_topic_0057845613:

Querying Information About Keystone API Version 3.0
===================================================

Function
--------

This API is used to obtain the information about the keystone API version 3.0.

URI
---

GET /v3

Request Parameters
------------------

Example request

.. code-block::

   curl -i -k -X GET https://sample.domain.com/v3

Response Parameters
-------------------

-  Response parameter description

   ========= ========= ====== =================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =================================
   version   Yes       Object Keystone API version information.
   ========= ========= ====== =================================

-  Description for the version format

   =========== ========= ====== =================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== =================================
   status      Yes       String Version status.
   updated     Yes       String Last version update time.
   media-types Yes       Array  Version-supported message format.
   id          Yes       String Version, for example, v3.0.
   links       Yes       Array  Version resource link.
   =========== ========= ====== =================================

-  Example response (successful response)

   .. code-block::

      {
          "version": {
              "status": "stable",
              "updated": "2016-04-04T00:00:00Z",
              "media-types": [
                  {
                      "base": "application/json",
                      "type": "application/vnd.openstack.identity-v3+json"
                  }
              ],
              "id": "v3.6",
              "links": [
                  {
                      "href": "https://sample.domain.com/v3/",
                      "rel": "self"
                  }
              ]
          }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
404         The requested resource cannot be found.
503         Service unavailable.
=========== =========================================
