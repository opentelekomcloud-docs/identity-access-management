:original_name: en-us_topic_0079467622.html

.. _en-us_topic_0079467622:

Deleting Permissions of an Agency on a Domain
=============================================

Function
--------

This API is used to delete permissions of an agency on a domain.

URI
---

-  URI format

   DELETE /v3.0/OS-AGENCY/domains/{domain_id}/agencies/{agency_id}/roles/{role_id}

-  URI parameters

   ========= ========= ====== =========================
   Parameter Mandatory Type   Description
   ========= ========= ====== =========================
   domain_id Yes       String ID of the current domain.
   agency_id Yes       String ID of an agency.
   role_id   Yes       String ID of a role.
   ========= ========= ====== =========================

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X DELETE https://sample.domain.com/v3.0/OS-AGENCY/domains/b32d99a7778d4fd9aa5bc616c3dc4e5f/agencies/37f90258b820472bbc8a0f4f0bfd720d/roles/0f3a2d418ed747fa8be46e92757be9ff

Response Parameters
-------------------

-  Example response (request failed)

   .. code-block::

      {
         "error" : {
             "message" : "Could not find role: 0f3a2d418ed747fa8be46e92757be9ddff",
             "code" : 404,
             "title" : "Not Found"
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
