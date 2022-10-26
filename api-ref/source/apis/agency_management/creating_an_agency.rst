:original_name: en-us_topic_0079467617.html

.. _en-us_topic_0079467617:

Creating an Agency
==================

Function
--------

This API is used to create an agency.

URI
---

POST /v3.0/OS-AGENCY/agencies

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | application/json;charset=utf8                                       |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Parameters in the request body

   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory    | Type   | Description                                                                                                                                                                                                                                                      |
   +===================+==============+========+==================================================================================================================================================================================================================================================================+
   | name              | Yes          | String | Name of an agency. The length is less than or equal to 64 characters.                                                                                                                                                                                            |
   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id         | Yes          | String | ID of the current domain.                                                                                                                                                                                                                                        |
   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | trust_domain_id   | At least one | String | ID of the delegated domain.                                                                                                                                                                                                                                      |
   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | trust_domain_name |              | String | Name of the delegated domain.                                                                                                                                                                                                                                    |
   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description       | No           | String | Description of an agency. The length is less than or equal to 255 characters.                                                                                                                                                                                    |
   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | duration          | No           | String | Validity period of the agency. The default value is **null**, which means that the agency will never expire. If this parameter is set to **FOREVER**, the validity of the agency is unlimited. If it is set to **ONEDAY**, the agency is valid only for one day. |
   +-------------------+--------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      At least one of **trust_domain_id** and **trust_domain_name** must exist in the request body. If both of them exist, **trust_domain_name** takes precedence.

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X POST -d'{"agency" : {"name" : "exampleagency","domain_id" : "0ae9c6993a2e47bb8c4c7a9bb8278d61","trust_domain_id" : "35d7706cedbc49a18df0783d00269c20","trust_domain_name" : "exampledomain","description" : "testsfdas"}}' https://sample.domain.com/v3.0/OS-AGENCY/agencies

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== =================
   Parameter Mandatory Type        Description
   ========= ========= =========== =================
   agency    Yes       JSON object Delegated object.
   ========= ========= =========== =================

-  Description for the agency format

   =============== ========= ====== ===============================
   Parameter       Mandatory Type   Description
   =============== ========= ====== ===============================
   id              Yes       String ID of an agency.
   name            Yes       String Name of an agency.
   domain_id       Yes       String ID of the current domain.
   trust_domain_id Yes       String ID of the delegated domain.
   description     Yes       String Description of an agency.
   duration        Yes       String Validity period of an agency.
   expire_time     Yes       String Expiration time of an agency.
   create_time     Yes       String Time when an agency is created.
   =============== ========= ====== ===============================

-  Example response (request successful)

   .. code-block::

      {
        "agency" : {
           "description" : "testsfdas",
           "trust_domain_id" : "35d7706cedbc49a18df0783d00269c20",
           "id" : "c1a06ec7387f430c8122d6f336c66dcf",
           "duration" : null,
           "create_time" : "2017-01-06T05:56:09.738212",
           "expire_time" : null,
           "domain_id" : "0ae9c6993a2e47bb8c4c7a9bb8278d61",
           "name" : "exampleagency"
          }
      }

-  Example response (request failed)

   .. code-block::

      {
          "error": {
              "message": "'name' is a required property",
              "code": 400,
              "title": "Bad Request"
          }
      }

**Status Codes**
----------------

=========== =========================================
Status Code Description
=========== =========================================
201         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
409         The agency already exists.
500         Internal server error.
=========== =========================================
