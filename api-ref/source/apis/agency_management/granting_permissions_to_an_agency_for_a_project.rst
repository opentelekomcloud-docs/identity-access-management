:original_name: en-us_topic_0079467620.html

.. _en-us_topic_0079467620:

Granting Permissions to an Agency for a Project
===============================================

Function
--------

This API is used to grant permissions to an agency for a project.

URI
---

-  URI format

   PUT /v3.0/OS-AGENCY/projects/{project_id}/agencies/{agency_id}/roles/{role_id}

-  URI parameters

   ========== ========= ====== =========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================================
   project_id Yes       String ID of a project under the current domain.
   agency_id  Yes       String ID of an agency.
   role_id    Yes       String ID of a role.
   ========== ========= ====== =========================================

   .. note::

      The role name corresponding to **role_id** in a request body is controlled by a blacklist. The role name cannot be **secu_admin** or **te_agency**.

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

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X PUT https://sample.domain.com/v3.0/OS-AGENCY/projects/0945241c5ebc4660bac540d48f2a2c14/agencies/37f90258b820472bbc8a0f4f0bfd720d/roles/0f3a2d418ed747fa8be46e92757be9ff

Response Parameters
-------------------

-  No response: indicates that the response is successful.

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
