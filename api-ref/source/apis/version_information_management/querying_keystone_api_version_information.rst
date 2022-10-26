:original_name: en-us_topic_0057845569.html

.. _en-us_topic_0057845569:

Querying Keystone API Version Information
=========================================

Function
--------

This API is used to obtain the keystone API version information.

URI
---

GET /

Request Parameters
------------------

Example request

.. code-block::

   curl -i -k -X GET https://sample.domain.com/

Response Parameters
-------------------

-  Response parameter description

   ========= ========= ====== =================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =================================
   versions  Yes       Object Keystone API version information.
   values    Yes       Array  Keystone API version list.
   ========= ========= ====== =================================

-  Description for the values format

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
          "versions": {
              "values": [
                  {
                      "media-types": [
                          {
                              "type": "application/vnd.openstack.identity-v3+json",
                              "base": "application/json"
                          }
                      ],
                      "links": [
                          {
                              "rel": "self",
                              "href": "https://sample.domain.com/v3/"
                          }
                      ],
                      "id": "v3.6",
                      "updated": "2016-04-04T00:00:00Z",
                      "status": "stable"
                  }
              ]
          }
      }

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
300         The request is successful.
400         The server failed to process the request.
404         The requested resource cannot be found.
503         Service unavailable.
=========== =========================================
