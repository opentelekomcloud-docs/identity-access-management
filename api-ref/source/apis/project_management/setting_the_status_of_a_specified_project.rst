:original_name: en-us_topic_0074171149.html

.. _en-us_topic_0074171149:

Setting the Status of a Specified Project
=========================================

Function
--------

This API is used to set the status of a specified project. The project statuses include **Normal** and **Suspended**.

URI
---

-  URI format

   PUT /v3-ext/projects/{project_id}

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

-  Parameters in the request body

   +-----------+-----------+--------+---------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                   |
   +===========+===========+========+===============================================================+
   | status    | Yes       | String | Project status. The value can be **suspended** or **normal**. |
   +-----------+-----------+--------+---------------------------------------------------------------+

   .. note::

      -  **suspended**: The project is frozen.
      -  **normal**: The project is normal or unfrozen.

-  Example request

   .. code-block::

      curl -i -k -H 'Accept:application/json' -H 'Content-Type:application/json;charset=utf8' -X "X-Auth-Token:$token" -X PUT -d '{"project": {"status":"suspended"}}'https://sample.domain.com/v3-ext/projects/5c9f5525d9d24c5bbf91e74d86772029

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
