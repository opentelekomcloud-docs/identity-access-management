:original_name: en-us_topic_0079467625.html

.. _en-us_topic_0079467625:

Deleting an Agency
==================

Function
--------

This API is used to delete an agency.

.. note::

   After this operation, the delegated party can no longer access the relevant resources. Exercise caution when performing this operation.

URI
---

-  URI format

   DELETE /v3.0/OS-AGENCY/agencies/{agency_id}

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

-  Example request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X DELETE https://sample.domain.com/v3.0/OS-AGENCY/agencies/2809756f748a46e2b92d58d309f67291

Response Parameters
-------------------

-  Example response (request failed)

   .. code-block::

      {
          "error": {
              "message": "Could not find agency: 2809756f748a46e2b92d58d309f67291",
              "code": 404,
              "title": "Not Found"
          }
      }

**Status Codes**
----------------

=========== =======================================
Status Code Description
=========== =======================================
204         The request is successful.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
=========== =======================================
