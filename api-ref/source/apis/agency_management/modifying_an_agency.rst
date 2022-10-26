:original_name: en-us_topic_0079467623.html

.. _en-us_topic_0079467623:

Modifying an Agency
===================

Function
--------

This API is used to modify agency information, including the **trust_domain_id**, **description**, and **trust_domain_name** parameters.

URI
---

-  URI format

   PUT /v3.0/OS-AGENCY/agencies/{agency_id}

-  URI parameters

   ========= ========= ====== ================
   Parameter Mandatory Type   Description
   ========= ========= ====== ================
   agency_id Yes       String ID of an agency.
   ========= ========= ====== ================

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                         |
   +==============+===========+========+=====================================================================+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field.               |
   +--------------+-----------+--------+---------------------------------------------------------------------+
   | X-Auth-Token | Yes       | String | Authenticated token with the **Security Administrator** permission. |
   +--------------+-----------+--------+---------------------------------------------------------------------+

-  Parameters in the request body

   +-------------------+-----------+--------+----------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                    |
   +===================+===========+========+================================================================+
   | trust_domain_id   | No        | String | ID of the delegated domain. The delegated domain must exist.   |
   +-------------------+-----------+--------+----------------------------------------------------------------+
   | trust_domain_name | No        | String | Name of the delegated domain. The delegated domain must exist. |
   +-------------------+-----------+--------+----------------------------------------------------------------+
   | description       | No        | String | Description of an agency.                                      |
   +-------------------+-----------+--------+----------------------------------------------------------------+

   .. note::

      The **trust_domain_id** and **trust_domain_name** parameters in a request body must exist or not exist at the same time. If both of them exist, **trust_domain_name** takes precedence.

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X PUT -d '{"agency" : {"trust_domain_id" : "35d7706cedbc49a18df0783d00269c20","trust_domain_name" : "exampledomain","description" : "111111"}}' https://sample.domain.com/v3.0/OS-AGENCY/agencies/2809756f748a46e2b92d58d309f67291

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= =========== =================
   Parameter Mandatory Type        Description
   ========= ========= =========== =================
   agency    Yes       JSON object Delegated object.
   ========= ========= =========== =================

-  Description for the agency format

   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                   |
   +=================+===========+========+===============================================================================================================+
   | id              | Yes       | String | ID of an agency.                                                                                              |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | name            | Yes       | String | Name of an agency.                                                                                            |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | domain_id       | Yes       | String | ID of the current domain.                                                                                     |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | trust_domain_id | Yes       | String | ID of the delegated domain.                                                                                   |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | description     | Yes       | String | Description of an agency.                                                                                     |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | duration        | Yes       | String | Validity period of an agency. The default value is **null**, indicating that the agency is permanently valid. |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | expire_time     | Yes       | String | Expiration time of an agency.                                                                                 |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | create_time     | Yes       | String | Time when an agency is created.                                                                               |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

-  Example response (request successful)

   .. code-block::

      {
        "agency" : {
           "description" : " testsfdas ",
           "trust_domain_id" : "3ebe1024db46485cb02ef08d3c348477",
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
          "message": "TrustDomainNotFound",
          "code": 404,
          "title": "Not Found"
        }
      }

**Status Codes**
----------------

=========== =========================================
Status Code Description
=========== =========================================
200         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =========================================
