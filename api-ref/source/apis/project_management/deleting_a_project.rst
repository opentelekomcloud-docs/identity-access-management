:original_name: en-us_topic_0094012960.html

.. _en-us_topic_0094012960:

Deleting a Project
==================

Function
--------

This API is used to delete a project.

URI
---

-  URI format

   DELETE /v3/projects/{project_id}

-  URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

-  Example Request

   .. code-block::

      curl -i -k -H "X-Auth-Token:$token" -H 'Content-Type:application/json;charset=utf8' -X DELETE https://sample.domain.com/v3/projects/3291eab70fd743499ef1a09aa3ae67a7

Response Parameters
-------------------

None

Status Codes
------------

=========== =========================================
Status Code Description
=========== =========================================
204         The request is successful.
400         The server failed to process the request.
401         Authentication failed.
403         Access denied.
404         The requested resource cannot be found.
500         Internal server error.
503         Service unavailable.
=========== =========================================
