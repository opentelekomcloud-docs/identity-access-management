:original_name: en-us_topic_0066154567.html

.. _en-us_topic_0066154567:

Querying Information About a Specified Project
==============================================

Function
--------

This API is used to query detailed information about a project based on the project ID.

URI
---

-  URI format

   GET /v3/projects/{project_id}

-  URI parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

-  Parameters in the request header

   +--------------+-----------+--------+-------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                           |
   +==============+===========+========+=======================================================+
   | X-Auth-Token | Yes       | String | Authenticated token.                                  |
   +--------------+-----------+--------+-------------------------------------------------------+
   | Content-Type | Yes       | String | Fill **application/json;charset=utf8** in this field. |
   +--------------+-----------+--------+-------------------------------------------------------+

-  Example request

   Obtaining information about the project whose ID is project_id=619d3e78f61b4be68bc5aa0b59edcf7b

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -H "X-Auth-Token:$token" -X GET https://sample.domain.com/v3/projects/619d3e78f61b4be68bc5aa0b59edcf7b

Response Parameters
-------------------

-  Example response

.. code-block::

   {
     "project": {
       "is_domain": false,
       "description": "",
       "links": {
         "self": "https://sample.domain.com/v3/projects/2e93d63d8d2249f5a4ac5e2c78586a6e"
       },
       "enabled": true,
       "id": "2e93d63d8d2249f5a4ac5e2c78586a6e",
       "parent_id": "44c0781c83484eb9a4a5d4d233522cea",
       "domain_id": "44c0781c83484eb9a4a5d4d233522cea",
       "name": "MOS"   //Default project name of OBS
     }
   }

Status Codes
------------

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
