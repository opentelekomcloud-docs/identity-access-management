:original_name: en-us_topic_0079467614.html

.. _en-us_topic_0079467614:

Querying an Agency List Based on the Specified Conditions
=========================================================

Function
--------

This API is used to query an agency list based on the specified conditions.

URI
---

-  URI format

   GET /v3.0/OS-AGENCY/agencies{?domain_id,name,trust_domain_id}

-  Query parameters

   =============== ========= ====== ===========================
   Parameter       Mandatory Type   Description
   =============== ========= ====== ===========================
   domain_id       Yes       String ID of the current domain.
   name            No        String Name of an agency.
   trust_domain_id No        String ID of the delegated domain.
   =============== ========= ====== ===========================

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

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X GET https://sample.domain.com/v3.0/OS-AGENCY/agencies?domain_id=0ae9c6993a2e47bb8c4c7a9bb8278d61

Response Parameters
-------------------

-  Parameters in the response body

   ========= ========= ========= =================
   Parameter Mandatory Type      Description
   ========= ========= ========= =================
   agencies  Yes       JSONArray List of agencies.
   ========= ========= ========= =================

-  Description for the agency format

   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                   |
   +===================+===========+========+===============================================================================================================+
   | id                | Yes       | String | ID of an agency.                                                                                              |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | name              | Yes       | String | Name of an agency.                                                                                            |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | domain_id         | Yes       | String | ID of the current domain.                                                                                     |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | trust_domain_id   | Yes       | String | ID of the delegated domain.                                                                                   |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | trust_domain_name | Yes       | String | Name of the delegated domain.                                                                                 |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | description       | Yes       | String | Description of an agency.                                                                                     |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | duration          | Yes       | String | Validity period of an agency. The default value is **null**, indicating that the agency is permanently valid. |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | expire_time       | Yes       | String | Expiration time of an agency.                                                                                 |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | create_time       | Yes       | String | Time when an agency is created.                                                                               |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

-  Example response (request successful)

   .. code-block::

      {
        "agencies": [
          {
            "trust_domain_name": "exampledomain",
            "description": " testsfdas ",
            "trust_domain_id": "b3f266d0c08544a0859740de8b84e850",
            "id": "afca8ddf2e92469a8fd26a635da5206f",
            "duration": null,
            "create_time": "2017-01-04T09:09:15.000000",
            "expire_time": null,
            "domain_id": "0ae9c6993a2e47bb8c4c7a9bb8278d61",
            "name": "exampleagency"
          }
        ]
      }

-  Example response (request failed)

   .. code-block::

      {
        "error": {
          "message": "You are not authorized to perform the requested action: identity:list_agencies",
          "code": 403,
          "title": "Forbidden"
        }
      }

**Status Codes**
----------------

=========== =======================================
Status Code Description
=========== =======================================
200         The request is successful.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =======================================
